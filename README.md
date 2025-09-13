# Haveno Telegram Addon

<p align="center">
<a href="https://haveno.app"><img src="https://github.com/KewbitXMR/haveno-app/blob/main/assets/android-chrome-512x512.png?raw=true" width=150 /></a>
<br>
<a href="https://haveno.app"><img src="https://raw.githubusercontent.com/KewbitXMR/haveno-app/refs/heads/main/assets/icon/side1.webp" width=100 /></a>
<a href="https://haveno.app"><img src="https://raw.githubusercontent.com/KewbitXMR/haveno-app/refs/heads/main/assets/icon/270a7bad400e6824b8ea9f238f66b61a.webp" width=275 /></a>
<a href="https://haveno.app"><img src="https://raw.githubusercontent.com/KewbitXMR/haveno-app/refs/heads/main/assets/icon/side2.webp" width=100 /></a>
</p>

---

A self-hosted Telegram bot that gives you a **command-line–like interface over chat** to your own [Haveno](https://haveno.app) node.  
Think of it as a **secure CLI in your pocket**: run commands, query markets, and manage your Haveno daemon directly from a private Telegram chat.

⚠️ **Important:** You host this bot yourself. There is no central Haveno bot and there never will be, that would compromise Haveno’s decentralized nature.  

---

## ✨ Features

- **Interactive CLI-like chat**: issue commands (`/markets`, `/balance`, `/orders`, etc.) and receive structured responses.
- **Self-hosted**: you deploy the bot, you control the keys, you control the connection.
- **Private**: runs in your own Telegram account or private group; no data leaves your environment.
- **Haveno integration**: communicates with your local Haveno daemon over gRPC/JSON-RPC.
- **Extendable**: add new commands to wrap Haveno RPC calls or custom workflows.
- **Lightweight**: written in Python, easy to run in Docker or directly on your server.

---

## 🚀 Getting Started

### Prerequisites
- A running Haveno daemon (with gRPC/JSON-RPC enabled).
- Python 3.9+ (or [Docker](https://hub.docker.com/repositories/havenodex)).
- A Telegram account and [BotFather](https://core.telegram.org/bots#botfather) token.

### 1. Clone the repository
```bash
git clone https://github.xom/KewbitXMR/haveno-telegram-addon.git
cd haveno-telegram-addon
```

### 2. Set up environment variables
Create a `.env` file:
```ini
TELEGRAM_TOKEN=123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11   # from BotFather
ALLOWED_USER_ID=123456789                                  # your Telegram user ID
HAVENO_GRPC_URL=127.0.0.1:50051                            # Haveno gRPC endpoint
```

### 3. Install dependencies
```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### 4. Run the bot
```bash
python haveno_bot.py
```

Now open Telegram, find your bot, and start chatting with it!

---

## 📚 Usage

The bot behaves like a CLI inside Telegram:

```
/help
Available commands:
/markets      – Show current markets
/balance      – Show wallet balances
/orders       – List open orders
/order <id>   – Show order details
/buy <amount> – Create a buy offer
/sell <amount> – Create a sell offer
```

Responses are formatted for readability but designed to mirror CLI output.

---

## 🛡️ Security Considerations

- **Run locally or on your own server.** Do **not** rely on third-party hosting.
- **Restrict access**: the bot checks your Telegram user ID (`ALLOWED_USER_ID`). Do not expose it to public groups.
- **Keep your tokens safe**: never share your Telegram bot token or Haveno RPC credentials.
- **Tor/I2P recommended**: for full privacy, route traffic between the bot and Haveno daemon through Tor/I2P.

---

## 🐳 Docker Deployment

Build and run the bot in Docker:

```bash
docker build -t haveno-telegram-addon .
docker run -d --name haveno-telegram-addon --env-file .env haveno-telegram-addon
```

---

## 🧩 Extending

New commands can be added by editing `commands.py`:

```python
@bot.command("my_custom")
def my_custom_command(args):
    # Call Haveno RPC here
    return "Custom response!"
```

Restart the bot, and your new command is available in Telegram.

---

## 🤝 Contributing

Contributions are welcome! Please open issues or submit pull requests via [git.haveno.app](https://github.com/KewbitXMR/haveno-telegram-addon).

---

## 📜 License

Licensed under the **GNU Affero General Public License v3 or later (AGPL-3.0+)**.  
You are free to use, modify, and share, but changes must remain open-source when deployed as a network service.

---

## 🌐 Project Links

- [Haveno App Website](https://haveno.app)  
- [Haveno App Documentation](https://haveno.app/documentation/)  
- [Haveno App Issues](https://github.com/KewbitXMR/haveno-network/haveno-telegram-addon/issues)

---

👉 This bot is a **personal interface** to your Haveno node, it's not a centralized service.  
If someone offers you a pre-hosted “Haveno Telegram Bot,” they’re missing the whole point.  
