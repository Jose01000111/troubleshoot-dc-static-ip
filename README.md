<p align="center">
<img src="https://i.imgur.com/pqTjnLb.png" alt="osTicket logo"/>
</p>

### Day 2.5 – Fixing a Critical Oversight (Static IP Issue)

While reviewing my setup, I had a gut feeling something was missing. I quickly realized the Domain Controller didn’t have a static IP assigned—putting DNS and authentication at risk with every reboot.

I configured a static private IP in Azure to ensure stability for DNS and domain services. (Consulted ChatGPT to verify the process and prevent future outages.)

### 🧪 Lab Tasks
I log in to the Azure portal at https://portal.azure.com.

<p align="center">
<img src="https://i.imgur.com/qCz50rw.png" alt="osTicket logo"/>
</p>
____________________________________________________________________________________________________________________________________________________________________
Next, I go to Virtual Machines in the Azure portal. I click on the VM running my Domain Controller (DC).
Then, I go to the Network Interface section of the VM.

<p align="center">
<img src="https://i.imgur.com/VAzqb3E.png" alt="osTicket logo"/>
</p>
____________________________________________________________________________________________________________________________________________________________________
In the left pane, I click on Networking. Under the Network Interface section, I select the NIC name (for example, dc-nic).

<p align="center">
<img src="https://i.imgur.com/DT6I835.png" alt="osTicket logo"/>
</p>
____________________________________________________________________________________________________________________________________________________________________
### Set Static Private IP
I click on IP Configurations under Settings, then click the IP configuration (usually labeled ipconfig1). I change the Assignment from Dynamic to Static and use the current IP to avoid any issues. Afterward, I click Save.

<p align="center">
<img src="https://i.imgur.com/hZzRxlo.png" alt="osTicket logo"/>
</p>
____________________________________________________________________________________________________________________________________________________________________
<p align="center">
<img src="https://i.imgur.com/5vQNIvv.png" alt="osTicket logo"/>
</p>
____________________________________________________________________________________________________________________________________________________________________

### Restart the VM
This ensures the network services recognize the change.

### 🚫 What Not To Do
Do not assign a static IP inside Windows!
That can cause Azure’s DHCP to break networking. Always use the Azure Portal for static IP assignments.

### ✅ End Result
Your Domain Controller now has a stable IP, ensuring consistent DNS and domain functionality across your environment.

### 💬 Quick Tip
Think of your DC like a library. If the address keeps changing, nobody knows where to return the books. 📚
