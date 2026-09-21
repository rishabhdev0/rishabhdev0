<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:161b22,100:58a6ff&height=200&section=header&text=Rishabh%20Pandey&fontSize=48&fontColor=58A6FF&animation=fadeIn&fontAlignY=35&desc=Software%20Engineer%20in%20the%20Making&descAlignY=55&descSize=18&descColor=8b949e"/>

<a href="https://github.com/rishabhdev0">
  <img src="https://komarev.com/ghpvc/?username=rishabhdev0&label=PROFILE+VIEWS&color=58a6ff&style=for-the-badge" />
</a>
<a href="https://github.com/rishabhdev0?tab=followers">
  <img src="https://img.shields.io/github/followers/rishabhdev0?style=for-the-badge&label=FOLLOWERS&color=58a6ff" />
</a>
<a href="https://codeforces.com/profile/rishabh_code">
  <img src="https://img.shields.io/badge/Codeforces-1F8ACB?style=for-the-badge&logo=codeforces&logoColor=white" />
</a>
<a href="https://leetcode.com/u/rishabh_code/">
  <img src="https://img.shields.io/badge/LeetCode-FFA116?style=for-the-badge&logo=leetcode&logoColor=black" />
</a>
<a href="https://www.hackerrank.com/profile/rishabh52003">
  <img src="https://img.shields.io/badge/HackerRank-2EC866?style=for-the-badge&logo=hackerrank&logoColor=white" />
</a>

<br><br>

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=22&duration=2800&pause=900&color=58A6FF&center=true&vCenter=true&width=800&lines=Building+a+low-latency+matching+engine+in+C%2B%2B;3.67ns%2Fop+memory+allocation+%E2%80%94+21x+faster+than+new%2Fdelete;Grinding+DSA+on+CF+%2F+LeetCode+%2F+HackerRank;Full-Stack+%7C+Systems+%7C+AI+Products;Turning+ideas+into+shipped%2C+benchmarked+software+%F0%9F%9A%80" />

</div>

---

## 🧠 About Me

```text
┌──────────────────────────────────────────────────────────────┐
│                                                                │
│  🎓 Final-year AIML student (AKTU)                            │
│  💼 Data Analyst Intern @ Bluestock Fintech                   │
│  💻 Full-Stack Developer — Next.js / TypeScript / tRPC        │
│  ⚙️  Systems Programmer — C++ low-latency engineering          │
│  🧩 Competitive Programmer — LeetCode Knight, 1800+ rating     │
│  🚀 Building production-style, benchmarked software            │
│                                                                │
└──────────────────────────────────────────────────────────────┘
```

I like taking an idea from **zero → architecture → implementation → benchmark → deployment**.
Most of my learning happens by building things, breaking them, measuring exactly how broken they were, and rebuilding them faster.

> **Current mission:** be the engineer who can both solve the algorithm *and* engineer the system it has to run inside of, under real load, with numbers to prove it.

---

## ⚡ What I'm Doing Right Now

<table>
<tr>
<td width="50%" valign="top">

### 🏗️ Building

**Nexora** — a full-stack BI & sales analytics platform

* Analytics engine — KPIs, trends, reports
* Interactive dashboards — charts & filters
* Auth, PostgreSQL, Redis caching
* Object storage (S3), Dockerized infra

</td>
<td width="50%" valign="top">

### 🧩 Improving

**Problem Solving — daily habit**

* Arrays & Strings · Binary Search
* Graphs · Dynamic Programming
* Greedy · Trees · Advanced patterns

**Platforms:** Codeforces · LeetCode · HackerRank

</td>
</tr>
</table>

---

## 🚀 Proof of Work

> I prefer showing what I built (and how fast it runs) over just listing what I know.

### ⚙️ `liquidity-engine` — Low-Latency Matching Engine — 🏆 Flagship Project

**A stock exchange matching engine in C++ — lock-free, memory-pooled, crash-safe.**

<p>
<img src="https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white"/>
<img src="https://img.shields.io/badge/CMake-064F8C?style=for-the-badge&logo=cmake&logoColor=white"/>
<img src="https://img.shields.io/badge/GoogleTest-4285F4?style=for-the-badge&logoColor=white"/>
<img src="https://img.shields.io/badge/WebSocket-2CA5E0?style=for-the-badge&logoColor=white"/>
<img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white"/>
<img src="https://img.shields.io/badge/Lock--Free_Concurrency-FF6F00?style=for-the-badge&logoColor=white"/>
</p>

