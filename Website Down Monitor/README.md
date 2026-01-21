### Website Down Monitor - n8n Workflow
**The Process:**  
**Schedule Trigger** (Every 10 mins) → **Ping Website **(HTTP HEAD) → **Check Status** Code (If != 200) → **Send Email Alert.**

**The Output (You get):**  
A "Dead Man's Switch" for your projects. If your site goes down (404/500 error), you get an email instantly. If it's healthy, the workflow does nothing.  

<img width="1348" height="261" alt="image" src="https://github.com/user-attachments/assets/8b2005d9-6ba4-4772-811b-666a0fbe87b9" />

_Critical note: Some website hosting services, like Cloudflare, have strict gatekeeping processes where the website is not accessible to computers (CAPTCHA). This often results in Status Code 403, which does not mean that the website is down— it's just inaccessible._

#### How to Set Up
**1. Configure n8n**
- Import the JSON: Copy the JSON file from this repo.
- Credentials: Connect your Google/Gmail account.
- Node Settings:
   - In the HTTP Request node, replace the URL with your own website.
   - In the Gmail node, enter your destination email address (add credentials if necessary).

Important: Ensure "Never Error" is toggled ON in the HTTP node options (otherwise the workflow fails before sending the alert).

**2. Test It**  
- Change the HTTP URL to a broken link (e.g., https://google.com/404-test).
- Run the workflow manually.
- Check your inbox for the alert.

Last updated: Jan 21, 2026
