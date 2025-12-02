# Installation Guide  
_How to install and activate SmartEdge EA in MT4_

This guide explains how to install SmartEdge EA on MetaTrader 4 (MT4), attach it to charts, and activate your license.

---

# 1. Download the EA  
You will receive the EA file:

SmartEdgeEA.ex4


(Or `.mq4` if you requested the source-enabled version.)

Save the file somewhere easy to find.

---

# 2. Open MetaTrader 4  
Launch your MT4 platform provided by your broker.

From the top menu:
File → Open Data Folder

This opens the MT4 directory.

---

# 3. Copy the EA Into the “Experts” Folder  

Navigate to:
MQL4 → Experts

Place the EA file inside this folder.

Example:
MQL4/Experts/SmartEdgeEA.ex4

---

# 4. Restart MT4  
Close MT4 completely and reopen it.

This refreshes the platform and loads the new EA.

---

# 5. Enable Algo Trading  
Before using the EA, make sure MT4 is allowed to run automated systems.

Go to:
Tools → Options → Expert Advisors

Enable the following:

✔ Allow automated trading  
✔ Allow DLL imports  
✔ Allow WebRequests (optional, only if instructed)

Click **OK**.

Then ensure the **AutoTrading** button at the top of MT4 is **green**.

---

# 6. Attach SmartEdge EA to a Chart  
Choose any chart and timeframe (60-minute recommended unless specified).

Then:
Navigator → Expert Advisors → SmartEdgeEA

Drag it onto the chart.

A window opens with settings.

---

# 7. Enter Your License Key  
In the EA settings under **Inputs**, you will find a field:

LicenseKey = YOUR-KEY-HERE

Paste the license key exactly as provided.

Example:
ABCD-1234-EFGH-5678


Click **OK** to activate.

---

# 8. Check the Smile Icon  
After attaching the EA, look at the top-right of the chart:

🙂 **Smiley face = EA running correctly**  
☹️ **Sad face = EA not working**

If you see a sad face:

- AutoTrading may be disabled  
- License key may be incorrect  
- Broker may be blocking algo trading  
- Chart may be paused  
- MT4 needs a restart  

---

# 9. Recommended Setup  
Although SmartEdge EA supports multiple pairs, we recommend:

✔ 1 chart per symbol  
✔ Same timeframe across all charts  
✔ Avoid running other EAs on the same symbols  

Your license allows activating across any supported broker account unless otherwise stated.

---

# 10. Viewing Trades  
The EA will display:

- Active trades  
- Average price  
- Basket status  
- Risk conditions  

You can monitor these in:
Terminal → Trade


---

# 11. Updating the EA  
When a new version is released:

1. Remove the old EA from the chart  
2. Delete the old `.ex4` file from `MQL4/Experts`  
3. Copy the new file  
4. Restart MT4  
5. Attach EA again  

Your license automatically applies to the new version.

---

# 12. Support  
If you need help:

📩 team@smartedgetrading.net  
🌐 https://smartedgetrading.net

---

© SmartEdge Trading — Installation Guide v1.0.0



