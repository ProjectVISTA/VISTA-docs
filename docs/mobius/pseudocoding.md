# 🧭 Guide to Writing Pseudocode for Troubleshooting Workflows

---

## 📘 Introduction

This guide provides a structured approach to writing pseudocode for troubleshooting workflows.  
The pseudocode acts as a **blueprint** for engineers to design interactive troubleshooting steps that systematically guide users through problem resolution.

---

## 🧱 1. Structure of Pseudocode

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

## 2. ☑️  Using Checkboxes in Questions 
To include checkboxes for user verification, insert {checkbox_html} in the question field. Example: 
```python
"question": f''' 
{checkbox_html} Confirm the firewall policy settings. 
{checkbox_html} Verify the routing table. 
''' 
```
## 3. 🧮 Implementing Input Fields 
For cases requiring user input (e.g., speed test results), define input_fields using predefined labels: 
<br>`"input_fields": ["PC Download Speed (Mbps)", "PC Upload Speed (Mbps)"]`
### Predefined fields: 
* Speed_test_1_download_name = 'PC Download Speed (Mbps)' 
- Speed_test_1_upload_name = 'PC Upload Speed (Mbps)' 
- Speed_test_2_download_name = 'FortiGate Download Speed (Mbps)' 
- Speed_test_2_upload_name = 'FortiGate Upload Speed (Mbps)' 
- Speed_test_3_download_name = 'SSL-VPN Download Speed (Mbps)' 
- Speed_test_3_upload_name = 'SSL-VPN Upload Speed (Mbps)' 

## 4. 🔁  Defining the Next Step Logic 
The next field maps user selections to the corresponding next step. Example: 
"next": {"Yes": "Investigate ISP", "No": "Check CPU/Memory"} 
For dynamically determined steps, leave next empty and handle logic separately. 
## 5. 🤖 Special Cases: Auto-Generated Steps 
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

## ✅ Conclusion 
By following this guide, engineers can create structured, interactive troubleshooting workflows for various use cases. The modular design allows easy customization and extension for different scenarios.

