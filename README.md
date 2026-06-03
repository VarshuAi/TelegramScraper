<!-- ========================================================================= -->
<!--                        TELEGRAMSCRAPER — README                            -->
<!--       Cyberpunk Premium Theme  |  Animated SVGs  |  Live Badges          -->
<!-- ========================================================================= -->

<div align="center">

<!-- ============================== BANNER ============================== -->

<img src="https://capsule-render.vercel.app/api?type=rounded&color=0:000000,50:001F0D,100:000000&height=180&section=header&text=TelegramScraper&fontSize=48&fontColor=00FF88&fontAlignY=38&animation=fadeIn" width="100%"/>

<!-- ============================== TYPING SVG ============================== -->

<br/>

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Source%20Code%20Pro&weight=500&size=22&duration=3500&pause=800&color=00FF88&center=true&vCenter=true&multiline=true&repeat=true&random=false&width=700&height=80&lines=%3E%20Welcome%20to%20TelegramScraper%20%F0%9F%9A%80;%3E%20Built%20using%20Code%20%7C%20Optimized%20%26%20Secure;%3E%20Scrape%20Telegram%20group%20members%20%28hidden%20me...)](https://github.com/VarshuAi/TelegramScraper)

<br/>

![Version](https://img.shields.io/badge/Version-1.0-00FF88?style=for-the-badge&logo=github&logoColor=black)
![Language](https://img.shields.io/badge/Code-Tech-00CC66?style=for-the-badge&logo=code&logoColor=black)
![Status](https://img.shields.io/badge/Status-Active-14354C?style=for-the-badge&logo=git&logoColor=white)

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:000000,50:001F0D,100:000000&height=60&section=header&text=&fontSize=0" width="100%"/>

</div>

<!-- ============================== ABOUT ============================== -->

<h2>
<img src="https://media.giphy.com/media/WUlplcMpOCEmTGBtBW/giphy.gif" width="30">
<samp>&nbsp;ABOUT</samp>
</h2>

```yaml
name: TelegramScraper
version: 1.0
type: Repository
author: VarshuAi
description: >
  Scrape Telegram group members (hidden members also) and add them to yours.
primary_tech: Code
```

<!-- ============================== CENTRAL GRAPHIC ============================== -->

<div align="center">
<br>
[![Activity Graph](https://github-readme-activity-graph.vercel.app/graph?username=VarshuAi&repo=TelegramScraper&theme=react-dark&bg_color=000000&color=00FF88&line=00FF88&point=00CC66)](https://github.com/VarshuAi/TelegramScraper)
<br>
</div>

<!-- ============================== FEATURES ============================== -->

<h2>
<img src="https://media2.giphy.com/media/QssGEmpkyEOhBCb7e1/giphy.gif?cid=ecf05e47a0n3gi1bfqntqmob8g9aid1oyj2wr3ds3mg700bl&rid=giphy.gif" width="28">
<samp>&nbsp;FEATURES</samp>
</h2>

- **Multi-Account Support** — Log in multiple Telegram accounts and rotate between them automatically
- **3 Login Methods** — Phone number (OTP + 2FA), QR code scan, or Telegram Desktop TData import
- **2 Scraping Modes** — Scrape from the visible members list, or extract hidden members from message history
- **2 Adding Modes** — Rush Adder (tracks progress by removing added members from CSV) or Calm Adder (keeps CSV intact)
- **Message Broadcast** — Send a formatted DM to all scraped members from a Markdown file, with 30–60s delays and account rotation
- **Session Encryption** — All session strings encrypted with Fernet (AES-128) using PBKDF2 key derivation
- **FloodWait Handling** — Automatic wait with jitter for small delays; switches account on large delays (1hr+)
- **Checkpoint Resume** — Interrupted hidden-member scrapes can be resumed from where they left off
- **Account Cooldown Tracking** — Persistent cooldown tracking across sessions with automatic expiry
- **Rich Terminal UI** — Progress bars, spinners, styled tables, and color-coded output
- **Session Management** — List all sessions, test connectivity, and clean up inactive accounts
- **Structured Logging** — Rotating file logs (never logs sensitive data like session strings)
- **Atomic CSV Writes** — Data written to temp file first, then replaced — no corruption on crash

[Get Access to ALL FILES](https://github.com/AbirHasan2005/TelegramScraper?tab=readme-ov-file#support--pricing)
---

<!-- ============================== COMMANDS ============================== -->

<h2>
<img src="https://media.giphy.com/media/iY8CRBdQXODJSCERIr/giphy.gif" width="28">
<samp>&nbsp;COMMANDS & USAGE</samp>
</h2>

### Option 01 — Login Telegram Account

This option lets you authenticate Telegram accounts. Sessions are encrypted and stored locally in the `sessions/` directory.

#### First-Time Encryption Setup

On your first login, you'll be asked to create an encryption password (minimum 4 characters). This password protects all your stored session strings using Fernet encryption with PBKDF2 key derivation (480,000 iterations). On subsequent logins, you'll enter this same password to decrypt existing sessions and encrypt new ones.

> **Important:** If you forget your encryption password, stored sessions cannot be recovered. You'll need to log in again.

#### Sub-Menu

```
01 - Login with Phone Number
02 - Login from TData
03 - Login with QR Code
00 - Go Back
```

#### Login with Phone Number

1. Enter your phone number in international format (e.g., `+1234567890`)
2. Telegram sends an OTP code to your phone/app
3. Enter the OTP code (spaces are automatically stripped)
4. If your account has 2FA enabled, enter your 2FA password (input is masked)
5. Session is encrypted and saved

#### Login with QR Code

1. A QR code is displayed in your terminal
2. Open Telegram on your phone → Settings → Devices → Scan QR Code
3. The tool automatically detects the scan (polls every 5 seconds)
4. If 2FA is enabled, enter your password
5. Session is encrypted and saved

#### Login from TData

1. Provide the path to your Telegram Desktop `tdata` folder
   - **Windows:** `%APPDATA%\Telegram Desktop\tdata`
   - **Linux:** `~/.local/share/TelegramDesktop/tdata`
   - **macOS:** `~/Library/Application Support/Telegram Desktop/tdata`
2. The tool extracts the auth key and converts it to a Pyrogram session
3. Connectivity is verified by calling `get_me()`
4. Session is encrypted and saved

---

### Option 02 — Members Scraper

Scrape members from a Telegram group and save them to `members.csv`.

#### Sub-Menu

```
01 - Scrape Non-Hidden Members (from Group's Members List)
02 - Scrape Hidden Members (from Group's Messages/Mentions)
00 - Go Back
```

#### Scrape Hidden Members

Scrapes members from **message history and mentions** — useful when the members list is restricted.

1. Enter the group link or username
2. The tool iterates through all messages in the group, extracting users from:
   - Message authors
   - `@username` mentions
   - Text mentions (clickable names that link to profiles)
3. A checkpoint is saved every 50 unique members to `scrape_checkpoint.json`
4. If interrupted (Ctrl+C), progress is saved — next time you scrape the same group, you'll be asked to **resume from the checkpoint**
5. Results saved to `members.csv`

**Best for:** Private groups with hidden member lists, or when you want to capture active participants.

[Get Access to ALL FILES](https://github.com/AbirHasan2005/TelegramScraper?tab=readme-ov-file#support--pricing)

#### Scrape Non-Hidden Members

Scrapes from the group's **official members list** (visible when you tap "Members" in group info).

1. Enter the group link or username (e.g., `https://t.me/mygroup`, `@mygroup`, or `mygroup`)
2. The tool selects an available account (skips accounts on cooldown)
3. Iterates through the members list, filtering out bots and deduplicating by user ID
4. A spinner shows real-time progress: member count, group name, and which account is being used
5. Results saved to `members.csv`

**Best for:** Public groups or groups where the members list is visible.

#### Output Format (`members.csv`)

```csv
Name,ID,Username,Access Hash,Group Name,Group ID
John Doe,123456789,johndoe,1234567890123456,MyGroup,-100987654321
Jane,987654321,,9876543210987654,MyGroup,-100987654321
```

---

### Option 03 — Members Adder

Add scraped members from `members.csv` to a target group.

#### Sub-Menu

```
01 - Rush Adder (Remove user from 'members.csv' after adding)
02 - Calm Adder (Keep user in 'members.csv' after adding)
00 - Go Back
```

#### Rush Adder vs Calm Adder

| | Rush Adder | Calm Adder |
|---|---|---|
| **After adding a member** | Removes them from `members.csv` | Keeps `members.csv` unchanged |
| **Best for** | Production runs — tracks progress, no duplicate adds on restart | Testing or intentional re-adds |

#### How Adding Works

1. Enter the target group link or username
2. A progress bar appears showing: percentage, added count, skipped count, elapsed time, and ETA
3. For each member in `members.csv`:
   - Attempts to add them to the group
   - On success: waits a **random 3–8 seconds** before the next add (jitter to avoid detection)
   - If already a member: skips (no delay)
   - If privacy-restricted, kicked, or invalid: skips with reason logged
4. Completion summary shows total processed, added, skipped, and remaining

#### FloodWait Handling

- **Small FloodWait (< 1 hour):** Waits in place with added jitter, then retries with the same account
- **Large FloodWait (>= 1 hour):** Puts the account on cooldown and **switches to the next available account**
- **PeerFlood (spam flag):** Automatically tries a workaround (add as contact → add to group → remove contact)

#### Account Rotation

If you have multiple accounts logged in, the adder cycles through them automatically. When one account hits a large FloodWait, it moves to the next. Cooldown times are persisted in `account_cooldowns.json` so they survive restarts.

---

### Option 04 — Message Broadcast

Send a formatted direct message to all scraped members in `members.csv`.

#### How It Works

1. On first use, a sample template file (`message_template.md`) is created in the project root — you can edit it or use your own `.md` file
2. A **syntax guide** is displayed showing supported Markdown formatting and how it renders on Telegram
3. Enter the path to your `.md` message file
4. The message is converted to Telegram-compatible HTML and a **preview** is shown for confirmation
5. After confirming, messages are sent one-by-one to each user in `members.csv`
6. Each successfully messaged user is **removed from `members.csv`** (allows resuming on restart)

#### Supported Markdown Syntax

| Markdown | Telegram Result |
|---|---|
| `**bold**` | **bold** |
| `*italic*` | *italic* |
| `~~strikethrough~~` | ~~strikethrough~~ |
| `[link text](url)` | Clickable link |
| `` `inline code` `` | `monospace` |
| ```` ```code block``` ```` | Code block |
| `# Header` | **Bold header line** |
| `- list item` | Bullet point |

> **Note:** The maximum message length is 4096 characters (after HTML conversion). Messages exceeding this limit will be rejected before sending.

#### Delay & Rate Limiting

- **30–60 seconds** random delay between each message (mimics human behavior)
- **Small FloodWait (< 1 hour):** Waits with jitter, then retries
- **Large FloodWait (>= 1 hour):** Switches to the next available account
- Account cooldowns are persisted in `account_cooldowns.json`

#### Error Handling

| Scenario | Action |
|---|---|
| User blocked the account | Skipped, removed from CSV |
| User account deactivated | Skipped, removed from CSV |
| User not found (invalid ID/username) | Skipped, removed from CSV |
| User has privacy restrictions | Skipped, **kept in CSV** (may change later) |
| Sending account deactivated/banned | Marked inactive, switches to next account |
| Ctrl+C interrupted | Stops gracefully, CSV reflects partial progress |

---

### Option 05 — Manage Sessions

View, test, and clean up your stored Telegram sessions.

#### Sub-Menu

```
01 - List All Sessions
02 - Test All Sessions
03 - Remove Inactive Sessions
00 - Go Back
```

#### List All Sessions

Displays a table of all stored sessions:

```
┌───┬─────────────────┬──────────┬───────────┐
│ # │ Phone           │ Status   │ Encrypted │
├───┼─────────────────┼──────────┼───────────┤
│ 1 │ +1234***890     │ Active   │ Yes       │
│ 2 │ +9876***321     │ Cooldown │ Yes       │
└───┴─────────────────┴──────────┴───────────┘
```

- Phone numbers are masked for security
- Status shows Active, Cooldown (with remaining time), or error reason
- Encrypted column shows whether the session string is Fernet-encrypted

#### Test All Sessions

Connects each session to Telegram and verifies it's still valid:

1. Enter your encryption password (to decrypt sessions)
2. Each session is tested by calling `get_me()`
3. Results shown in a table: OK (with user ID) or FAILED (with error reason)

#### Remove Inactive Sessions

Finds sessions with a non-Active status (banned, deactivated, auth key invalid, etc.) and offers to delete them:

1. Shows a table of inactive sessions with their status
2. Asks for confirmation: `Remove all inactive sessions? (y/n)`
3. On confirm: deletes the session CSV files from disk

---

### Option 99 — About

Displays tool information: name, version, developer, and contact details.

---

<!-- ============================== TECH STACK ============================== -->

<h2>
<img src="https://media2.giphy.com/media/QssGEmpkyEOhBCb7e1/giphy.gif?cid=ecf05e47a0n3gi1bfqntqmob8g9aid1oyj2wr3ds3mg700bl&rid=giphy.gif" width="28">
<samp>&nbsp;TECH STACK</samp>
</h2>

<div align="center">

#### `>> SYSTEM INVENTORY`
![Code](https://img.shields.io/badge/Code-Primary_Language-00FF88?style=for-the-badge&logoColor=black)
![Git](https://img.shields.io/badge/Git-VCS-00CC66?style=for-the-badge&logo=git&logoColor=white)

</div>

<!-- ============================== SETUP ============================== -->

<h2>
<img src="https://media.giphy.com/media/LnQjpWaON8nhr21vNW/giphy.gif" width="28">
<samp>&nbsp;SETUP</samp>
</h2>

When you launch the tool, you'll see the main menu:

```
TelegramScraper v1.6
ℹ 0 sessions loaded (check Manage Sessions for status)

┌─────────────────────┐
│      Main Menu      │
├─────────────────────┤
│  01  Login Telegram Account
│  02  Members Scraper
│  03  Members Adder
│  04  Message Broadcast
│  05  Manage Sessions
│
│  99  About
│  00  Exit
└─────────────────────┘
› Choose an option:
```

**Typical workflow:**
1. **Login** one or more Telegram accounts (Option 01)
2. **Scrape** members from a source group (Option 02)
3. **Add** scraped members to a target group (Option 03)
4. **Broadcast** a message to all scraped members (Option 04)

---

<!-- ============================== STRUCTURE ============================== -->

<h2>
<samp>&nbsp;📁 STRUCTURE</samp>
</h2>

```
TelegramScraper/
├── main.py                  # Entry point, main menu loop
├── configs.py               # Config class, loads .env variables
├── crypto.py                # Fernet encryption/decryption for sessions
├── account_manager.py       # Multi-account rotation & cooldown tracking
├── retry.py                 # @async_retry decorator with exponential backoff
├── logger.py                # Rotating file logger setup
├── utils.py                 # CSV I/O, input helpers, phone validation
├── requirements.txt         # Pinned dependencies
├── .env                     # Your API credentials (not in repo)
├── LICENSE                  # License & Terms of Service
│
├── funcs/
│   ├── ui.py                # Rich console styling, prompts, spinners
│   ├── helpers.py           # Session loading, member saving helpers
│   └── options_handlers/
│       ├── login.py         # Phone, QR, TData login flows
│       ├── scrape_members.py# Non-hidden & hidden member scraping
│       ├── add_members.py   # Rush & calm member adding
│       ├── broadcast_message.py # Message broadcast to scraped members
│       ├── manage_sessions.py # List, test, cleanup sessions
│       └── about.py         # About screen
│
├── sessions/                # Encrypted session CSVs (not in repo)
├── logs/                    # Rotating log files (not in repo)
├── members.csv              # Scraped member data (not in repo)
└── scrape_checkpoint.json   # Resume checkpoint (not in repo)
```

[Get Access to ALL FILES](https://github.com/AbirHasan2005/TelegramScraper?tab=readme-ov-file#support--pricing)
---

<!-- ============================== FOOTER ============================== -->

<div align="center">

<br/>

<img src="https://capsule-render.vercel.app/api?type=rounded&color=0:000000,50:001F0D,100:000000&height=80&section=footer&text=&fontSize=0" width="100%"/>

<br/>

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Source%20Code%20Pro&size=14&duration=4000&pause=1000&color=00FF88&center=true&vCenter=true&width=500&lines=Made+with+%E2%9D%A4%EF%B8%8F+by+VarshuAi;Build+Fast.+Ship+Secure.+Scale+Infinite.)](https://github.com/VarshuAi)

<br/>

[![GitHub](https://img.shields.io/badge/VarshuAi-Profile-00FF88?style=for-the-badge&logo=github&logoColor=black)](https://github.com/VarshuAi)
[![Repo](https://img.shields.io/badge/TelegramScraper-Repo-00CC66?style=for-the-badge&logo=github&logoColor=black)](https://github.com/VarshuAi/TelegramScraper)

<br/>

</div>
