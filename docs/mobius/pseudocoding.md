# 🧭 Guide to Writing Pseudocode for Troubleshooting Workflows

---

## 📘 Introduction

This guide provides a structured approach to writing pseudocode for troubleshooting workflows.  
The pseudocode acts as a **blueprint** for engineers to design interactive troubleshooting steps that systematically guide users through problem resolution.

---

## 🧱 Structure of Pseudocode

Each troubleshooting workflow is represented as a **list of dictionaries**, where each dictionary defines one step. Each step includes the following keys:

- **`step`**: A unique identifier for the troubleshooting step.  
- **`question`**: The prompt or instruction displayed to the user.  
- **`options`**: The available choices or actions the user can take.  
- **`input_fields`** *(optional)*: Fields where users can enter relevant data.  
- **`next`**: A mapping that defines the next step based on the user's selection.

### Example


```python
troubleshooting_steps = [
    {
        "step": "Step Name",
        "question": "Describe the action the user should take.",
        "options": ["Option1", "Option2"],
        "next": {
            "Option1": "Next Step 1",
            "Option2": "Next Step 2"
        }
    }
]
```

## ☑️  Using Checkboxes in Questions 
To include checkboxes for user verification, insert {checkbox_html} in the question field. Example: 
```python
"question": f''' 
{checkbox_html} Confirm the firewall policy settings. 
{checkbox_html} Verify the routing table. 
''' 
```

## Using text input:
```python
{input_field('Single users affected or multiple?')}
```

Corresponding helper function:
```python
def input_field(name, value=""):
    return f'<input type="text" step="0.01" name="{name}" value="{value}" style="width: 100px; padding: 5px; margin: 5px;">'
```

## Using dropdowns:
```python
{dropdown("hardware platform", "Select the hardware model: ", ['Option1','Option2','Option3'])}
```
Corresponding helper fuction:
```python
def dropdown(name, text, options):
    html_code = f'<label for="{name}">{text}</label>'
    html_code += f'<select name="{name}" id="{name}">'
    html_code += '<option value="">--Please choose an option--</option>'
    for entry in options:
        html_code += f'<option value="{entry}">{entry}</option>'
    html_code += '</select>'
    return html_code
```
## 🧮 Implementing Input Fields 
For cases requiring user input (e.g., speed test results), define input_fields using predefined labels: 
<br>`"input_fields": ["PC Download Speed (Mbps)", "PC Upload Speed (Mbps)"]`
### Predefined fields: 
* Speed_test_1_download_name = 'PC Download Speed (Mbps)' 
- Speed_test_1_upload_name = 'PC Upload Speed (Mbps)' 
- Speed_test_2_download_name = 'FortiGate Download Speed (Mbps)' 
- Speed_test_2_upload_name = 'FortiGate Upload Speed (Mbps)' 
- Speed_test_3_download_name = 'SSL-VPN Download Speed (Mbps)' 
- Speed_test_3_upload_name = 'SSL-VPN Upload Speed (Mbps)' 

## 🔁  Defining the Next Step Logic 
The next field maps user selections to the corresponding next step. Example: 
"next": {"Yes": "Investigate ISP", "No": "Check CPU/Memory"} 
For dynamically determined steps, leave next empty and handle logic separately. 

## 🤖 Special Cases: Auto-Generated Steps 
Some steps require dynamic decision-making, such as analyzing speed test results. In such cases, set next to an empty dictionary: 
```python
{ 
"step": "Comparison of speed tests", 
"question": "Click Proceed and the system will analyze the results.", 
"options": ["Proceed"], 
"next": {} 
}
```
The logic engine will determine the next step based on inputs. 

## 💡 Collapsible Info Section
Use the "info" key to include optional context/information shown in a collapsible format at the top-right of the page.

```python
"info": "Use this step to understand if there's an upstream routing issue."
```

## 🛠️ Highlighted Debug Commands
Wrap CLI debug commands with {debug_start} and {debug_end} for highlighted, copy-enabled display.

```python
{debug_start}
ping PC2 –n 30 –l 1472
{debug_end}
```
## 📝 Debug Text Area (Paste or Upload Logs)
To allow pasting/uploading of debug logs (which will be saved in the report), include      {text_area_html} in questions field infomration.

## ✅ Conclusion 
By following this guide, engineers can create structured, interactive troubleshooting workflows for various use cases. The modular design allows easy customization and extension for different scenarios.

