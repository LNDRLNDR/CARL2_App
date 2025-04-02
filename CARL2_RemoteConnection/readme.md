# 🛰️ WebSocket Local Proxy Tool for CARL2

A simple Node.js-based WebSocket relay that allows remote PCs on the same network to connect to CARL2 running on a game
PC. This tool forwards WebSocket messages locally so the CARL2 client on the remote machine can receive live game data
from the game PC.

---

## 🔧 How to Use

1. Download this CARL2 Proxy package and
   unzip: [Download](https://github.com/LNDRLNDR/CARL2_App/raw/refs/heads/main/CARL2_RemoteConnection/CARL2Proxy.zip)

2. **Edit `config.json`:**  
   Set the `"remote_ip"` field to the IP address of the game PC (the one running RocketLeague with CARL2).

    ```json
    {
      "remote_ip": "192.168.1.45",
      "remote_port": 49446,
      "local_port": 49446,
      "debug": true
    }
    ```

3. **Install dependencies (first time only):**

    ```bash
    npm install
    ```

4. **Run the relay:** Double-click `run.bat`


5. **Connect from CARL2 client:** Open CARL2 on your Non-Game PC and it should connect automatically if you set the
   correct Game PC IP in the config.json


6. **On the game PC:** Make sure CARL2 has been launched at least once to install the required plugin. After that, you can close it — the plugin stays installed.

---

## 💡 What It Does

- Acts as a bridge between your **game PC** (running RocketLeague & CARL2 to collect game data) and your **remote PC** (running CARL2
  to visualize game data).
- Each remote PC should run its own instance of the proxy tool (only once per machine). Multiple remote PCs can connect
  to the same game PC.

---

## 📦 Requirements

- [Node.js](https://nodejs.org/)
- The only dependency is the [`ws`](https://www.npmjs.com/package/ws) WebSocket library:

```bash
npm install
```

---

## 📁 File Structure

```
/CARL2_RemoteConnection
├── config.json      # Set your game PC's IP + ports here
├── index.js         # Main WebSocket proxy script
├── run.bat          # Shortcut for Windows
└── package.json     # Includes ws dependency
```

---

## ❓FAQ / Notes

- There’s no IP detection or fancy UI — make sure you know your game PC’s local IP (e.g. 192.168.1.x).
- Make sure the local firewall on the game PC allows inbound WebSocket traffic on the chosen port.
- Logging/debug output is shown in the terminal window for now.
- No message modification or extra logic — it’s just a transparent relay.
- Ports can be remapped but only do this if you know what you're doing.
