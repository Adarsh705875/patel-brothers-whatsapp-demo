<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:075E54,50:128C7E,100:25D366&height=220&section=header&text=Patel%20Brothers%20AI%20Assistant&fontSize=42&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=WhatsApp-style%20grocery%20support%20powered%20by%20n8n%20%2B%20AI&descAlignY=58&descSize=18" width="100%" />

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=20&duration=3000&pause=1000&color=25D366&center=true&vCenter=true&width=650&lines=Ask+about+store+locations+%F0%9F%93%8D;Check+timings+and+weekly+deals+%F0%9F%8F%B7%EF%B8%8F;Place+grocery+orders+by+chat+%F0%9F%9B%92;Automated+with+n8n+and+an+AI+agent+%F0%9F%A4%96)](https://git.io/typing-svg)

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![n8n](https://img.shields.io/badge/n8n-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)
![Cloudflare](https://img.shields.io/badge/Cloudflare_Tunnel-F38020?style=for-the-badge&logo=cloudflare&logoColor=white)
![GitHub Pages](https://img.shields.io/badge/GitHub_Pages-222222?style=for-the-badge&logo=githubpages&logoColor=white)

### [🚀 **Live Demo**](https://adarsh705875.github.io/patel-brothers-whatsapp-demo/)

</div>

> ⚠️ **Disclaimer:** This is an independent learning prototype. It is **not affiliated with, endorsed by, or an official product of Patel Brothers or WhatsApp.** Store and deal data used in the demo is for demonstration only.

---

## 📸 Preview

<!-- Replace with your own screenshot or GIF: upload it to the repo and use the path below -->
<!-- ![Chat demo](./screenshots/demo.gif) -->

*Add a screenshot or GIF of the chat here.*

---

## 📖 Overview

An interactive **WhatsApp-style customer support web app** connected to an **n8n automation workflow** and an **AI agent**. It shows how a grocery retailer could handle repetitive customer questions (store locations, opening hours, weekly deals and ordering) through a familiar chat interface instead of a human replying to every message.

**Try asking:**

- "Hi"
- "Where is the nearest Patel Brothers store?"
- "What are your store timings?"
- "Show me this week's deals."
- "I want to place a grocery order."
- "Can I speak to a human representative?"

---

## ✨ Features

| | Feature | Details |
|---|---|---|
| 💬 | **WhatsApp-style chat UI** | Message bubbles, input box, send action, and a persistent session ID stored in the browser |
| 🤖 | **AI-powered replies** | Messages are processed by an AI agent connected to a configured language model |
| ⚙️ | **n8n orchestration** | A webhook receives each message and returns the AI response to the page |
| 📍 | **Store information** | Answers about locations, addresses, contact numbers and hours |
| 🏷️ | **Weekly deals** | Structured promotional data for deal-related questions |
| 🛒 | **Guided ordering** | Demonstrates a conversational grocery ordering flow |
| 🙋 | **Human handoff** | Recognizes requests to speak with a person |

---

## 🏗️ System Architecture

```mermaid
flowchart LR
    A[👤 Customer] -->|types message| B[💬 Chat UI<br/>GitHub Pages]
    B -->|POST + session ID| C[🌐 Cloudflare Tunnel]
    C --> D[⚙️ n8n Webhook]
    D --> E[🤖 AI Agent]
    E <--> F[(🗂️ Store & Deals Data)]
    E -->|response| D
    D -->|JSON reply| B
    B -->|shows reply| A
```

**Flow in short:** the frontend sends the message and session ID to an n8n webhook, the AI agent builds a reply using the configured instructions and business data, and n8n returns it to the chat window. The UI and the AI logic are separate, so the backend can change without rebuilding the frontend.

---

## 🧰 Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, JavaScript |
| Automation | n8n (webhook workflow) |
| AI | AI agent with a configured language model |
| Data | Structured store and deals records |
| Hosting | GitHub Pages (frontend), Cloudflare Tunnel (exposes n8n for demo) |

---

## 📁 Project Structure

```
patel-brothers-whatsapp-demo/
├── index.html      # Chat interface and webhook communication
└── README.md
```

---

## 🚀 Getting Started

### Run the frontend locally

```bash
git clone https://github.com/Adarsh705875/patel-brothers-whatsapp-demo.git
cd patel-brothers-whatsapp-demo
```

Open `index.html` in your browser, or serve it with any static server:

```bash
python -m http.server 8000
```

### Connect your own n8n backend

1. Install and start **n8n** (locally or on a server).
2. Create a workflow with a **Webhook** node (POST) that receives the customer's message and session ID.
3. Connect the webhook to an **AI Agent** node with your chosen language model, a system prompt and your store and deals data.
4. Return the agent's answer with a **Respond to Webhook** node.
5. Expose n8n for the demo, for example with a Cloudflare Tunnel:
```bash
   cloudflared tunnel --url http://localhost:5678
```
6. Put your webhook URL in `index.html` where the `fetch` call is made.
7. Activate the workflow and send a test message.

> 🔐 **Never commit API keys or credentials.** Keep model keys inside n8n credentials, not in `index.html`.

### Deploy on GitHub Pages

**Settings → Pages → Deploy from a branch → `main` / root.** Your site will be live at `https://adarsh705875.github.io/patel-brothers-whatsapp-demo/`.

---

## 🧪 Testing

Try these in the chat and check that each gets a sensible reply:

| Test message | Expected behavior |
|---|---|
| "Hi" | Friendly greeting |
| "Nearest store?" | Store location details |
| "What are your timings?" | Opening hours |
| "Show me this week's deals" | Current deals |
| "I want to order groceries" | Guided ordering prompts |
| "Talk to a human" | Handoff response |

---

## ⚠️ Limitations

- This is a **prototype**, not a production customer service system.
- The live demo only responds while the **n8n backend and tunnel are running**. Free Cloudflare quick tunnels also change their URL on restart, so the webhook URL may need updating.
- Answer quality depends on the model, system instructions and the data supplied.
- The chat UI only imitates WhatsApp. It does **not** use the official WhatsApp API.
- Data shown is sample data.

---

## 🔮 Future Enhancements

- [ ] Real WhatsApp Business API integration
- [ ] Connect to a live product and inventory database
- [ ] Order confirmation and payment flow
- [ ] Handoff to a real support agent
- [ ] Multi-language support
- [ ] Chat history and analytics dashboard
- [ ] Permanent hosted backend instead of a tunnel

---

## 🎓 What I Learned

- Building a chat interface with JavaScript and webhook communication
- Designing automation workflows in n8n
- Connecting an AI agent to structured business data
- Exposing a local service safely for demos
- Handling sessions, errors and real-world limits of AI replies

---

## 👤 Author

**Adarsh Kadam**: Game Developer · AI/ML Engineer · Data Analyst

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/adarsh-kadam)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Adarsh705875)
[![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:adarshkadam06@gmail.com)

<div align="center">

⭐ If you found this useful, consider starring the repo!

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:25D366,100:075E54&height=100&section=footer" width="100%" />

</div>
