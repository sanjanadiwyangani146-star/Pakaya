# FLASH MD MINI BOT 🐼

A powerful WhatsApp Multi-Device Bot using **dct-dula-baileys** with full command and plugin support.

## Features ✨

- ✅ Multi-number support
- ✅ MongoDB integration for session management
- ✅ Plugin system for easy command creation
- ✅ Auto-reply features (AI, status viewing, emoji reactions)
- ✅ Newsletter management
- ✅ Admin system with OTP verification
- ✅ Auto-reconnect on disconnection
- ✅ Material UI Dashboard
- ✅ RESTful API endpoints
- ✅ Customizable bot configurations per session

## Installation 📦

### Prerequisites
- Node.js >= 20.x
- npm or yarn
- MongoDB account (free tier available)

### Setup Steps

1. **Clone or Download the Repository**
```bash
cd my\ base\ 🥲⚡
```

2. **Install Dependencies**
```bash
npm install
```

3. **Configure Environment Variables**
```bash
# Copy the example file
cp .env.example config.env

# Edit config.env with your settings
```

4. **Start the Bot**
```bash
npm start
# or
node index.js
```

The bot will start on `http://localhost:8000`

## Configuration 🔧

### Key Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `MONGO_URI` | MongoDB connection string | Required |
| `BOT_NAME` | Bot display name | FLASH MD MINI |
| `PREFIX` | Command prefix | . |
| `OWNER_NUMBER` | Owner's WhatsApp number | 94787072548 |
| `AUTO_AI` | Enable auto AI reply | true |
| `AUTO_LIKE_STATUS` | Auto like status updates | true |
| `AUTO_VIEW_STATUS` | Auto view status updates | true |

### Work Types
- `public` - Bot works everywhere (default)
- `private` - Only owner can use commands
- `inbox` - Works only in private chats
- `groups` - Works only in group chats

## API Endpoints 🔌

### Bot Management
- `GET /code` - Connect new number
- `GET /code/active` - List active sessions
- `GET /code/ping` - Health check
- `GET /code/reconnect` - Reconnect all sessions

### Admin Management
- `POST /code/admin/add` - Add admin
- `POST /code/admin/remove` - Remove admin
- `GET /code/admin/list` - List admins

### Newsletter Management
- `POST /code/newsletter/add` - Add newsletter
- `POST /code/newsletter/remove` - Remove newsletter
- `GET /code/newsletter/list` - List newsletters

### Configuration
- `GET /code/update-config` - Update user config (requires OTP)
- `GET /code/verify-otp` - Verify OTP

## Plugin Development 🔌

### Plugin Structure
```javascript
module.exports = {
  name: "plugin-name",
  command: ["cmd1", "cmd2"],
  category: "category-name",
  
  async execute({ socket, msg, args, command, config, isOwner, isGroup, sender }) {
    // Plugin code here
  }
};
```

### Example Plugin
```javascript
module.exports = {
  name: "hello",
  command: ["hello", "hi"],
  
  async execute({ socket, msg, sender }) {
    await socket.sendMessage(sender, {
      text: "👋 Hello! How are you?"
    }, { quoted: msg });
  }
};
```

Plugins are automatically loaded from the `plugins/` directory.

## Commands 📝

### Built-in Commands
- `.alive` - Bot status
- `.menu` - Command list
- `.ping` - Response time
- `.system` - System info
- `.owner` - Owner contact
- `.pair <number>` - Pair new session
- `.freebot` - Free bot pairing

## Database Schema 🗄️

MongoDB Collections:
- `sessions` - Store user credentials
- `numbers` - Active bot numbers
- `admins` - Admin list
- `newsletter_list` - Followed newsletters
- `configs` - User-specific configurations
- `newsletter_reacts` - Newsletter reaction emojis

## Project Structure 📁

```
.
├── index.js              # Express server
├── start.js              # Core bot logic
├── settings.js           # Configuration loader
├── id.js                 # ID generation utility
├── admin.json            # Admin list
├── package.json          # Dependencies
├── public/               # Web static files
│   ├── main.html
│   └── pair.html
└── plugins/              # Command plugins
    ├── alive.js
    ├── system.js
    ├── owner.js
    ├── mainmenu.js
    └── freebot.js
```

## Error Fixes Applied ✅

1. **Fixed Baileys Package**: Updated from `dew-baileys` to `dct-dula-baileys`
2. **Added Missing Dependencies**: body-parser, dotenv
3. **Fixed Import Path**: Changed `@whiskeyshokets/baileys` to `dct-dula-baileys`
4. **Added fetchJson Helper**: For AUTO_AI functionality
5. **Fixed Config References**: RCD_IMAGE_PATH → IMAGE_PATH
6. **Added Error Handling**: Proper middleware error handling in Express
7. **Enhanced Settings**: Added missing config options (AUTO_TYPING, AUTO_READ_MESSAGE, WORK_TYPE, ANTI_CALL)

## Troubleshooting 🔍

### Bot Not Connecting
- Check MongoDB connection string
- Verify WhatsApp account is not banned
- Check if phone number format is correct

### Commands Not Working
- Ensure prefix is correct
- Check if sender is admin/owner for restricted commands
- Verify plugin syntax in plugins folder

### Session Issues
- Delete the session folder in temp directory
- Reconnect using `/code/reconnect` endpoint
- Clear MongoDB sessions collection

## License 📄

MIT License - Feel free to use and modify

## Support 💬

For issues and questions:
- Create an issue on GitHub
- Contact the bot owner via WhatsApp

---

**Maintained with ❤️ by FLASH Team**