```mermaid
flowchart LR
    A[WebSocket Gateway] --> B[["SPSC Ring Buffer"]]
    B --> C["MatchingEngine<br/>(memory-pooled)"]
    C --> D[("Append-only Journal")]
    C --> E[Live Dashboard]

    style A fill:#161b22,stroke:#58a6ff,color:#c9d1d9
    style B fill:#161b22,stroke:#f85149,color:#c9d1d9
    style C fill:#0d1117,stroke:#3fb950,color:#c9d1d9
    style D fill:#161b22,stroke:#a371f7,color:#c9d1d9
    style E fill:#0d1117,stroke:#d29922,color:#c9d1d9
```

| Metric | Result |
|---|---|
| Memory pool vs. raw `new`/`delete` | **~21x faster** (3.67ns vs 79.2ns/op) |
| Throughput | ~1.7–2.1M ops/sec single-threaded |
| Test coverage | 57 passing GoogleTest cases |

- Price-time priority order book with O(1) cancel, IOC/FOK, and live modify
- Lock-free SPSC ring buffer decouples ingest from matching (found & fixed a real stack-overflow bug here)
- Crash-safe journal replays on restart · live Next.js dashboard over WebSocket

🔗 **Repository:** [rishabhdev0/liquidity-engine](https://github.com/rishabhdev0/liquidity-engine)

---

### 🗳️ CipherVote — Blockchain Voting System

A security-focused voting platform exploring how to make digital voting **verifiable without exposing individual ballots**.

<p>
<img src="https://img.shields.io/badge/Blockchain-3C3C3D?style=for-the-badge&logo=ethereum&logoColor=white"/>
<img src="https://img.shields.io/badge/Cryptography-4B0082?style=for-the-badge&logoColor=white"/>
<img src="https://img.shields.io/badge/Zero--Knowledge_Proofs-6A0DAD?style=for-the-badge&logoColor=white"/>
<img src="https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black"/>
<img src="https://img.shields.io/badge/Smart_Contracts-3C3C3D?style=for-the-badge&logo=solidity&logoColor=white"/>
</p>

* Smart-contract-backed ballot casting and tallying
* Zero-knowledge proof design for ballot privacy vs. verifiability
* React frontend for wallet-based voting

🔗 **Repository:** [rishabhdev0/CipherVote](https://github.com/rishabhdev0/CipherVote)

---

### 📊 Nexora — Business Intelligence & Sales Analytics

**A full-stack analytics platform designed around real-world business workflows.**

<p>
<img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white"/>
<img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white"/>
<img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white"/>
<img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white"/>
<img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
<img src="https://img.shields.io/badge/S3-569A31?style=for-the-badge&logo=amazons3&logoColor=white"/>
<img src="https://img.shields.io/badge/Auth-FFB300?style=for-the-badge&logo=auth0&logoColor=white"/>
<img src="https://img.shields.io/badge/Data_Viz-00BCD4?style=for-the-badge&logoColor=white"/>
</p>

```mermaid
flowchart LR
    A[Data Sources] --> B[API Layer]
    B --> C[("Redis Cache")]
    B --> D[("PostgreSQL")]
    C --> E["Analytics Engine<br/>KPIs · Trends · Reports"]
    D --> E
    E --> F["Interactive Dashboard<br/>Charts · Filters · KPIs"]

    style A fill:#161b22,stroke:#58a6ff,color:#c9d1d9
    style B fill:#161b22,stroke:#58a6ff,color:#c9d1d9
    style C fill:#161b22,stroke:#f85149,color:#c9d1d9
    style D fill:#161b22,stroke:#58a6ff,color:#c9d1d9
    style E fill:#0d1117,stroke:#3fb950,color:#c9d1d9
    style F fill:#0d1117,stroke:#a371f7,color:#c9d1d9
```

🔗 **Repository:** [View Project](https://github.com/rishabhdev0)

---

### 🎙️ Sonicra — AI Voice Generation Platform

A voice-generation SaaS focused on a clean, production-style user experience.

<p>
<img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white"/>
<img src="https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black"/>
<img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white"/>
<img src="https://img.shields.io/badge/Chatterbox_TTS-FF4081?style=for-the-badge&logoColor=white"/>
<img src="https://img.shields.io/badge/Prisma-2D3748?style=for-the-badge&logo=prisma&logoColor=white"/>
<img src="https://img.shields.io/badge/Clerk-6C47FF?style=for-the-badge&logo=clerk&logoColor=white"/>
<img src="https://img.shields.io/badge/Cloud_Storage-4CAF50?style=for-the-badge&logoColor=white"/>
</p>

* AI voice generation & voice cloning
* Async generation workflows, SaaS billing architecture

🔗 **Repository:** [rishabhdev0/Sonicra](https://github.com/rishabhdev0/Sonicra)

---

## 📈 Engineering Activity

<div align="center">
<img src="https://ghchart.rshah.org/58a6ff/rishabhdev0" width="95%"/>
</div>

<br>

<div align="center">
<img src="https://streak-stats.demolab.com?user=rishabhdev0&theme=github-dark-blue&hide_border=true" width="70%"/>
</div>

---

## 🧮 Competitive Programming

<div align="center">

<img src="https://leetcard.jacoblin.cool/rishabh_code?theme=dark&font=baloo&ext=heatmap" width="700"/>

<br><br>

<img src="https://codeforces-readme-stats.vercel.app/api/card?username=rishabh_code" width="500"/>

</div>

| Platform | Profile | Focus |
|---|---|---|
| 🔵 **Codeforces** | [rishabh_code](https://codeforces.com/profile/rishabh_code) | Competitive Programming · Rated Contests |
| 🟠 **LeetCode** | [rishabh_code](https://leetcode.com/u/rishabh_code/) | DSA · Interview Problems · Patterns (Knight, 1800+) |
| 🟢 **HackerRank** | [rishabh52003](https://www.hackerrank.com/profile/rishabh52003) | Algorithms · SQL · Problem Solving |

### 🧠 Patterns I'm Grinding

```text
Arrays          ████████████████████
Binary Search   █████████████████
Graphs          ███████████████
DP              █████████████
Greedy          ████████████
Trees           ███████████
Advanced DSA    █████████
```

---

## 🛠️ Tech Stack

### Languages
<p><img src="https://skillicons.dev/icons?i=cpp,c,java,python,js,ts" /></p>

### Frontend
<p><img src="https://skillicons.dev/icons?i=react,nextjs,html,css,tailwind,vite" /></p>

### Backend
<p><img src="https://skillicons.dev/icons?i=nodejs,express,spring,graphql" /></p>

### Databases & Infrastructure
<p><img src="https://skillicons.dev/icons?i=postgres,mongodb,redis,docker,aws,vercel" /></p>

### Tools
<p><img src="https://skillicons.dev/icons?i=git,github,gitlab,postman,figma,npm" /></p>

---

## 🏆 GitHub Achievements

<div align="center">

<img src="https://github.com/KaweMaximo/github-profile-achievements/raw/main/images/pull-shark-default.png" width="90" title="Pull Shark — 2+ pull requests merged"/>
<img src="https://github.com/KaweMaximo/github-profile-achievements/raw/main/images/yolo-default.png" width="90" title="YOLO — merged a PR without code review"/>

**Pull Shark** · **YOLO**

</div>

---

## 🌱 Currently Learning

```mermaid
mindmap
  root((Rishabh))
    Systems Engineering
      Lock-Free Concurrency
      Memory Pools
      Crash-Safe Journaling
      Low-Latency C++
    CS Fundamentals
      Operating Systems
      DBMS
      Computer Networks
      OOP
    DSA
      Graphs
      Dynamic Programming
      Trees
      Greedy
      Binary Search
    Full Stack
      tRPC end-to-end types
      Prisma + PostgreSQL
      Server Components
      WebSockets / real-time
      Auth & session design
    Infrastructure
      Docker
      Cloud
      CI/CD
      Object Storage
```

---

## 🔥 My Developer Loop

```text
   IDEA 💡 → DESIGN 🎨 → BUILD 🛠️ → BREAK 💥 → DEBUG 🐛 → BENCHMARK 📊 → SHIP 🚀 → REPEAT
```

---

## 📌 Featured Projects

| Repo | Description |
|---|---|
| ⚙️ **[liquidity-engine](https://github.com/rishabhdev0/liquidity-engine)** | Low-latency C++ matching engine — lock-free, memory-pooled, crash-safe |
| 🗳️ **[CipherVote](https://github.com/rishabhdev0/CipherVote)** | Blockchain voting system with zero-knowledge ballot privacy |
| 🎙️ **[Sonicra](https://github.com/rishabhdev0/Sonicra)** | AI voice generation SaaS with cloning & async workflows |

---

## 🤝 Let's Connect

<div align="center">

<a href="https://linkedin.com/in/rishabh-pandey-254a08285/">
<img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/>
</a>
<a href="mailto:rishabh52003@gmail.com">
<img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white"/>
</a>
<a href="https://x.com/Rishabh58750540">
<img src="https://img.shields.io/badge/X-000000?style=for-the-badge&logo=x&logoColor=white"/>
</a>
<a href="https://github.com/rishabhdev0">
<img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white"/>
</a>

</div>

---

<div align="center">

### `Build → Break → Benchmark → Ship → Repeat`

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:161b22,100:58a6ff&height=120&section=footer"/>

</div>
