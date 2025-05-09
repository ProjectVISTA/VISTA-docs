# IKE Debugger – Developer Details

## Setting up your developer environment:

It is highly suggested to use Linux or Windows Subsystem for Linux(WSL) for development on this application, all development to this point has been on WSL/MacOS and development has not been tested with Windows.

Refer here for information on setting up WSL: [https://learn.microsoft.com/en-us/windows/wsl/install](https://learn.microsoft.com/en-us/windows/wsl/install)

Once you've gotten your Linux/WSL/MacOS development environment setup for the application, please follow these steps to begin adding test cases:

### 1. Request access for development repository and fork it.

In order to fork the repository used for developing new test cases before they get pushed to prod, you will need to request access for Lukas's repository at [https://github.com/lvannstruth-ftnt/gui_ike_debugger_reforked](https://github.com/lvannstruth-ftnt/gui_ike_debugger_reforked). You can reach Lukas on Teams or via Email at lstruth@fortinet.com. Once Lukas provides you access, please create a fork of the 'gui_ike_debugger_reforked' repository following these instructions: [https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo)

### 2. Clone your new fork:

Follow these instructions for your newly created fork to download the repository locally: [https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository)

### 3. Setup your Python/Postgres installation(Ubuntu):

The following steps apply both for bare-metal Ubuntu as well as WSL Ubuntu.

You will need to install the following packages for Python development with the following instructions to function:

```bash
sudo apt update
sudo apt upgrade 
sudo apt install python3.10-venv python-is-python3 postgresql
```

This installs the python venv package required for python development, applies the system alias to make the 'python' command run python3, and installs postgresql for the database.

### 4. Setup your Python virtual environment:

Once you have the repository cloned to your machine and the required packages installed, enter the root directory of the repository and run the following commands to setup your virtual environment for development. 

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

These commands setup a virtual environment, activate the virtual environment script and then installs all the required libraries for the project to run.

### 5. Setup PostgresSQL Database:

In order for the flask app to run successfully, PostgreSQL needs to be setup to run locally so the app can successfully record usage/feedback logs. You can refer to the 'instantiate_db_example.bash' command for example commands that Lukas used for his development environment, but generally speaking you need to run the following commands to setup your Linux user as a postgres user(so they can access the database)

```bash 
lukas@lvs-ubuntu-ems$
lukas@lvs-ubuntu-ems$ sudo -i -u postgres
postgres@lvs-ubuntu-ems:~$ createuser --interactive
Enter name of role to add: lukas
Shall the new role be a superuser? (y/n) y
```

When prompted to 'Enter name of role to add:', enter your username. For my Ubuntu VM here, my username is 'lukas'.

After the Postgres user is setup, you need to run the following commands to setup a Postgres user for the application to use:

```bash
psql postgres lukas --command "CREATE USER ike_user WITH PASSWORD 'ike_psk';"
psql postgres lukas --command "CREATE DATABASE usage_logs OWNER ike_user;"
psql postgres lukas --command "GRANT ALL PRIVILEGES ON DATABASE usage_logs TO ike_user;"
```

Replace 'lukas' in these commands with the name of your new Postgres user created in the previous commands.

After the database is created, you need to add a .env file to the root directory of your fork for the database authentication credentials. For the 'ike_user' Postgres user created above, use the following entry in your project's .env file. 

```
DB_URI=postgresql://ike_user:ike_psk@localhost:5432/usage_logs
```

Finally, the postgres server must be started on your machine.

On Ubuntu, use the following command:

```bash
systemctl enable --now postgresql
```

On WSL, use the following command:

```bash
sudo service start postgresql
```

### 6. Running the server and testing:

With your virtual environment setup, you can now run the server from the root directory of the project with the following command. Ensure that you have already run the 'source venv/bin/activate command as specificed in step 4 so that your shell has the correct python libraries imported.

```bash
flask run
```

From here you can add business logic in the `ike_parser` function in `src/app.py` as required for your new test case. Note that a refactor for the parser is in progress by Lukas, he will update this documentation when this is completed.

### 7. Submitting a Pull Request to merge your changes:

After you have finished validating your changes, please submit a pull request for Lukas's `gui_ike_debugger_reforked` repository on github following these instructions: [https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request)

Please ensure to include the following in your pull request:

1. The ticket number or mantis for which you are adding a test case.
2. The log file you have been using to test your changes.
3. A list of the expected analysis output for this new test case.
4. A short summary of the changes made.

Once the PR is opened, one of the core developers will review your request and provide any feedback if necessary or merge your changes if it passes test validation.

Please reach out to Lukas/Jaskirat/Vishal if you run into any issues with setting up your development environment.

## How classes related to results have been defined:
### 💡 What the result class looks like:

```python
class Analysis_Result:
def __init__(self, severity=4, line_num=0, msg="", confidence=5, hyperlink="", 
             verbose_msg="", debug_msg="", fstring="", ai_string="", result_type=0):

    self.sev = Severity(severity)
    self.text_color = self.colors[self.sev.value]
    self.line_number = line_num
    self.msg = msg
    self.confidence = confidence
    self.hyperlink = hyperlink
    self.verbose_msg = verbose_msg
    self.debug_msg = debug_msg
    self.result_type = ResultType(result_type)

    # If fstring is manually set, use that value instead of applying the default formatting.
    if fstring == "":
        self.fstring = self.gen_fstring()
    else: 
        self.fstring = fstring

    # If ai_string is manually set, use that value instead of doing the default action
    if ai_string == "":
        self.ai_string = self.gen_ai_string()
    else: 
        self.ai_string = ai_string
```

### 💡 What the Severity class looks like:
```python
class Severity(Enum):
    """Defines severity levels for analysis messages

    ALERT = 1\n
    ERROR = 2\n
    WARNING = 3\n
    INFO = 4\n
    VALIDATED = 5\n
    """
    ALERT = 1
    ERROR = 2
    WARNING = 3
    INFO = 4
    VALIDATED = 5
```

### 💡 The ResultType class:

```python
class ResultType(Enum):
    """Defines types of result
    ISSUE_NONE = 0
    ISSUE_POTENTIAL = 1
    ISSUE_IDENTIFIED = 2
    
    """
    ISSUE_NONE = 0
    ISSUE_POTENTIAL = 1
    ISSUE_IDENTIFIED = 2
```

### 💡 Color mapping of Severity:
```python
    colors = {
        1: "red",
        2: "orange",
        3: "yellow",
        4: "white",
        5: "green"
    }
```

---

---

## 💡 How to add a new result instance:

```python
if re.search(ike_debug_id_pattern, lineitem).group(1) == ike_debug_instance_id and 'detected retransmit' in lineitem:
    analysis_output.append(Analysis_Result(2, line_num=k+1, msg=f'{lineitem}', ai_string="The FortiGate detected a retransmit of an IKE message from the peer"))
```

This ensures that while we catagorize and print the original line from the debug file in <span style="color:orange;">orange</span>, the strong that will be used for matching with data_model.py for the AI query will be the one as defined with `ai_string`.

---

---

## 💡 Jenkins Access for IKE-DEBUGGER-Tools

### Accessing Jenkins

Jenkins is hosted internally (for access please contact jaskirat/vishal/lukas) and **can only be accessed on the on-prem Vancouver network** at:

👉 [http://10.119.200.83:8080/](http://10.119.200.83:8080/)

---

###  Main Pipeline: `GUI_IKE_FINAL`

This is the primary pipeline used to validate all test cases for `IKE-DEBUGGER-Tools`.

###  What it Does:
1. **Runs verbose `pytest`**  
   - Validates all tests and use-cases.
2. **Runs `pytest` again with coverage**  
   - Generates a code coverage report.
3. **Executes a custom Python script**  
   - Verifies that code coverage is **100%**.

---

###  What Happens on Failures

####  ❌ Test Failures:
- An email is sent to Devs.
- The pipeline stops immediately.

#### ⚠️ Coverage Below 100%:
- The build is marked as **UNSTABLE**.
- An email is sent with the actual coverage percentage.

#### 🛑 Coverage Parsing Failed:
- The pipeline fails with an error.

---

### Pipeline Schedule

- Runs **daily at ~1:00 AM** automatically.
- Runs **Trying to Push to Prod** 
---

### How to Run a Build Manually

1. Log into the Jenkins web UI.
2. Click on the **`GUI_IKE_FINAL`** pipeline on the dashboard.
3. Click **"Build Now"** on the left panel.
4. Monitor progress in **Build History**.
5. Click the build number (e.g., `#23`) → **Console Output** to view logs.
6. Wait for completion:
   - ✅ SUCCESS indicates a successful build.
