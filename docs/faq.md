# SmartEdge EA – Frequently Asked Questions (FAQ)

This page answers the most common questions from SmartEdge EA users about installation, licensing, VPS requirements, trading behavior, and troubleshooting.

If your question is not listed here, feel free to contact us.

---

## 🔑 1. Licensing & Account Binding

### **Q: Can I use my license on more than one MT4 account?**
No.  
Each license is automatically bound to **one MT4 account number**.

You can change the MT4 account only by contacting support.

---

### **Q: What happens if I change my VPS or reinstall MT4?**
No problem.  
Your license is tied to your **MT4 account number**, not your device.

SmartEdge will continue working normally.

---

### **Q: Why does the EA say “Not Licensed”?**
Possible reasons:

1. Email or license key typed incorrectly  
2. License expired  
3. MT4 account number changed  
4. Internet/VPS connection issue  

Check the details inside the EA HUD.

---

### **Q: Can I switch between Trading Mode and Exit Mode?**
Yes.  
You can toggle it directly inside the EA using the on-chart button:

- **Trading Mode:** EA opens all new trades  
- **Exit Mode:** EA stops new grids but still manages existing ones  

---

## ⚙️ 2. Installation & Setup

### **Q: Do I need the “Master EA”?**
No.  
Clients only install the **SmartEdge Client EA**, which has limited settings and receives signals remotely.

The Master EA runs only on the SmartEdge server.

---

### **Q: How often does the EA communicate with the server?**
Every **5 seconds**.

It uses secure HTTPS communication and reconnects automatically if disconnected.

---

### **Q: What are the minimum client inputs I need to fill?**

Only:

- **Email**  
- **License Key**  
- (Optional) Symbol prefix/suffix (for certain brokers)

All other parameters are locked for safety.

---

## 📈 3. Trading Behavior

### **Q: What symbols does SmartEdge trade?**
SmartEdge automatically trades the symbols configured for your license plan.  
You don’t need to manually add or change anything.

---

### **Q: Why don’t I see trades immediately after installing the EA?**
Possible normal reasons:

- EA is waiting for the next signal  
- Market is closed  
- EA is in **Exit Mode**  
- You changed VPS/timezone and MT4 needs fresh data  
- Broker symbols not mapped (e.g., “EURUSD.” vs “EURUSD”)  

Check the HUD for clues.

---

### **Q: Does SmartEdge ever hide losses or martingale?**
No.

SmartEdge is designed for **controlled risk**, not gambling.  
It does **not** use:

- Hidden martingale  
- Multipliers  
- Unlimited grids  
- Random lot increases  

---

### **Q: Does SmartEdge modify trades after opening?**
Yes, depending on signals:

- It can close individual symbols  
- It can add additional grid trades  
- It can apply TP/SL sent by the server  
- It can sync missed closes using the recovery system  

---

## 🖥️ 4. VPS Requirements

### **Q: Do I really need a VPS?**
Yes — if you want 24/7 uninterrupted trading.

We recommend:

- Windows VPS  
- At least **2 GB RAM**  
- Stable internet  
- Good uptime  

---

### **Q: What happens if my VPS disconnects while trades are open?**
Nothing dangerous.

- Existing trades stay open  
- EA simply stops receiving new signals  
- When VPS reconnects, EA automatically recovers missed signals  

---

## 📡 5. Connectivity & Stability

### **Q: Why do I see “5203 errors”?**
This is a **MetaTrader server timeout**, not a SmartEdge issue.

SmartEdge Client EA includes advanced recovery logic:

- Automatic retry  
- Dynamic timeout adjustment  
- DNS refresh  
- Connection reset  
- License re-validation  

The EA fixes itself automatically.

---

### **Q: Will SmartEdge still work if MT4 freezes?**
Yes.

Once MT4 is restored, the EA:

- Reconnects  
- Validates license  
- Recovers missed signals  
- Returns to normal mode  

---

## 🔧 6. Changing Settings

### **Q: Can I change the MaxLots input?**
Yes, but the EA will still ensure:

- Broker limits  
- Risk restrictions  
- Correct step size  

This prevents accidental misuse.

---

### **Q: Can I change the Magic Number?**
Yes — but only if you know why.

If you use multiple EAs on the same account, they **must have different magic numbers**.

---

### **Q: Can I remove the HUD?**
Yes. Set:InpShowHUD = false;

---


## 🔍 7. Strategy & Performance

### **Q: Is strategy code included inside the Client EA?**
No.

All proprietary strategy logic is safely executed on the SmartEdge server.

Client EA is purely:

- Execution  
- License management  
- Safety checks  
- Signal processing  

---

### **Q: Why does performance vary slightly between users?**
Small differences may occur due to:

- Spread  
- Slippage  
- Account type  
- Execution speed  
- VPS quality  
- GMT offset  

But SmartEdge minimizes variance by using:

- Equity-based scaling  
- Fixed signal execution  
- Broker-agnostic trade mapping  

---

### **Q: Does SmartEdge trade news?**
SmartEdge trades based on strategy signals — not events.

However:

- The system includes safety checks during high volatility  
- No random trades occur  
- No news-based martingale  

---

## 💳 8. Billing & Subscription

### **Q: What happens when my subscription expires?**
The EA will:

- Stop opening new trades  
- Continue managing **existing trades**  
- Show a “License expired” message  

Once renewed, trading resumes automatically.

---

### **Q: Do you offer refunds?**
Refunds follow the policy on the website.  
Contact support with your order number.

---

### **Q: Can I upgrade from Monthly → Quarterly → Yearly?**
Yes, simply purchase the new plan.  
Your license validity will update automatically.

---

## 🛠 9. Support

### **Q: How do I contact support?**

Email: **support@smartedgetrading.net**  
Website: **https://smartedgetrading.net**  

Please include:

- MT4 account number  
- License key  
- Screenshot of the issue  
- VPS/MT4 logs if available  

This helps resolve issues faster.

---

# ✔ Need more help?

If your question isn’t listed, open a ticket or email support.  
We are here to help you trade safely and confidently with SmartEdge EA.



