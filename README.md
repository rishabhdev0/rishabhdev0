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

**`liquidity-engine`** — a low-latency stock exchange matching engine in C++

* Lock-free SPSC ring buffer for ingest
* Custom memory pool allocator (~21x faster than `new`/`delete`)
* Crash-safe append-only journal with replay-on-restart
* IOC / FOK / modify-in-place order semantics
* Live WebSocket dashboard in Next.js

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

**A from-scratch stock exchange matching engine in C++, built in phases and benchmarked at every stage — not a toy order book.**

`C++` `CMake` `GoogleTest` `Google Benchmark` `WebSocket` `Next.js` `Lock-Free Concurrency`

```text
     Ingest Thread                Matching Thread
   ┌────────────────┐          ┌────────────────────┐
   │  Order Gateway  │  SPSC   │  MatchingEngine     │
   │  (WebSocket)    │ ──────► │  ┌───────────────┐  │
   └────────────────┘ Ring Buf │  │ OrderBook      │  │
                                │  │ (price-time    │  │
                                │  │  priority)     │  │
                                │  └───────┬───────┘  │
                                │          │           │
                                │   MemoryPool<Order>  │
                                │   (3.67ns/op alloc)  │
                                └──────────┬───────────┘
                                           │
                              ┌────────────▼────────────┐
                              │  Append-Only Journal     │
                              │  (crash-safe, replayed   │
                              │   on restart)            │
                              └────────────┬────────────┘
                                           │
                              ┌────────────▼────────────┐
                              │  Live Dashboard (Next.js)│
                              │  Price/Depth charts,     │
                              │  order entry, trade tape │
                              └──────────────────────────┘
```

**Real, measured numbers — not marketing copy:**

| Metric | Result |
|---|---|
| Order allocation (raw `new`/`delete`) | ~79.2 ns/op |
| Order allocation (custom memory pool) | **~3.67 ns/op (~21x faster)** |
| 10k-order batch churn, pooled vs. raw | **~28.9x faster** |
| Single-threaded rest + fill | ~564 ns / ~1.7–2.1M ops/sec |
| Concurrent (SPSC-decoupled) producer path | ~1674 ns/op — a deliberate decoupling cost, not a raw-speed win: the ingest thread never blocks on matching |
| Test suite | 57 passing GoogleTest cases across order book, engine, concurrency, journal replay, and order-type semantics |

**Engineering it actually took to get here:**
- Built the order book with **price-time priority**, O(1) cancel via index map, and full IOC / FOK / modify-in-place semantics that mirror real exchange behavior (a price or size-increase change loses time priority; a size decrease keeps it)
- Wrote a custom **memory pool** to kill `malloc` pauses on the hot path, then benchmarked it against the naive version to prove the win
- Built a **lock-free SPSC ring buffer** to decouple network ingest from matching, and found + fixed a real stack-overflow bug caused by storing the buffer inline instead of on the heap
- Added a **crash-safe append-only journal** that replays on restart to rebuild pre-crash state
- Shipped a live **Next.js dashboard** over a WebSocket bridge — price chart, depth chart, order entry, live order cancel, and round-trip latency display

🔗 **Repository:** [rishabhdev0/liquidity-engine](https://github.com/rishabhdev0/liquidity-engine)

---

### 🗳️ CipherVote — Blockchain Voting System

A security-focused voting platform exploring how to make digital voting **verifiable without exposing individual ballots**.

`Blockchain` `Cryptography` `Zero-Knowledge Proofs` `React` `Smart Contracts`

* Smart-contract-backed ballot casting and tallying
* Zero-knowledge proof design for ballot privacy vs. verifiability
* React frontend for wallet-based voting

🔗 **Repository:** [rishabhdev0/CipherVote](https://github.com/rishabhdev0/CipherVote)

---

### 📊 Nexora — Business Intelligence & Sales Analytics

**A full-stack analytics platform designed around real-world business workflows.**

`Next.js` `TypeScript` `PostgreSQL` `Redis` `Docker` `S3` `Authentication` `Data Visualization`

```text
Data Sources → API Layer → Redis Cache → PostgreSQL
                                 │
                                 ▼
                    Analytics Engine (KPIs · Trends · Reports)
                                 │
                                 ▼
                 Interactive Dashboard (Charts · Filters · KPIs)
```

🔗 **Repository:** [View Project](https://github.com/rishabhdev0)

---

### 🎙️ Sonicra — AI Voice Generation Platform

A voice-generation SaaS focused on a clean, production-style user experience.

`Next.js` `React` `TypeScript` `Chatterbox TTS` `Prisma` `Clerk` `Cloud Storage`

* AI voice generation & voice cloning
* Async generation workflows, SaaS billing architecture

🔗 **Repository:** [View Project](https://github.com/rishabhdev0)

---

## 📈 Engineering Activity

<div align="center">
<img src="https://github-readme-activity-graph.vercel.app/graph?username=rishabhdev0&bg_color=0d1117&color=58a6ff&line=58a6ff&point=ffffff&area=true&hide_border=true" width="95%"/>
</div>

<br>

<div align="center">
<img src="https://github-readme-stats.vercel.app/api?username=rishabhdev0&show_icons=true&hide_border=true&theme=github_dark&include_all_commits=true&count_private=true" height="180"/>
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=rishabhdev0&layout=compact&hide_border=true&theme=github_dark&langs_count=8" height="180"/>
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
<img src="https://github-profile-trophy.vercel.app/?username=rishabhdev0&theme=darkhub&no-frame=true&no-bg=true&margin-w=8&column=6" width="90%"/>
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
    DSA
      Graphs
      Dynamic Programming
      Trees
      Greedy
      Binary Search
    Full Stack
      React
      Next.js
      Node.js
      Spring Boot
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

<div align="center">
<a href="https://github.com/rishabhdev0/liquidity-engine">
<img src="https://github-readme-stats.vercel.app/api/pin/?username=rishabhdev0&repo=liquidity-engine&theme=github_dark&hide_border=true" />
</a>
<a href="https://github.com/rishabhdev0/CipherVote">
<img src="https://github-readme-stats.vercel.app/api/pin/?username=rishabhdev0&repo=CipherVote&theme=github_dark&hide_border=true" />
</a>
</div>

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
