# Mudassar WhatsApp MD Bot (Baileys + Pairing Code)

Production-ready, modular WhatsApp Multi-Device bot built with Node.js and Baileys.

## Features
- Pairing code authentication (no QR scanning)
- Auto-reconnect and session persistence in `session/`
- Dynamic plugin loader (`plugins/*.js`)
- Prefix command system (`!` and `.` by default)
- Message + status emoji reactions
- Owner-only control commands
- JSON database backend (`database/database.json`)
- Docker-ready deployment

## Project Structure
```text
project-root
├── package.json
├── index.js
├── config.js
├── .env
├── README.md
├── Dockerfile
├── connection/
│   └── whatsapp.js
├── handlers/
│   ├── commandHandler.js
│   └── eventHandler.js
├── plugins/
│   ├── ping.js
│   ├── menu.js
│   ├── downloader.js
│   ├── react.js
│   ├── status.js
│   └── owner.js
├── database/
│   └── database.json
├── utils/
│   ├── helpers.js
│   └── downloader.js
├── session/
└── media/
```

## Setup
1. Install Node.js LTS.
2. Install dependencies:
   ```bash
   npm install
   ```
3. Edit `.env` if needed.
4. Start bot:
   ```bash
   node index.js
   ```

## Pairing Code Login Flow
1. Start bot with `node index.js`.
2. Enter your WhatsApp number (with country code) when prompted.
3. Bot prints pairing code in terminal.
4. On WhatsApp open **Settings → Linked Devices → Link with phone number**.
5. Enter pairing code.
6. Session is saved in `session/` for future restarts.

## Commands
- `!ping` → Pong check
- `!menu` → Command list
- `!download <url>` → Media downloader (TikTok implemented, YouTube/Instagram ready for API integration)
- `!react <emoji>` → React with custom emoji

### Owner Commands (923216046022)
- `!restart`
- `!shutdown`
- `!broadcast <message>`
- `!reload`

## Deployment
### Local / VPS
```bash
npm install
node index.js
```

### Docker
```bash
docker build -t mudassar-md-bot .
docker run -it --name mudassar-bot mudassar-md-bot
```

## Notes
- Keep API keys and sensitive values in `.env`.
- Replace downloader endpoints in `utils/downloader.js` for full production media support.
- To add commands, create a new file in `plugins/` exporting `{ name, description, execute }`.
