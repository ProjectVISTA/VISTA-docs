# 🧭 Integrating ticket ID into existing tools

## Steps to integrate ticket ID into existing tools:
#### The following packages need to be installed and should be added to requirements.txt:
```
flask_sqlalchemy
python-dotenv
psycopg2-binary
```

#### Add a '.env' file to the repo, contents will be:
`DB_URI=postgresql://<dbusername>>:<dbpassword>@localhost:5432/usage_logs`

#### (Optional) Add a '.env.example' file to the repo, contents will be:
`DB_URI=postgresql://<username>:<password>@<host>:<port>/<database>`

#### Create (or append to it if it already exists) '.gitignore' as:
```
.env
__pycache__/
```

#### Create db.py as:
```python
from flask_sqlalchemy import SQLAlchemy

db = SQLAlchemy()
```

#### Create models.py as:
from db import db
```python
class TicketUsage(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    tool_name = db.Column(db.String(100), nullable=False)
    username = db.Column(db.String(100))
    ticket_id = db.Column(db.String(100), nullable=False)
    timestamp = db.Column(db.DateTime, server_default=db.func.now())
```

#### In app.py:
```python
from flask import Flask, request, redirect, url_for, session
from db import db
from datetime import datetime
from flask_sqlalchemy import SQLAlchemy
from dotenv import load_dotenv
import os
from models import TicketUsage


load_dotenv()

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = os.getenv('DB_URI')
app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False

db.init_app(app)

with app.app_context():
    db.create_all()  # Ensure tables are created
```

in the flask routes in app.py:
In index(), make sure to allow POST (already done), and in troubleshoot():
```python
@app.route("/troubleshoot", methods=["GET", "POST"])
def troubleshoot():
    if request.method == "POST":
        ticket_id = request.form.get("ticket_id")
        session["ticket_id"] = ticket_id  # store in session

        # Log in DB
        usage = TicketUsage(
            tool_name="SSL-VPN Troubleshooter",
            username=None,  # add username when auth is ready
            ticket_id=ticket_id
        )
        db.session.add(usage)
        db.session.commit()
```

#### In index.html:
```python
# in index.html:
<form action="{{ url_for('troubleshoot') }}" method="POST">
    <label for="ticket_id">Enter Ticket ID:</label><br>
    <input type="text" name="ticket_id" required style="padding: 6px;"><br><br>
    <button class="btn" type="submit">Start Troubleshooting</button>
</form>
```
## FAQs

#### Why did we go with a sql based approach?
Since our entries are structured (tool name, ticket_id, user, timestamp) and we want Excel exports + user-level stats:
- PostgreSQL (or any SQL DB) is a cleaner, safer, and more future-proof solution.

#### 🔍 Why PostgreSQL 
✅ Relational Structure
- The data (tool name, ticket ID, username, timestamp) is clearly tabular, fixed-structure.
- Relational databases excel at structured, queryable, historical logs like this.
- We might later want to join with other tables (e.g. user info, tool versions).

✅ Analytics & Reporting
- We want to export Excel reports, filter by dates, group by users, count tickets, etc.
- SQL is far better suited for these kinds of queries than MongoDB’s aggregation pipeline.
- Pandas integrates more naturally with relational query results.

✅ Concurrency Support
- PostgreSQL handles high-concurrency scenarios natively and robustly.

✅ Why PostgreSQL is the Best Fit for us:
- Designed for concurrent use by multiple tools/users.
- Built-in time-based filtering, grouping, and advanced reporting queries.
- Has excellent support for exporting data to Pandas → Excel.
- Will scale with us: no need to change DBs late.
- Can be centrally hosted and shared by all our Flask tools.
- Powerful enough to support future features like role-based access, dashboards, etc.

