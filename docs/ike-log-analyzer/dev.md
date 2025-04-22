# IKE Debugger – Developer Details

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