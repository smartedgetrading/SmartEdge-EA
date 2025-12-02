# SmartEdge Client EA — Update Guide
This guide explains how clients can safely update their SmartEdge Client EA to the latest version without losing license activation or open trades.

SmartEdge Client EA updates are simple and fully backward-compatible.

---

## 🏁 Before You Start
You only need:
- Your license key  
- Your login email  
- The new `.ex4` file provided by SmartEdge

**No settings will be lost**, because the EA automatically restores:
- Last processed signal ID  
- Trading mode (Trading vs Exit mode)  
- Sync state  
- Global variables for monthly returns  

---

## 🔄 Update Steps (Safe & Recommended)

### **1️⃣ Remove the old EA from the chart**
Right-click the chart → *Expert List* → Select “SmartEdge Client EA” → *Remove*  
(or simply close the chart).

This step ensures MT4 unloads the old file from memory.

---

### **2️⃣ Delete or replace the old EA file**
Go to:
MT4 → File → Open Data Folder → MQL4 → Experts

Delete:
SmartEdge ClientEA.ex4


Copy/paste the new version into the same folder.

---

### **3️⃣ Restart MT4**
Close MT4 completely and reopen it.
This ensures MT4 loads the new file into memory.

---

### **4️⃣ Attach the EA to your chart**
Open any chart (recommended: EURUSD M1 or M5), then:
Navigator → Experts → SmartEdge Client EA → Attach to chart

Input your settings:
- Email  
- License key  
- Max lots  
- Symbol mapping  
- HUD visibility  

Click **OK**.

---

### **5️⃣ Confirm successful update**
In the Terminal → *Experts* tab you should see:
SmartEdge Client EA vX.XX Initializing...
License validation successful
Polling server every 5 seconds...


This confirms the EA is connected and updated.

---

## 🛡 What You Will NOT Lose
Updates **never** change:
- Your account license  
- Activation status  
- Your open trades  
- EA’s internal state  

The server always knows your last signal ID, so the EA continues normally.

---

## ❗ Important Notes
### Recovery Mode & Exit Mode  
If you were in:
- **Exit Mode** → EA continues in Exit Mode  
- **Trading Mode** → EA continues Trading  

### No need to revalidate manually  
The EA automatically revalidates the license after each update.

---

## 🆘 Support  
If you face any issue during update:
- Email: **team@smartedgetrading.net**
- Telegram: *https://t.me/smartedgetrading*

Include your:
- MT4 account number  
- License key  
- Screenshot of any errors  

We respond in under **12–24 hours**.

---

*SmartEdge Trading — Built for long-term, stable algorithmic trading.*

