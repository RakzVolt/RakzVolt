<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0f172a,100:1e293b&height=200&section=header&text=RakzVolt&fontSize=52&fontColor=f8fafc&fontAlignY=42&desc=Backend%20%7C%20WhatsApp%20Bot%20%7C%20API&descAlignY=68&descSize=14&descColor=94a3b8" />
  
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&size=18&duration=3000&pause=800&color=38bdf8&center=true&vCenter=true&width=560&lines=Backend+Engineer;Go+%7C+Node.js+%7C+WhatsApp+Bots;Building+systems+that+don't+break" />
</div>

<br/>

**Hey.**  
I build backend systems and WhatsApp bots that stay simple, fast, and actually usable.  
Most of my time goes into clean APIs, solid data layers, and features that people actually use — not just demos.

---

### Tech Stack

<div align="center">

**Languages & Runtime**  
![Go](https://img.shields.io/badge/Go-00ADD8?style=for-the-badge&logo=go&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)

**Backend & API**  
![Prabogo Go](https://img.shields.io/badge/Prabogo_Go-22c55e?style=for-the-badge)
![Express](https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white)
![Baileys](https://img.shields.io/badge/Baileys-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)
![ToolCoin](https://img.shields.io/badge/ToolCoin-f59e0b?style=for-the-badge)

**Database**  
![SawitDB](https://img.shields.io/badge/SawitDB-f59e0b?style=for-the-badge)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)

**Frontend / UI**  
![JokoUI](https://img.shields.io/badge/JokoUI-0ea5e9?style=for-the-badge)
![Luna](https://img.shields.io/badge/Luna-8b5cf6?style=for-the-badge)
![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)

**Tools & Others**  
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![FFmpeg](https://img.shields.io/badge/FFmpeg-007808?style=for-the-badge&logo=ffmpeg&logoColor=white)

</div>

---

### What I build

- **WhatsApp Bots** – full command runtime, menu system, rich messages, buttons, stickers, welcome cards
- **Marketplace features** – catalog, pack downloads, preview cards connected to ToolCoin backend
- **AI chat** – conversational replies inside WhatsApp
- **Media tools** – sticker creation, quote images, group media helpers
- **Music & Spotify** – search + rich player cards
- **Mini games** – light interactive features for groups
- **Clean APIs** – Go services that stay predictable and easy to maintain

---

### Bot Architecture

Everything routes through one command runtime. Features stay modular so new ones can be added without breaking the core.

```mermaid
flowchart TD

subgraph group_runtime["Bot Runtime"]
  node_dispatcher["Command runtime<br/>[index.js]"]
  node_config["Bot configuration<br/>[config.js]"]
end

subgraph group_market["Marketplace"]
  node_catalog["Marketplace API<br/>[toolcoin.js]"]
  node_menu["Command menu<br/>[menu.js]"]
end

subgraph group_features["Bot Features"]
  node_ai["AI chat<br/>[ai.js]"]
  node_play["Music search<br/>[play.js]"]
  node_spotify["Spotify cards<br/>[spotify.js]"]
  node_group_tools["Group media tools<br/>[groupTools.js]"]
  node_welcome["Welcome cards<br/>[welcome.js]"]
  node_sticker["Sticker creation<br/>[sticker.js]"]
  node_iqc["Quote images<br/>[iqc.js]"]
  node_games["Games and fun<br/>[minigames.js]"]
end

subgraph group_presentation["WhatsApp Presentation"]
  node_preview["Marketplace previews<br/>[previewAd.js]"]
  node_wa_ui["WhatsApp UI helpers<br/>[baileysUi.js]"]
  node_buttons["Button formatting<br/>[buttons.js]"]
  node_rich["Rich message rendering<br/>[rich.js]"]
end

node_user(("WhatsApp user"))
node_whatsapp(("WhatsApp service"))
node_toolcoin_service(("ToolCoin backend"))
node_luna(("Luna UI library"))

node_user -->|"sends commands"| node_whatsapp
node_whatsapp -->|"delivers messages"| node_dispatcher
node_dispatcher -->|"loads settings"| node_config
node_dispatcher -->|"routes menu"| node_menu
node_dispatcher -->|"sends replies"| node_wa_ui
node_dispatcher -->|"formats buttons"| node_buttons
node_menu -->|"sends menus"| node_wa_ui
node_menu -->|"builds previews"| node_preview
node_dispatcher -->|"builds previews"| node_preview
node_preview -->|"reads settings"| node_config
node_dispatcher -->|"marketplace commands"| node_catalog
node_catalog -->|"requests catalog data"| node_toolcoin_service
node_catalog -->|"downloads packs"| node_toolcoin_service
node_dispatcher -->|"creates stickers"| node_sticker
node_dispatcher -->|"configures welcomes"| node_welcome
node_welcome -->|"persists settings"| node_config
node_dispatcher -->|"renders quote images"| node_iqc
node_dispatcher -.->|"injects UI library"| node_luna
node_dispatcher -->|"sends responses"| node_whatsapp
node_wa_ui -->|"sends UI messages"| node_whatsapp
node_spotify -->|"renders player cards"| node_rich
node_rich -->|"sends rich messages"| node_whatsapp

classDef toneBlue fill:#dbeafe,stroke:#2563eb,stroke-width:1.5px,color:#172554
classDef toneAmber fill:#fef3c7,stroke:#d97706,stroke-width:1.5px,color:#78350f
classDef toneMint fill:#dcfce7,stroke:#16a34a,stroke-width:1.5px,color:#14532d
classDef toneRose fill:#ffe4e6,stroke:#e11d48,stroke-width:1.5px,color:#881337
classDef toneIndigo fill:#e0e7ff,stroke:#4f46e5,stroke-width:1.5px,color:#312e81

class node_dispatcher,node_config,node_user,node_luna toneBlue
class node_catalog,node_menu toneAmber
class node_ai,node_play,node_spotify,node_group_tools,node_welcome,node_sticker,node_iqc,node_games toneMint
class node_preview,node_wa_ui,node_buttons,node_rich toneRose
class node_whatsapp,node_toolcoin_service toneIndigo
