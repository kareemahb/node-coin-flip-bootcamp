# Coin Flip Game 🪙
 
A heads-or-tails guessing game with a Node.js back end built only from core modules. No Express and no dependencies. Pick a side, flip the coin, and the **server** decides the result while a gold coin spins in 3D in the browser.
 
🔗 **Live Demo:** [node-coin-flip-bootcamp-jtd5.onrender.com](https://node-coin-flip-bootcamp-jtd5.onrender.com/)
 
 
![Coin Flip Game with Heads and Tails buttons, a gold coin, and the Flip Coin button](image.png)
 

 
## ✨ Features
 
- **Server-side randomness**: the Node.js server flips the coin, not the browser, so the game has a real front-end-to-back-end request flow
- **3D coin animation**: a gold coin spins and lands on the side the server picked
- **Win or lose feedback**: shows your call, the coin result, and "You win!" or "You lose!"
- **Input checks**: the browser asks you to pick a side before flipping, and the API returns `400` if no choice is sent
- **No double flips**: the Flip button is disabled until the current flip finishes

 
## 🔍 How It Works
 
```
Pick heads/tails ──▶ GET /api?choice=heads ──▶ server flips with Math.random() ──▶ JSON ──▶ coin animation + result
```
 
The server (`backend/server.js`) uses Node's built-in `http`, `fs`, and `path` modules and routes each request by hand:
 
| Route                    | What it returns                  |
| ------------------------ | -------------------------------- |
| `/`                      | `api.html` (the game page)       |
| `/main.css`              | The stylesheet                   |
| `/js/main.js`            | The client-side script           |
| `/images/v1008-21-b.jpg` | The gold coin background image   |
| `/api?choice=…`          | JSON with the flip result        |
| anything else            | `404 - Page Not Found`           |
 
### API example
 
```
GET /api?choice=heads
```
 
```json
{
  "playerChoice": "heads",
  "coinResult": "tails",
  "message": "You lose!"
}
```
 
If `choice` is missing, the API returns status `400` with `{ "error": "Please choose heads or tails." }`.
 

 
## 🛠️ Tech Stack
 
- **Node.js** (`http`, `fs`, `path`; no frameworks)
- **HTML5**
- **CSS3** (3D transforms, `perspective`, keyframe animations)
- **JavaScript** (DOM manipulation, Fetch API)
- **Render** for hosting

 
## 📁 Project Structure
 
```
node-coin-flip-bootcamp/
├── api.html          # Game page: choice buttons, coin, results
├── main.css          # Styling and the 3D coin flip animation
├── js/
│   └── main.js       # Handles clicks, calls the API, runs the animation
├── backend/
│   └── server.js     # Node HTTP server: serves files and the /api route
├── images/
│   └── v1008-21-b.jpg
├── image.png         # README screenshot
└── package.json
```
 

 
## 🚀 Run It Locally
 
You need [Node.js](https://nodejs.org/) installed.
 
```bash
git clone https://github.com/kareemahb/node-coin-flip-bootcamp.git
cd node-coin-flip-bootcamp
npm start
```
 
Then open [http://localhost:8000](http://localhost:8000). The server uses the `PORT` environment variable when it's set (Render sets it), and falls back to `8000` otherwise.
 

 
## 💡 What I Learned
 
- Building an HTTP server and routing requests without a framework
- Serving HTML, CSS, JS, and image files with `fs` and the right `Content-Type` headers
- Reading query parameters with the `URL` class
- Keeping game logic on the server and sending the result back as JSON
- Timing a CSS animation so the result appears after the coin lands
- Deploying a Node app to Render with a dynamic `PORT`

 
## 👩‍💻 Created By
 
**Kareemah Bahaadur**
[GitHub](https://github.com/kareemahb)
 
