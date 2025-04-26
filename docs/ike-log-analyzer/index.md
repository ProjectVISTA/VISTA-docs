# IKE Debugger – Intro to the Tool

## 🎥 How to Use the Tool

<video controls width="600" preload="metadata">
  <source src="../assets/videos/ike-demo.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

## 📘 Overview

We're excited to introduce **IKE Log Analyzer**—a new automation tool designed to simplify IKE debug log analysis.

This tool processes an IKE debug log file and **automatically highlights potential issues**, saving you both time and effort.

---

## 🛠️ Accessing the Tool

* The IKE Log Analyzer is currently accessible via VPN to either Ottawa or Vancouver at the IP address <a href="http://10.21.3.250:8888" target="_blank">`10.21.3.250:8863`</a> or from our <a href="http://10.21.3.250:8863/" target="_blank">homepage</a>.
* Vancouver VPN: `van-vpn1.myfortinet.com:443 `
* Ottawa VPN: `ott-vpn2.myfortinet.com:10443`

Once you're connected, follow these steps:

1. **Upload** your debug log file.
2. Click **Analyze** to start the analysis process.

---

## 🔍 Analysis Page Overview

The analysis page is divided into four main sections:

### 1️⃣ Connection Summary

The **Connection Summary** is a **collapsible** section that provides a quick overview of the number of connections detected and their associated details. It offers insights into the initial connection states, making it easier to spot issues quickly.

### 2️⃣ Enriched Log File

- This section is where the **magic happens**. Key issues and milestones, such as "Phase 1 Up," are clearly highlighted, helping you interpret the log flow more efficiently.

- Each key event or milestone is visually **marked** for easy reference.

### 3️⃣ AI-Powered Insights

- The **AI Analysis** section uses your local LLM to provide **intelligent insights** and summaries based on the log content.

- It helps with understanding why certain failure logs could be showing up, along with suggested next steps.

### 4️⃣ Raw Log File

- The **Raw Log File view** allows you to access the full raw data. Each line in the enriched log is **clickable**, taking you directly to the corresponding line in the raw log file.


---

## 🗣️ Share Your Insights

As you explore the tool, you may discover new patterns, issues, or use cases we haven’t yet covered. We’d love to hear from you!

- Click the <a href="https://forms.office.com/pages/responsepage.aspx?id=eMQ2LAA9L0WFNUg5b18B8BdRR8fI0dRMpEqJ2cz_JtJUNE4wOVhCVVc5TzlZWk9JSTVRMUo0RUhEVi4u" target="_blank"> Report new use-cases </a> link to share your insights and suggestions.

---
