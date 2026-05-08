# Planning Poker

A serverless, peer-to-peer planning poker app built with a single HTML file and [PeerJS](https://peerjs.com/). No backend, no accounts, no install — just open and play.

## How it works

Connections are established directly between browsers using **WebRTC DataChannels**. PeerJS's public signaling server is used only for the initial handshake (exchanging network addresses); all game data flows peer-to-peer after that.

One player acts as **host** — their browser ID becomes the Room ID others use to join. The host holds the authoritative game state and broadcasts it to all connected clients after every action.

## Hosting on GitHub Pages

1. **Fork or create a repository** on GitHub and add `planning-poker.html` to the root.

2. **Enable GitHub Pages** in your repository:
   - Go to **Settings → Pages**
   - Under *Source*, select **Deploy from a branch**
   - Choose `main` (or `master`) and `/ (root)`, then click **Save**

3. **Access your app** at:
   ```
   https://<your-username>.github.io/<your-repo-name>/
   ```

GitHub Pages is free for public repositories and requires no configuration beyond the steps above.

## Usage

1. Open the app and enter your name.
2. Click **Create new room** — your Room ID appears in the sidebar.
3. Share the Room ID with your team. They paste it into **Join room**.
4. Each player picks a card. Once everyone has voted, **Reveal votes** appears.
5. Click **New round** to reset and estimate the next story.

## Limitations

- The room lives as long as the host's browser tab is open. If the host leaves, the session ends.
- PeerJS's free signaling server (`0.peerjs.com`) has no uptime guarantee. For production use, self-host [`peerjs-server`](https://github.com/peers/peerjs-server).
- WebRTC requires a modern browser (Chrome, Firefox, Safari, Edge).
