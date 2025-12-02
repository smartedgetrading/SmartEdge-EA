# SmartEdge EA – Troubleshooting Guide

If SmartEdge EA isn’t behaving as expected, this guide helps you diagnose and fix common issues quickly.

---

# 🔧 1. EA Shows “Not Licensed” or “License Invalid”

### ✔ Common Causes
- Email mistyped  
- License key mistyped  
- MT4 account number changed  
- License expired  
- VPS/MT4 has no internet  
- Server temporarily unreachable  

### ✔ How to Fix
1. Open the EA settings  
2. Confirm:
   - **InpEmail** is correct  
   - **InpLicenseKey** is correct  
3. Check MT4 → *Help → About* to confirm correct account number  
4. Restart MT4  
5. Restart VPS internet  
6. Check if your license is still active on your SmartEdge dashboard  

### ✔ If still not licensed  
Contact support with:
- Screenshot  
- MT4 account number  
- License key  

---

# 🌐 2. EA Not Opening Trades

### ✔ Possible reasons
- **Exit Mode enabled**  
- Market closed  
- Broker suffix mismatch (EURUSD. / EURUSD-i)  
- No new signals from the server  
- VPS disconnected  
- Symbol not tradable  
- Insufficient margin  
- MaxLots exceeded  

### ✔ Fix Steps
1. Check HUD:
   - Must show **Trading Mode**
2. Make sure market is open  
3. Check *Market Watch* → right-click → “Show All”
4. If broker symbols use suffix/prefix:
   Set:
InpSymbolPrefix = ""
InpSymbolSuffix = "."

5. Verify your VPS clock is correct  
6. Watch MT4 Terminal → Experts for warnings  
7. Ensure InpMaxLots >= 0.01  

---

# ⚠️ 3. EA Not Closing Trades

### ✔ Possible causes
- Recovery system waiting for server confirmation  
- Broker freeze levels preventing close  
- Connection problems  
- EA temporarily blocked by MT4  
- VPS CPU overload  

### ✔ Fix Steps
1. Check HUD "Connection" status  
2. Refresh rates: press **F7**, then OK  
3. Close VPS heavy tasks  
4. Restart MT4  
5. Within 5 minutes, recovery system will sync closes automatically  

If trades still don’t close:
Contact support with the symbol & screenshot.

---

# 🕒 4. EA Stops Receiving Signals (No Updates)

### ✔ Diagnosed by:
HUD shows:
- “Waiting…”
- “Last poll: XX seconds”
- “5203 errors”
- “Connection reset pending”

### ✔ What causes this?
- VPS internet instability  
- Broker spikes freezing MT4  
- MT4 blocked WebRequest  
- Temporary server timeout  

### ✔ Fix
1. Restart MT4  
2. Restart VPS internet  
3. Go to MT4:
- Tools → Options → **WebRequest**
- Make sure this URL is added:
  ```
  https://smartedgetrading.net
  ```
4. Wait 1–2 minutes  
EA auto-recovers by:
- Resetting connection  
- Revalidating license  
- Re-syncing missed signals  

---

# 🔄 5. “5203 WebRequest Timeout”

This is the most common MetaTrader error.  
It is NOT caused by SmartEdge.

### ✔ Cause
MT4 cannot reach the server due to:
- VPS congestion  
- DNS delay  
- Broker lag  
- Weak internet  
- Too many MT4 terminals running  

### ✔ Fix
No action usually required.

SmartEdge Client EA automatically:
- Retries  
- Increases timeout  
- Flushes DNS  
- Resets connection  
- Verifies license  
- Re-syncs signals  

### ✔ If errors are non-stop:
- Restart VPS  
- Close other MT4 terminals  
- Use a better VPS provider  
- Contact support  

---

# 📊 6. Signals Delayed or Out of Sync

### ✔ Causes
- VPS CPU/RAM overload  
- MT4 “Not Responding”  
- Too many charts open  
- Running heavy indicators  

### ✔ Fix
1. Close all charts except **one** with SmartEdge EA  
2. Disable unnecessary indicators  
3. Restart MT4  
4. Ensure VPS has at least:
- 2 GB RAM  
- 1 vCPU minimum  

---

# 💼 7. EA Closes Trades Too Early or Too Late

### ✔ Why this happens
SmartEdge uses:
- Equity-based dynamic scaling  
- Symbol mapping  
- Real-time server signals  

Small differences between brokers may cause:
- 1–2 pip difference in close timing  
- Slight spread differences  
- Execution speed variance  

### ✔ Fix / Recommendation
This is normal and expected.  
Performance will still remain highly aligned with the Master account.

---

# 🧩 8. “Symbol Not Tradable” Message

### ✔ Causes
- Broker uses symbol variations  
- Symbol not enabled in Market Watch  

### ✔ Fix
1. In MT4 → Market Watch → right-click → **Show All**  
2. Check symbol names:
- EURUSD
- EURUSD.
- EURUSD.i  
3. Match these using:
InpSymbolPrefix = ""
InpSymbolSuffix = ".i"


---

# 🧲 9. EA Button Not Working (Trading / Exit Mode)

### ✔ Causes
- Chart locked  
- MT4 objects disabled  
- Chart event issues  

### ✔ Fix
1. Enable chart events:
- Tools → Options → Experts → “Allow DLL” and “Allow Algo Trading”
2. Press F7 → OK  
3. Change timeframe once  
4. Reattach EA  

---

# 💾 10. VPS / MT4 Freezes or Crashes

### ✔ Causes
- Low RAM  
- Too many MT4 terminals  
- Heavy indicators  
- Windows updates  

### ✔ Fix
- Choose a VPS with **2–4 GB RAM**  
- Disable Windows updates  
- Restart VPS weekly  
- Use MT4 portable mode for clean performance  

---

# 📥 11. EA Did Not Recover Missed Signals

Rare but possible.

### ✔ Fix
1. Keep EA running for at least 5 minutes  
2. Recovery system will:
- Fetch missed closes  
- Sync grids  
- Validate open positions  

3. If still stuck → restart MT4  
4. If persist → contact support  

---

# 🧱 12. License Locked After Changing MT4 Account

### ✔ Reason
Licenses bind automatically to the first MT4 account number.

### ✔ Fix
Contact support and request:
- License reset  
- New MT4 number activation  

---

# 📬 13. No Email Received (Order / License / Renewal)

### ✔ Causes
- Gmail spam filter  
- Typo in email during checkout  
- SMTP delays  

### ✔ Fix
Check:
- Spam / promotions folder  
- Your order email accuracy  

Contact support to resend any email.

---

# 🧼 14. Cleanup Steps (If EA Still Misbehaves)

These steps fix **99% of issues**:

1. Restart MT4  
2. Restart VPS  
3. Delete chart → open fresh chart  
4. Reattach the EA  
5. Check internet + WebRequest URL  
6. Confirm license inputs  
7. Let EA run 1–2 minutes  

If still unresolved:
Email support@smartedgetrading.net with a screenshot.

---

# 🤝 Need help?

If none of the above solves your issue, contact support with:

- Screenshot  
- MT4 journal logs  
- Account number  
- License key  
- Broker name  

We respond quickly and help you get back on track.

