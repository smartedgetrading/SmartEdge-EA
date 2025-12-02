# SmartEdge Client EA – Settings Guide

This page explains the inputs you will see when you load **SmartEdge Client EA** in MT4.

> 🔐 The Client EA does **not** contain or expose the internal trading strategy.  
> It only receives and executes signals securely from the SmartEdge master server.

---

## 1. Basic Inputs

### `InpEmail`
**Your registration email.**

- Use the **same email** you used when you purchased or requested your license.
- The server uses this to match your MT4 account with your license.

Example:

```text
InpEmail = "your@email.com"
InpLicenseKey
Your unique SmartEdge license key.

This will be sent to you after purchase/activation.

Copy–paste it exactly as it is (including dashes, no extra spaces).

Example:

text
Copy code
InpLicenseKey = "LIC-ABCD1-EFGH2"
If the key is invalid or mistyped, the EA will show a “not licensed” status in the HUD.

2. Risk / Volume Control
InpMaxLots
Safety cap for maximum lot size per trade.

The Client EA automatically scales trades based on your account size vs the master account.
InpMaxLots is a hard ceiling to make sure the EA never uses more than this lot size.

For small accounts (e.g. 1k–5k USD):
→ you can leave this at the default (e.g. 5.0)

For larger accounts:
→ increase only if you understand your risk

Example:

text
Copy code
InpMaxLots = 50.0
✅ This does not force the EA to always use 50 lots — it only ensures it never goes above that value.

InpMagic
Magic number used to tag orders created by SmartEdge Client EA.

Used internally to distinguish SmartEdge trades from other EAs or manual trades.

You normally don’t need to change this.

Only change it if:

You run multiple SmartEdge Client EAs on the same account with different settings.

Or your broker/EAs require a specific magic separation.

Example:

text
Copy code
InpMagic = 66001
3. Display & Chart Settings
InpShowHUD
Shows or hides the on-chart information panel (HUD).

true → Display the SmartEdge panel on the chart

false → Hide the panel (EA still works in the background)

Example:

text
Copy code
InpShowHUD = true
The HUD shows:

License status

Connection status

Monthly % change (relative to when you started the EA)

Trading mode (Trading vs Exit)

Last signal info or last error

4. Broker Symbol Mapping
Some brokers add prefixes or suffixes to symbol names, e.g.:

EURUSD.m

EURUSD.pro

mEURUSD

EURUSD-RAW

To handle that, the Client EA has:

InpSymbolPrefix
Text placed before the symbol.

Example:

If your broker uses mEURUSD
→ set: InpSymbolPrefix = "m"
→ server sends EURUSD, EA trades mEURUSD.

InpSymbolSuffix
Text placed after the symbol.

Example:

If your broker uses EURUSD.m
→ set: InpSymbolSuffix = ".m"
→ server sends EURUSD, EA trades EURUSD.m.

If your broker uses plain symbols like EURUSD, GBPUSD etc, leave both empty:

text
Copy code
InpSymbolPrefix = ""
InpSymbolSuffix = ""
5. Sync & Recovery Options
These are advanced, but still safe to expose to clients.
They control how the Client EA behaves when:

You attach it for the first time

Your terminal disconnects

You restart MT4 or VPS

SYNC_EXISTING
Controls what happens on first connect regarding historical/master signals.

false (recommended for most users)
→ Skip all historical signals and start fresh.
→ The EA will only act on new signals from now on.

true (advanced)
→ EA will try to synchronize with existing open trades from the master.
→ Useful if:

You had the EA disconnected

Or you are attaching it to a live account that should already match the master

Example:

text
Copy code
SYNC_EXISTING = false
If you are unsure, keep it false.

EnableRecovery
Enables the missed-signal recovery system.

true → EA will periodically send a list of open trades to the server and ask:

“Did I miss any CLOSE instructions for these?”

If yes, it will close anything the server flags as “should be closed”.

false → Recovery system is disabled.
The EA will only act on live poll signals.

Recommended: leave this enabled.

text
Copy code
EnableRecovery = true
RecoveryMinutes
How long (in minutes) of no new signals must pass before the EA triggers a recovery check.

Example:

text
Copy code
RecoveryMinutes = 5
Meaning:

If no signals are received for 5+ minutes,

The EA sends your current open positions to the server,

The server responds with “close list” if any trades should already be closed.

You can increase this if your strategy is naturally slower, or reduce it if you want more frequent safety checks.

6. Startup Mode
StartInTradingMode
Controls which mode the EA starts in when you:

Attach it to a chart

Restart MT4

Restart your VPS

Modes:

Trading Mode → EA is fully active

Opens new trades

Adds to grids

Closes trades

Exit Mode → EA does not start new grids

Will still manage / close existing positions as instructed by the server

Good if you want to “wind down” exposure without new entries

Input:

text
Copy code
StartInTradingMode = true
true → Start in full Trading Mode

false → Start in Exit Mode (only manage / close, no new grids)

You can switch between modes anytime via the on-chart button.

7. Typical Recommended Settings
For 99% of users:

text
Copy code
InpEmail          = "your@email.com"
InpLicenseKey     = "your-license-key"
InpMaxLots        = 50.0
InpMagic          = 66001
InpShowHUD        = true
InpSymbolPrefix   = ""
InpSymbolSuffix   = ""
SYNC_EXISTING     = false
EnableRecovery    = true
RecoveryMinutes   = 5
StartInTradingMode = true
Only change:

Prefix/Suffix if your broker symbols are different

InpMaxLots if you really understand your risk

StartInTradingMode if you want the EA to boot into Exit Mode

8. Support
If you are unsure about any setting:

📩 Email: team@smartedgetrading.net
🌐 Website: https://smartedgetrading.net

Please include:

Your MT4 account number

Broker name

Screenshot of inputs window (if possible)

© SmartEdge Trading — SmartEdge Client EA Settings v1.0.0
