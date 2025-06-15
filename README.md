# Flirty AI Telegram Bot

A Telegram chatbot powered by Google's Gemini AI model that can engage in flirty and NSFW conversations without restrictions.

## Features

- Flirty and unrestricted conversations with no content limitations
- Advanced NSFW content capability 
- Conversation history tracking for more coherent interactions
- Personalized responses using your name
- **User authorization system** to control who can use your bot
- Command system:
  - `/start` - Begin interaction with the bot
  - `/help` - Display available commands
  - `/reset` - Reset the conversation history
  - `/flirt` - Receive a random flirty message
  - `/whoami` - Display your user and chat information
  - `/auth` - (Owner only) Authorize a user or chat
  - `/revoke` - (Owner only) Revoke authorization
  - `/listauth` - (Owner only) List all authorized users and chats
- Emoji-enhanced responses for a more engaging experience

## Setup Instructions

### Prerequisites
- Python 3.9+
- A Telegram bot token (created through @BotFather on Telegram)
- A Google Gemini API key
- Your Telegram user ID (to set as the owner)

### Installation

1. Clone this repository:
```bash
git clone https://github.com/yourusername/ai-telegram-chatbot.git
cd ai-telegram-chatbot
```

2. Install the required dependencies:
```bash
pip install -r requirements.txt
```

3. Set up your environment variables:
   - Add your Telegram Bot Token, Gemini API key, and owner ID to the `.env` file:
   ```
   TELEGRAM_BOT_TOKEN=your_telegram_bot_token_here
   GEMINI_API_KEY=your_gemini_api_key_here
   OWNER_ID=your_telegram_user_id_here
   ```

### Getting the API Keys and User ID

#### Telegram Bot Token
1. Open Telegram and search for @BotFather
2. Start a chat with BotFather and send the command `/newbot`
3. Follow the instructions to create a new bot
4. Once created, BotFather will give you a token - copy this to your `.env` file

#### Google Gemini API Key
1. Go to https://ai.google.dev/
2. Sign in or create a Google account
3. Navigate to the API section and create a new API key
4. Copy this key to your `.env` file

#### Getting Your Telegram User ID
1. Start a chat with @userinfobot on Telegram
2. The bot will reply with your user ID
3. Copy this ID to the `OWNER_ID` field in your `.env` file

### Running the Bot

Run the bot with the following command:
```bash
python main.py
```

The bot will start running, and you can now interact with it through Telegram.

## Authorization System

By default, only the owner (you) can use the bot. To allow others to use it:

### Authorizing Users and Chats

As the owner, you can authorize specific users or group chats:

1. To authorize a user:
```
/auth user <user_id>
```

2. To authorize a chat (group):
```
/auth chat <chat_id>
```

Users can find their user ID by using the `/whoami` command.

### Revoking Authorization

To revoke access:

1. For a user:
```
/revoke user <user_id>
```

2. For a chat:
```
/revoke chat <chat_id>
```

### Viewing Authorized Users and Chats

To see all authorized users and chats:
```
/listauth
```

## Customization

You can customize the bot's behavior by:

1. Modifying the system instruction in the `create_model()` function in `main.py`
2. Adding or changing the flirty messages in the `FLIRTY_MESSAGES` list
3. Adjusting the conversation history limit (currently set to 10 messages)

## Disclaimer

This bot is intended for adult use only. By using this bot, you acknowledge that you are of legal age in your jurisdiction and take full responsibility for its use and any consequences thereof.

## Deployment on Koyeb

### What is Koyeb?

Koyeb is a developer-friendly serverless platform that allows you to deploy applications globally. It's perfect for hosting Telegram bots as it provides always-on services with automatic scaling.

### Deployment Steps

1. **Sign up for Koyeb**
   - Create an account at [koyeb.com](https://www.koyeb.com/)

2. **Set up your project for deployment**
   - Ensure your repository contains:
     - `requirements.txt` (with all dependencies)
     - `Procfile` (specifying the command to run)
     - `runtime.txt` (specifying Python version)
     - `Dockerfile` (if you prefer Docker deployment)

3. **Deploy to Koyeb**
   - From the Koyeb dashboard, click "Create App"
   - Choose "GitHub" as the deployment method
   - Select your repository
   - Configure the following environment variables:
     ```
     TELEGRAM_BOT_TOKEN=your_telegram_bot_token_here
     GEMINI_API_KEY=your_gemini_api_key_here
     OWNER_ID=your_telegram_user_id_here
     OWNER_NAME=your_name_here
     WEBHOOK_URL=https://your-app-name.koyeb.app/
     ```
   - Click "Deploy"

4. **Configure Webhooks (Optional)**
   - By default, the bot will automatically configure webhooks when deployed to Koyeb
   - If you want to manually set the webhook, you can use the Telegram Bot API:
     ```
     https://api.telegram.org/bot<TELEGRAM_BOT_TOKEN>/setWebhook?url=https://your-app-name.koyeb.app/<TELEGRAM_BOT_TOKEN>
     ```

5. **Verify Deployment**
   - Once deployed, your bot should be online and responsive
   - You can check the logs in the Koyeb dashboard for any issues

### Maintaining Your Deployed Bot

- **Scaling**: Koyeb automatically scales your application as needed
- **Updates**: Push changes to your GitHub repository, and Koyeb will automatically redeploy
- **Monitoring**: Use the Koyeb dashboard to monitor your application's performance and logs

### Troubleshooting

- If your bot isn't responding, check:
  - The logs in the Koyeb dashboard for errors
  - That all environment variables are correctly set
  - That the webhook URL is correctly configured 
  - ex1234567