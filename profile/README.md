# 🏗️ DEMC Infrastructure Documentation

**Project Name**: DEMC (Dwi Emas Minecraft)  
**Maintained by**: Hitbox Games  
**Type**: Multi-System Game Infrastructure  
**Purpose**: A secure, customized Minecraft experience with account management, anti-cheat protections, and a connected community.

---

## 🌐 System Overview

The DEMC ecosystem includes the following components:

1. 🔐 **HTBX-Auth** – Central authentication and HWID verification system  
2. 👤 **PlayerInfo API** – Centralized API for player metadata and integration  
3. 🖥️ **Minecraft Server** – Secure and modded server with plugin integrations  
4. 🧩 **Client Mod** – Enforces authentication, anti-cheat, and token sync  
5. 🌐 **DEMC Website** – User profile customization and account portal  
6. 🤖 **Discord Bot & Community** – Account linking, player commands, and live alerts

---

## 🧱 Architecture Diagram

```mermaid
graph TD
  A[Client Mod] -->|Login + HWID| B[HTBX-Auth Server]
  A -->|Connect| C[Minecraft Server]
  C -->|Fetch UUID & Stats| D[PlayerInfo API]
  B -->|Issue Auth Token| A
  B -->|Validate HWID| E[Native Binary]
  F[Website] -->|Token Login| B
  G[Discord Bot] -->|Link/Query| D
````

---

## 🔐 1. HTBX-Auth

**Technology**: Node.js + SQLite3
**Purpose**: Secure authentication and HWID binding

* Password hashing with `bcrypt`
* HMAC signature validation
* Local SQLite3 user/session store
* Native binary used for fingerprinting
* REST + WebSocket endpoints

🔗 [HTBX-Auth GitHub Repo](https://github.com/HitboxDevelopment/htbx-auth)

---

## 📊 2. PlayerInfo API

**Technology**: Node.js / Express
**Purpose**: Stores and exposes player metadata

* Tracks join date, stats, roles, etc.
* Linked to Minecraft UUID and Discord ID
* Token-based access
* Supports web and bot queries

---

## 🎮 3. Minecraft Server

**Base**: Paper / Forge Hybrid
**Features**:

* Auth integration using HTBX-Auth token
* Anti-cheat hooks via client mod
* Player sync to PlayerInfo API
* Custom gameplay plugins

---

## 🧩 4. Client Mod

**Built With**: Forge/Fabric
**Purpose**: Local login enforcement and integrity check

* Runs native executable for HWID
* Sends auth requests to HTBX-Auth
* Ensures player token matches session
* Sends behavior telemetry to backend

---

## 🌐 5. DEMC Website

**Tech Stack**: React + REST API
**Purpose**: Public user interface and profile portal

* Login via HTBX-Auth token
* View and update player profile
* Link Discord account
* Customize settings and skins (future)
* Admin dashboard for moderation (future)

---

## 🤖 6. Discord Bot & Community

**Bot Platform**: Discord.js
**Community Server**: [DEMC Discord Invite]() *(Insert Invite)*

**Features**:

* Account linking via Discord ID
* `/profile`, `/stats`, `/verify` commands
* Live alerts (logins, bans, events)
* Sync roles with in-game data
* Moderation + logging integration (optional)

---

## 🧠 Roadmap

* [ ] Profile customization (skins, cosmetics)
* [ ] Discord role sync to in-game ranks
* [ ] Player reputation system
* [ ] Admin moderation tools (web + Discord)

---

## 👥 Contributors

* Hitbox Games Core Team
* DEMC Moderation Team
* Dwi Emas IT Collaborators

---

## 📄 License

Project components are semi-private; some systems are open-sourced under MIT License. See individual repositories for license terms.

```
