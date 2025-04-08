<p align="center">
<img src="https://i.imgur.com/pqTjnLb.png" alt="osTicket logo"/>
</p>

### 🛠️ Troubleshooting: Forgot to Assign a Static IP to My DC

### 🧩 Overview
In this quick lab, we fix a common mistake: forgetting to assign a static IP to the Domain Controller (DC) in Azure. Without a static IP, services like DNS and Active Directory can become unreliable.

### ❓ Why It Matters
A Domain Controller must have a static private IP address so clients and services always know where to find it. If Azure randomly changes your DC’s IP on reboot, domain authentication and DNS resolution can break.

### 🛠️ Steps to Fix in Azure
- Login to the Azure Portal

- Go to https://portal.azure.com

<p align="center">
<img src="https://i.imgur.com/qCz50rw.png" alt="osTicket logo"/>
</p>

- Navigate to Your VM (Domain Controller)

- Go to Virtual Machines

- Click on the VM running your DC

- Go to the Network Interface

<p align="center">
<img src="https://i.imgur.com/VAzqb3E.png" alt="osTicket logo"/>
</p>

- In the left pane, click Networking

- Under Network Interface, click the NIC name (example: dc-nic)

<p align="center">
<img src="https://i.imgur.com/DT6I835.png" alt="osTicket logo"/>
</p>

### Set Static Private IP

- Click IP Configurations under Settings

<p align="center">
<img src="https://i.imgur.com/hZzRxlo.png" alt="osTicket logo"/>
</p>

- Click the IP configuration (usually ipconfig1)

- Change Assignment from Dynamic ➡️ Static

<p align="center">
<img src="https://i.imgur.com/5vQNIvv.png" alt="osTicket logo"/>
</p>

- Use the current IP to avoid issues

- Click Save

### (Optional) Restart the VM
This ensures the network services recognize the change.

### 🚫 What Not To Do
Do not assign a static IP inside Windows!
That can cause Azure’s DHCP to break networking. Always use the Azure Portal for static IP assignments.

### ✅ End Result
Your Domain Controller now has a stable IP, ensuring consistent DNS and domain functionality across your environment.

### 💬 Quick Tip
Think of your DC like a library. If the address keeps changing, nobody knows where to return the books. 📚

