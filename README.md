# Spades Night

A dependency-free, real-time multiplayer Spades game for 2–8 players.

## Run it

Install Node.js 18 or newer, open a terminal in this folder, and run:

```sh
node server.js
```

Keep that terminal running, then open `http://localhost:3000` to create a room. **Do not open `index.html` directly**; room creation needs the server. Players on the same Wi-Fi can use the invite link or the host computer's local network address, for example `http://192.168.1.20:3000`. To play across different networks, deploy this folder to a Node.js host and share its public URL. Room state is held in memory, so games reset if the server restarts.

If PowerShell says `node` is not recognized and you are using the Codex desktop app, run `.\start.ps1` from this folder. It uses the Node runtime bundled with Codex. You can also run the bundled executable directly:

```powershell
& "$env:USERPROFILE\.cache\codex-runtimes\codex-primary-runtime\dependencies\node\bin\node.exe" .\server.js
```

## Share a public link without keeping your computer on

The folder includes `package.json` and `render.yaml` for a starter Render deployment:

1. Create a GitHub repository, then use GitHub's **Add file → Upload files** to upload the files in this folder to the repository root.
2. In Render, connect GitHub and create a **Blueprint** from that repository. Render reads `render.yaml` and deploys the web service.
3. When deployment finishes, share the service's public `onrender.com` address. Friends open the same link on phones or computers and enter the room code.

The included config selects Render's free service tier. A free service spins down after 15 minutes without incoming traffic and may take about a minute to wake on the next visit. This game keeps rooms in server memory, so a restart, spin-down, or redeploy clears active rooms; start a new room after the service wakes. For sessions that must stay available continuously, use an always-on single instance or add persistent shared storage before scaling to multiple instances.

Four players use two teams, with opposite seats as partners. Other table sizes use individual cutthroat scoring. Bids, nil, bags, and the 500-point finish follow the rules approved in chat.
