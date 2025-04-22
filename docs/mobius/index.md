# Mobius Troubleshooting Flows

## 🎥 **Overview Video**
<video controls width="600">
  <source src="/assets/videos/mobius-intro-720p.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

---

## 🛠️ **Mobius Speed Testing Tool**

The **MOBIUS Speed Testing Tool** is designed to guide engineers through speed-related issue investigations across various topologies in a structured and dynamic manner.

### Key Features:

#### 1. **Step-by-Step Guided Troubleshooting:**
The tool dynamically adjusts the next step based on the current output, providing a tailored flow for each scenario.

#### 2. **Information Panel:**
An info section is available at the top right of every step, explaining why the step is necessary and what we aim to achieve.

#### 3. **Automated iPerf Analysis:**
Just provide the iPerf results as requested, and the tool will analyze the data and suggest the most logical next step—removing the guesswork from performance testing.

#### 4. **Report Generation:**
At any stage, you can download a report that summarizes the troubleshooting performed so far—perfect for attaching to support tickets or documentation purposes.

---

### 🌐 **Topologies Supported:**
Currently supports the following four scenarios:

- **SSL VPN (Internet and Internal Data Access)**
- **PC Behind FortiGate (LAN Slowness)**
- **IPsec Site to Site VPN**

> **Dial-up IPsec support** will be added in the coming weeks.


---

### 🔧 **Tool Integrations:**

- **IKE Debugger Tool**: Integrated with the IKE Debugger Tool for deeper insight.
- **NP MOBIUS Tool**: Works seamlessly with the NP MOBIUS Tool for troubleshooting across layers.

---

## **NP Troubleshooting Assistant**

### Overview:
Tailored for **NP (Network Processor) troubleshooting**, the NP Troubleshooting Assistant offers intelligent guidance for identifying and resolving issues related to packet processing.

### Key Highlights:
- **Step-by-step NP troubleshooting guidance**
- Currently supports **NP7 platforms** (Support for other ASIC platforms is in development)
- Integrated with the **IKE Debugger** and **MOBIUS Speed Testing Tool**

---

## 🛠️ Accessing the Tool

* The Mobius tools are currently accessible via VPN to either Ottawa or Vancouver from our <a href="http://10.21.3.250:8863/" target="_blank">homepage</a>.
* Vancouver VPN: `van-vpn1.myfortinet.com:443`
* Ottawa VPN: `ott-vpn2.myfortinet.com:10443`

---

## 🚀 **Launch and Feedback**

The tools are currently in a **pre-global launch phase** and are scheduled to launch officially alongside the **IKE Debugger Tool**.

We encourage all engineers to explore these tools—not only for troubleshooting but also as a learning resource. Your feedback is invaluable for improving the tools.

> **Let us know what works, what doesn't, and how we can make it better!**
