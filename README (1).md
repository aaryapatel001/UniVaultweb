# UniVault — AI Coding Platform

## 👥 Team Members

| Name | Email |
|---|---|
| Shrey Patel | shreypatel2201@gmail.com |
| Nachiket Acharya | nachiketnacharya@gmail.com |
| Aarya Patel | aaryap971@gmail.com |
| Krish Prajapati | krishprajapati2147@gmail.com |

---

> A feature-rich, single-file web application for competitive programming practice, AI-assisted learning, and Web3-powered developer reputation — all in one sleek dark-mode interface.

---

## 📌 Overview

UniVault is a self-contained HTML application that combines a LeetCode-style problem set, an in-browser code editor, AI tutoring, leaderboards, and blockchain-based developer credentials. It requires **no backend, no build step, and no dependencies** beyond a modern browser.

---

## 🚀 Features

### 🏠 Home / Landing Page
- Animated hero section with a floating code preview card
- Starfield background with subtle twinkling animation
- Light pillar visual effect (canvas-based)
- Call-to-action buttons for Sign Up and Demo

### 🔐 Authentication
- Sign Up and Login pages with form validation
- OAuth-style "Continue with Google / GitHub" buttons (UI only)
- Smooth page transitions between auth and main app

### 🧠 Practice Problems
- Curated set of coding problems with Easy / Medium / Hard difficulty tags
- Per-problem tags (Arrays, DP, Graphs, Trees, etc.)
- Problem filtering by difficulty and topic
- Acceptance rate and submission count display

### 💻 In-Browser Code Editor
- Full-screen split-panel layout: problem description on the left, editor on the right
- Syntax-highlighted `<textarea>` with JetBrains Mono font
- Language selector (Python, JavaScript, C++, Java)
- **Run Code** — simulates execution and shows output panel
- **Submit** — evaluates against test cases and shows pass/fail results
- Timer that tracks time spent per problem
- Keyboard shortcut support

### 🤖 AI Tutor
- Interactive chat interface powered by the Anthropic Claude API (`claude-sonnet-4-20250514`)
- Context-aware: automatically includes the active problem + user's current code in every message
- Streaming-style response display
- Suggested prompt chips (Hint, Explain, Optimize, Debug, Complexity)
- Conversation history persisted during the session

### 📊 Dashboard & Profile
- Solved problem counts by difficulty
- Submission heatmap (GitHub-style activity grid)
- Language usage breakdown
- Personal stats: ranking, streak, acceptance rate
- Recent activity feed

### 🏆 Leaderboard
- Global rankings table with rank, username, score, problems solved, and streak
- Highlight for the logged-in user's row
- Country flags and badge icons

### 🌐 Web3 / Blockchain Features
Simulated on-chain interactions with mock transaction hashes:

| Feature | Description |
|---|---|
| **Wallet Connect** | Connect MetaMask or WalletConnect (simulated) |
| **Mint Achievement NFT** | Mint a badge NFT for completing a problem set |
| **Publish Reputation Score** | Publish your coding score on-chain |
| **Mint Certificate NFT** | Permanent on-chain certificate for practice sessions |
| **Code Ownership** | SHA-256 fingerprint of your code stored via IPFS simulation |
| **Freelance Marketplace** | Post and hire developer gigs, pay with `UNE` token |

All Web3 actions show loading modals and success/failure states with simulated transaction hashes.

### 🎨 UI / Theming
- Dark mode by default (`#060a12` background)
- Light mode toggle available
- CSS custom properties throughout for easy theming
- Glassmorphism cards, glowing buttons, and gradient accents
- Floating navbar with three-panel layout (logo | links | profile)
- Fully responsive for mobile and desktop
- Smooth `fadeUp` page transition animations

---

## 🗂 File Structure

This is a **single-file application** — everything is contained in one `.html` file:

```
coderank_updated.html
├── <head>          — Fonts (Inter, JetBrains Mono, Fraunces, Caveat), CSS variables
├── <style>         — ~10,000 lines of scoped CSS for all pages and components
├── <body>          — All page markup (Home, Auth, Practice, Coding, AI, Dashboard, Web3, Marketplace)
└── <script>        — All JS: routing, editor logic, AI API calls, Web3 simulations, starfield canvas
```

---

## ⚙️ Setup & Usage

### Running Locally

No installation needed. Just open the file in a browser:

```bash
# Option 1 — double-click the file in your file manager

# Option 2 — serve locally to avoid CORS issues with the Anthropic API
npx serve .
# then open http://localhost:3000/coderank_updated.html
```

### AI Tutor API Key

The AI Tutor makes calls to the Anthropic API. The fetch call in the script is set up to work with the Claude.ai Artifact environment (no API key header needed). If running outside Claude.ai, you must add your API key:

```js
headers: {
  "Content-Type": "application/json",
  "x-api-key": "YOUR_ANTHROPIC_API_KEY",   // add this line
  "anthropic-version": "2023-06-01"
}
```

> ⚠️ Never expose your API key in client-side code in production.

---

## 🛠 Technologies Used

| Technology | Usage |
|---|---|
| Vanilla HTML / CSS / JS | Entire app — no framework |
| CSS Custom Properties | Theming and dark/light mode |
| Canvas API | Starfield background, light pillar effect |
| Anthropic Claude API | AI Tutor chat (`claude-sonnet-4-20250514`) |
| Web Crypto API | SHA-256 code fingerprinting for ownership feature |
| Google Fonts | Inter, JetBrains Mono, Fraunces, Caveat |

---

## 📐 Architecture Notes

- **Routing** is handled by toggling `.on` CSS class on `.pg` (page) elements — no URL routing.
- **State** is maintained entirely in JavaScript variables (no localStorage).
- **AI context** is built dynamically each turn by reading the active problem title and the current textarea value.
- **Web3 actions** are fully simulated — no actual wallet or blockchain connection is made. Mock transaction hashes are generated client-side.
- The **starfield** and **light pillar** are fixed-position canvas elements that sit behind all page content using `z-index` layering.

---

## 📄 License

This project is a frontend prototype / demo. No license is specified. Please add one before distributing.

---

## 🙋 Contributing

Since this is a single-file project, contributions can be made by editing the HTML file directly. Suggested areas for improvement:

- Extract CSS into a separate stylesheet
- Add real backend / auth (Supabase, Firebase)
- Integrate a real code execution engine (Judge0, Piston API)
- Connect actual Web3 wallet (ethers.js / wagmi)
- Add more problems to the problem set
