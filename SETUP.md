# Quick Setup Guide

## 🚀 Getting Started in 5 Minutes

### Step 1: Install Dependencies
```bash
npm install
```

### Step 2: Configure Bot
```bash
# Copy example environment file
cp .env.example config.env

# Edit config.env with your settings
# Required: MONGO_URI, OWNER_NUMBER
```

### Step 3: Create/Configure MongoDB
1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a free account
3. Create a cluster
4. Get your connection string
5. Add it to `config.env` as `MONGO_URI`

### Step 4: Start Bot
```bash
npm start
# Bot will start on http://localhost:8000
```

### Step 5: Pair Your Number
1. Open `http://localhost:8000` in browser
2. Enter your WhatsApp number
3. Scan QR code with WhatsApp
4. Bot is ready to use!

---

## ⚙️ Configuration Settings

Key settings in `config.env`:

```env
# MongoDB (Required)
MONGO_URI=mongodb+srv://user:pass@cluster.mongodb.net/

# Bot Owner
OWNER_NUMBER=94787072548

# Features
AUTO_AI=true              # Auto reply with AI
AUTO_LIKE_STATUS=true     # Like status updates
AUTO_VIEW_STATUS=true     # View status updates
AUTO_RECORDING=false      # Show recording indicator

# Bot Info
BOT_NAME=FLASH MD MINI
PREFIX=.

# Server Port
PORT=8000
```

---

## 🛠️ Useful Commands

### Development
```bash
npm run dev      # Start with auto-reload
npm start        # Start production
```

### API Endpoints
- `GET http://localhost:8000/code/active` - Active sessions
- `GET http://localhost:8000/code/ping` - Health check
- `GET http://localhost:8000/` - Web dashboard

---

## 🔧 Using Commands

### Basic Commands
- `.alive` - Show bot status
- `.menu` - Show all commands
- `.ping` - Check response time
- `.system` - System information
- `.owner` - Owner contact

### Admin Commands
- `.pair <number>` - Pair new number

---

## 📁 File Structure

```
├── index.js           # Main server
├── start.js           # Bot logic
├── settings.js        # Config
├── package.json       # Dependencies
├── config.env         # Environment (create this)
├── plugins/           # Commands
│   ├── alive.js
│   ├── system.js
│   └── ...
└── public/            # Web files
```

---

## ❌ Troubleshooting

### Port Already in Use
```bash
# Use different port
PORT=3000 npm start
```

### Bot Not Connecting
1. Check `MONGO_URI` is correct
2. Check internet connection
3. Verify WhatsApp account is not banned

### Commands Not Working
1. Check PREFIX is correct (default: `.`)
2. Ensure you're sending `.command` not `!command`
3. Check bot is fully connected

---

## 📚 Documentation

- **README.md** - Full documentation
- **CHANGELOG.md** - What's new
- **.env.example** - All config options

---

## 🤝 Support

- Check README.md for detailed docs
- Review plugin examples in `plugins/`
- Check console for error messages

**Happy Bot Building! 🎉**
