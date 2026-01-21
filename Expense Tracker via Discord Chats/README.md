### Expense Tracker - n8n Workflow (with Discord)
**The Process:**  
**Schedule Trigger** (Daily at Midnight) → **Fetch Messages** from Discord Channel (Batch of 50) → **Filter & Parse** (Javascript + Static Memory) → **Append Rows** to Google Sheet → **Calculate** Totals → **Send Summary** back to Discord.

**The Output (You get):**  
- A Google Sheet automatically populated with your spending (Date, Amount, Description, User). Customizable. 
- A daily "Morning Briefing" message in Discord: "📉 Daily Expense Report: You spent $45.50 yesterday."

<img width="1051" height="182" alt="image" src="https://github.com/user-attachments/assets/2c6d1294-7650-4736-b017-5bad393017d3" />


#### How to Set Up
**1. This workflow uses the following 'stuff'.**
- n8n (Self-hosted or Cloud).
- Discord Account with a private server.
- Google Account for Sheets.


**2. Create the Discord Bot: You need a "Bot Token" to read your messages.**
- Go to the Discord Developer Portal.
- Create a New Application → Go to Bot → Click "Reset Token" (Save this!).
- Crucial: Scroll down and enable "Message Content Intent".
- Copy this link and replace `YOUR_CLIENT_ID` with the "Application ID" found on your bot's General Information page: `https://discord.com/api/oauth2/authorize?client_id=YOUR_CLIENT_ID&permissions=3072&scope=bot`

Copy & paste that into your browser, and it _will_ work. Authorize the bot for your server/user profile.

**3. Prepare Google Sheets**
Create a new Sheet with the following headers in Row 1: `Date` | `Amount` | `Description` | `User`

**4. Configure n8n**
- Import the JSON: Copy the JSON file from this repo and paste it into n8n.  
- Credentials:  
  - Create a generic Header Auth credential for Discord: Authorization: Bot YOUR_TOKEN_HERE.  
  - Connect your Google account.

Node Settings:
- In the Discord nodes, copy/paste your Channel ID (Right-click channel in Discord > Copy ID).
- In the Google Sheets node, select your specific file.

#### Usage
Just text your bot naturally throughout the day:  
"15 Lunch" "4.50 Coffee" "120 Groceries"

The bot wakes up at midnight, logs everything to the sheet, and tells you the total.

Last updated: Jan 21, 2026
