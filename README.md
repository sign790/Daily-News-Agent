# Daily News Agent

A personal daily news briefing tool built with the OpenAI Agents SDK. It fetches RSS news sources every day, lets an Agent select the most important stories, generates a Chinese email briefing, and sends it to the specified email address.

## Features

Fetches RSS sources such as BBC, Bloomberg, CoinDesk, The Verge, and more
Covers global headlines, technology and AI, geopolitics, macro markets, crypto policy, China-related international news, and major sports events
Outputs up to 12 news items by default
Supports dry-run testing without sending emails
Supports sending emails via SMTP
Supports scheduled runs at a fixed time
Local-first design


## Local-first design

This project is meant to be downloaded and run locally. It asks for an OpenAI API key and an email SMTP app password, so a public hosted version would need account systems, encrypted secret storage, abuse prevention, rate limits, billing controls, and a safer credential flow.

For most users, the safest setup is:

1. Clone the repo.
2. Copy `.env.example` to `.env`.
3. Fill in their own keys and email settings locally.
4. Run `python web_app.py` and use the local browser UI.

## Installation

```powershell
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

## Configuration

Copy .env.example to .env, then fill in your own configuration:

```env
OPENAI_API_KEY=your-openai-api-key
NEWS_AGENT_MODEL=gpt-5.4
NEWS_TIMEZONE=Asia/Shanghai
NEWS_RUN_TIME=09:00

NEWS_EMAIL_TO=receiver@example.com, second@example.com
NEWS_EMAIL_FROM=your-sender@gmail.com
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your-sender@gmail.com
SMTP_PASSWORD=
SMTP_USE_SSL=false
```

Multiple recipients can be separated by English commas, for example: 

NEWS_EMAIL_TO=receiver@example.com, second@example.com


## Web Interface

Start the local control panel:

python web_app.py

Then open:

http://127.0.0.1:8765

In the web interface, you can enter the model, recipient email, sender email, SMTP app password, topic preferences, final number of news items, and email requirements.

Secrets will be saved locally to .env. Do not upload .env to GitHub.

## Usage

Generate the briefing without sending an email:

python main.py --dry-run

Generate the briefing and send the email:

python main.py

Keep the program running and trigger it at the NEWS_RUN_TIME set in .env:

python main.py --schedule

## Security Notes

Use a dedicated secondary email account as the sender when possible
Use a Gmail App Password or an email SMTP authorization code for SMTP_PASSWORD; do not use your main email password
Do not commit .env, API keys, or email authorization codes to GitHub






