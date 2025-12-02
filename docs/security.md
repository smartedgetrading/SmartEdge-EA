# SmartEdge EA – Security & Data Protection

SmartEdge Trading is designed with a **security-first architecture**.  
The Client EA does *not* contain any trading strategy code and does not store any sensitive data locally.  
This document explains how the system protects users, trades, and license information.

---

## 🔐 1. No Strategy Logic Inside the Client EA

The Client EA does **not** include:

- No entry strategy code  
- No indicator logic  
- No grid or risk calculations  
- No trading strategy parameters  

All strategy logic runs securely on the SmartEdge server.  
The Client EA only executes the trades sent by the server.

**This protects the strategy from reverse-engineering and ensures consistent results.**

---

## 🔑 2. License Protection (Email + License Key + MT4 Account)

Each license is securely bound to:

- **User Email**
- **License Key**
- **MT4 Account Number**

The EA validates the license during:

- Installation  
- Every reconnection  
- VPS restart  
- MT4 restart  

If the license or account number does not match, the EA will:

- Stop trading  
- Disable automatic execution  
- Display a clear message inside the HUD  

This prevents:

✔ License sharing  
✔ Unauthorized usage  
✔ Multiple accounts using a single license  

---

## 🔒 3. Encrypted HTTP Communication

All communication between Client EA ↔ Server uses:

- **HTTPS with SSL/TLS encryption**
- **Signed JSON payloads**
- **Randomized timestamps to prevent replay attacks**

SmartEdge EA **never** sends:

✘ Passwords  
✘ Personal data  
✘ MT4 investor/master passwords  
✘ Trading history  

The EA only sends:

- License key  
- Email  
- Logged-in MT4 account  
- Current open positions (during recovery check only)

---

## 🛡 4. Strict Trade Safety Validation

Before placing any trade, the Client EA runs **14+ local safety checks**, including:

- Spread limit  
- Maximum allowed slippage  
- Minimum distance to SL/TP  
- Symbol availability  
- Margin availability  
- Fast market movement checks  
- Broker freeze-level constraints  
- Zero-price protection (no stale quotes)

If any safety rule fails, the EA **blocks the trade** and logs the reason.

This prevents unexpected behavior on bad brokers and protects user funds.

---

## 🔄 5. Fault-Tolerant Connection System

SmartEdge includes an advanced stability system:

### ✔ Automatic retry logic  
### ✔ 5203 error recovery  
### ✔ Dynamic timeout adaptation  
### ✔ DNS refresh  
### ✔ Connection reset mechanism  
### ✔ Re-licensing attempt if VPS disconnects  
### ✔ Signal recovery system if MT4 misses trades  

All of this ensures the EA continues functioning even during:

- Network instability  
- VPS freezing  
- Broker price feed outages  

---

## 📁 6. No User Data Stored on Server

SmartEdge Trading does **not** store:

- MT4 trading history  
- Personal customer data  
- VPS or device information  
- Passwords or credentials  

Stored server-side:

| Data | Purpose |
|------|---------|
| License key | Verify subscription |
| Email | Match license |
| MT4 account | Prevent license sharing |
| Trading signals | Execute the strategy |
| Monthly performance (aggregate) | Display EA performance (no user breakdown) |

No user-identifiable trading history is ever collected.

---

## 🧩 7. Controlled Execution Only (Client Cannot Modify Strategy)

Client EA inputs are intentionally **limited**, so users cannot break the strategy:

Allowed:

- Email  
- License Key  
- Max Lots  
- Magic Number  
- Symbol prefix/suffix  
- HUD visibility  
- Trading/Exit Mode toggle  

Not allowed:

✘ Changing strategy parameters  
✘ Changing risk model  
✘ Adding indicators  
✘ Editing grid or scaling rules  
✘ Modifying SL/TP logic  

This preserves strategy integrity and protects the system from misuse.

---

## 🔥 8. Secure Update & Versioning

The EA includes:

- Remote version check  
- Auto-notification when a new version is available  
- Server-side enforcement of outdated client versions  

If a client EA becomes outdated, it will:

- Display a clear HUD warning  
- Stop taking new trades  
- Instruct the user to update  

This ensures all users are always protected by the latest security improvements.

---

## 🧿 9. What Happens If the VPS Goes Offline?

SmartEdge is designed to protect the user:

### ✔ Trades already open continue normally  
### ✔ No new trades are opened  
### ✔ No reverse trades or errors occur  
### ✔ When MT4 comes back online, EA automatically reconnects  
### ✔ Missed signals are recovered (optional recovery system)  

---

## 🧱 10. Protected Architecture (High-Level Diagram)

+--------------------------+
| SmartEdge Server Engine |
| (Trade Logic & Signals) |
+-----------+--------------+
|
HTTPS (TLS)
|
+-----------v-------------+
| SmartEdge Client EA |
| (License + Execution) |
+-----------+-------------+
|
MT4 Terminal

The client executes trades **only** after receiving secure, validated signals.

---

## ✔ Summary

SmartEdge EA is built with a strong security architecture:

- No strategy logic exposed  
- Secure license binding  
- Encrypted communication  
- Trade safety checks  
- Fault-tolerant engine  
- Zero personal data stored  
- Restricted client inputs  
- Auto-recovery and connection reset  
- Auto-block when license is invalid  

These systems together ensure **reliability**, **protection**, and **consistency** for every SmartEdge user.
