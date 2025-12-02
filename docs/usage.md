# SmartEdge Client EA – Usage Guide

This guide explains **how to use the SmartEdge Client EA** on your MT4 account.

> ✅ The Client EA does **not** contain the trading strategy.  
> It securely follows signals from the SmartEdge master server.

---

## 1. Requirements

Before you start, make sure you have:

- A **live or demo MT4 account** with a supported broker
- A valid **SmartEdge license key**
- The **SmartEdge Client EA** file (`SmartEdgeClientEA.ex4`)
- A **stable VPS or PC** that can keep MT4 running

Recommended:

- Ping to broker/server: **< 200 ms**
- Uptime: **24/5** for best results

---

## 2. One-Time MT4 Setup

### 2.1 Enable Algo Trading

In MT4:

1. Go to **Tools → Options → Expert Advisors**
2. Make sure these are checked:
   - ✅ *Allow automated trading*
   - ✅ *Allow WebRequest for listed URL*
3. Click **OK**

---

### 2.2 Allow WebRequest to SmartEdge Server

Still in **Tools → Options → Expert Advisors**:

1. Tick: ✅ *Allow WebRequest for listed URL*  
2. Add this URL to the list:

```text
https://smartedgetrading.net
Click OK

⚠ If this URL is missing, the Client EA cannot talk to the server (no signals, no validation).

3. Attaching the Client EA to a Chart
You only need to attach the Client EA to ONE chart (any symbol, any timeframe).

Suggested:

Symbol: EURUSD

Timeframe: M15 or H1 (doesn't matter for logic – only for visuals)

Steps:

Open MT4

Open a new chart (e.g. EURUSD)

In the Navigator (left panel), find
Expert Advisors → SmartEdge Client EA

Drag & drop it onto the chart

In the inputs tab, fill in:

InpEmail → your registration email

InpLicenseKey → your license key

InpSymbolPrefix / InpSymbolSuffix → if your broker uses custom symbols

Click OK

If everything is correct, you should see:

A small “play” icon (🟢) in the top toolbar

The SmartEdge HUD panel on the chart (if InpShowHUD = true)

4. Understanding the HUD (On-Chart Panel)
When InpShowHUD = true, you will see a panel like:

✅ Status: Licensed OK / Not Licensed

🌐 Connection: Connected / Waiting

💰 Equity & Balance

📈 Monthly Returns (%):

Based on account equity change since the EA started tracking

🧠 EA Mode: TRADING MODE / EXIT MODE

🕒 Last signal / Last error

If something is wrong (license, connection, WebRequest), the panel will show a red or yellow status and print details in the Experts tab.

5. Trading Modes (Very Important)
SmartEdge Client EA has two modes:

5.1 Trading Mode (Normal Mode)
EA opens new trades

EA adds to existing grids

EA closes trades when instructed by the server

This is your standard live mode.

If StartInTradingMode = true, the EA will start in this mode when you attach it or restart MT4.

5.2 Exit Mode (Wind-Down Mode)
EA does NOT start new grids

EA still manages and closes existing positions

Useful if:

You want to reduce risk and let the system “exit gracefully”

You are preparing to withdraw or pause the strategy

You can switch modes at any time using the HUD button:

Button label:

“Switch to Exit Mode” (when currently trading)

“Switch to Trading Mode” (when in exit mode)

🔁 Mode changes are saved, so the EA remembers the last mode across restarts.

6. Broker Symbol Mapping
If your broker uses non-standard symbols, set:

InpSymbolPrefix: text added before symbol

InpSymbolSuffix: text added after symbol

Examples:

Broker Symbol	Prefix	Suffix	Server Symbol
mEURUSD	m	(empty)	EURUSD
EURUSD.m	(empty)	.m	EURUSD
EURUSD-RAW	(empty)	-RAW	EURUSD

If your broker uses normal names like EURUSD, GBPUSD etc, leave both empty:

text
Copy code
InpSymbolPrefix = ""
InpSymbolSuffix = ""
7. Typical Client Setup (Recommended Defaults)
For most users:

text
Copy code
InpEmail           = "your@email.com"
InpLicenseKey      = "your-license-key"
InpMaxLots         = 50.0
InpMagic           = 66001
InpShowHUD         = true
InpSymbolPrefix    = ""
InpSymbolSuffix    = ""
SYNC_EXISTING      = false
EnableRecovery     = true
RecoveryMinutes    = 5
StartInTradingMode = true
8. Common Scenarios
8.1 Moving to a New VPS
Install MT4 on the new VPS

Log in to the same trading account

Copy SmartEdgeClientEA.ex4 into MQL4/Experts

Enable Algo Trading + WebRequest (see section 2)

Attach the EA with the same:

Email

License key

Prefix/suffix (if needed)

If the license is bound to a specific MT4 account number, it will continue working normally.

8.2 You Want to Pause New Trading but Keep Management
Set EA to Exit Mode using the button on the HUD

The EA will:

Close existing positions as signals come

Not start any new grids

This is the safest way to wind down risk without interrupting management.

8.3 You See “Not Licensed” or Connection Errors
Check:

Is WebRequest enabled for:
https://smartedgetrading.net

Is your license key typed correctly (no spaces)?

Is your email matching your registration email?

Is your internet/VPS connection stable?

Try:

Removing the EA

Restarting MT4

Attaching the EA again

If the issue persists, contact support (see below).

9. Logs & Debugging
If something doesn’t look right:

Open the Experts tab (bottom of MT4)

Look for messages starting with SmartEdge

Take a screenshot of:

The chart with HUD

The Experts tab logs

Send them to support so we can see exactly what’s happening.

10. Support
If you need help:

📩 Email: team@smartedgetrading.net
🌐 Website: https://smartedgetrading.net

Please include:

Your MT4 account number

Broker name

Screenshot of:

The inputs window

The SmartEdge panel

Any error messages in Experts tab

© SmartEdge Trading — SmartEdge Client EA Usage v1.0.0
