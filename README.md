# transcendence_pong_game 🏓

> A comprehensive multiplayer Pong platform with microservices architecture, 3D graphics, and real-time features

![Status](https://img.shields.io/badge/Status-Production_Ready-success)
![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?logo=docker)
![TypeScript](https://img.shields.io/badge/TypeScript-Frontend-3178C6?logo=typescript)
![Node.js](https://img.shields.io/badge/Node.js-Backend-339933?logo=node.js)

## 📖 Overview

**transcendence** is a modern web application for multiplayer Pong featuring a complete microservices architecture. The project combines 3D graphics rendering with Babylon.js, real-time communication via WebSockets, and a comprehensive monitoring system.

### ✨ Key Features

- 🎮 **3D Pong Gameplay** with Babylon.js rendering engine
- 👥 **Multiplayer Modes**: Local, Remote, and Tournaments
- 🏆 **Tournament System** with automatic bracket generation
- 🔐 **Secure Authentication** with JWT and optional 2FA
- 👤 **User Management** with profiles, avatars, and friends system
- 📊 **Monitoring & Logging** with complete ELK stack
- 🔒 **Security Features**: XSS protection, input validation, SQL injection prevention

## 🏗️ Architecture

### Microservices Structure

```
┌─────────────┐
│   Nginx     │ ← Reverse Proxy & SSL Termination
│   (Port 8443)│
└──────┬──────┘
       │
┌──────▼──────┐
│   Gateway   │ ← API Gateway, Auth Middleware, WebSocket Routing
│   (Port 3000)│
└──────┬──────┘
       │
       ├─────────────┬─────────────┬─────────────┬─────────────┐
       │             │             │             │             │
┌──────▼──────┐ ┌───▼───────┐ ┌───▼────────┐ ┌──▼──────────┐ ┌──▼──────────┐
│User Service │ │Game Service│ │Tournament  │ │Log Service  │ │Database     │
│  (Port 3001)│ │(Port 3002) │ │Service     │ │(Port 3003)  │ │Service      │
│             │ │            │ │(Port 3005) │ │             │ │(Port 3006)  │
│• JWT Auth   │ │• Pong Logic│ │• Brackets  │ │• ELK Stack  │ │• SQLite     │
│• Profiles   │ │• WebSocket │ │• Matches   │ │• Monitoring │ │• Shared DB  │
│• Friends    │ │• Remote    │ │• Scoring   │ │             │ │             │
└─────────────┘ └────────────┘ └────────────┘ └─────────────┘ └─────────────┘
```

### Tech Stack

#### Frontend
- **Framework**: Vanilla TypeScript + Vite
- **3D Engine**: Babylon.js
- **Styling**: Tailwind CSS
- **Architecture**: SPA with client-side routing

#### Backend Services
- **Gateway**: Fastify (TypeScript) - API routing & WebSocket management
- **User Service**: Express (Node.js) - Authentication & user management
- **Game Service**: Express (Node.js) - Game logic & real-time communication
- **Tournament Service**: Express (Node.js) - Tournament management
- **Log Service**: Express (Node.js) - Centralized logging
- **Database Service**: Express (Node.js) - Database operations

#### Infrastructure
- **Container**: Docker & Docker Compose
- **Reverse Proxy**: Nginx with SSL/TLS
- **Database**: SQLite (shared volume)
- **Monitoring**: Elasticsearch, Logstash, Kibana (ELK Stack)
- **Authentication**: JWT with HttpOnly cookies

## 🚀 Quick Start

### Prerequisites

- Docker & Docker Compose
- Git
- 4GB RAM (minimum), 8GB RAM (recommended with monitoring)
- Ports 8443 (HTTPS) and 8080 (HTTP) available

### Installation

1. **Clone the repository**
```bash
https://github.com/emily-cloud/transcendence_pong_game.git
cd transcendence_pong_game/transcendence
```

2. **Configure environment variables**
```bash
-> create and fill .env file
```

3. **Start services with monitoring**

**Option A: Basic setup (without monitoring)**
```bash
cd transcendence ; make start 
```

**Option B: Full setup (with ELK stack)**
```bash
cd transcendence ; make
```

5. **Access the application**
- Frontend: https://localhost:8443
- Kibana (monitoring only): http://localhost:5601
- SQLite Admin: http://localhost:8080

### Getting Started

1. Register a new account or use the test account
2. Create your profile and upload an avatar
3. Start a local game or join a tournament
4. Invite friends for remote matches

### Getting Started

1. **Register a new account or use the test account**  
   After accessing the platform, create a new player profile or log in using one of the provided test accounts.

2. **Set up your profile and upload an avatar**  
   Personalize your player identity with an avatar and profile details—these will appear in matches, friend lists, and tournaments.

3. **Start a local game or join a tournament**  
   You can warm up in a local match or immediately join an online tournament where brackets are generated automatically.

4. **Invite friends for remote matches**  
   Play against others in real time via WebSockets, challenge friends, or join public games.

---

### 🎮 Gameplay Preview

Below are a few example screenshots showing what the user will experience when playing:

🏠 Lobby

The lobby is the main landing area where users can navigate to game modes, view friends, manage profiles, or join active matches.

<p align="center">
  <img src="https://raw.githubusercontent.com/emily-cloud/transcendence_pong_game/main/game_screenshot/Screenshot%202025-12-31%20at%2014.30.49.png" 
       alt="Main Gameplay Screen" width="75%">
</p>

👤 User Profile

Each player has a customizable profile with avatar upload, statistics, match history, and friend management.

<p align="center">
  <img src="https://raw.githubusercontent.com/emily-cloud/transcendence_pong_game/main/game_screenshot/Screenshot%202025-12-31%20at%2014.31.50.png" 
       alt="Lobby or Pre-Match" width="75%">
</p>

🌐 Remote Game Lobby

Players can join remote matches, invite friends, or wait for opponents in real time.

<p align="center">
  <img src="https://raw.githubusercontent.com/emily-cloud/transcendence_pong_game/main/game_screenshot/Screenshot%202025-12-31%20at%2014.32.28.png" 
       alt="3D Arena" width="75%">
</p>

🏆 Tournament Lobby  
The Tournament Lobby allows players to join or create tournaments, view brackets, and follow match progress in real time.

<p align="center">
  <img src="https://raw.githubusercontent.com/emily-cloud/transcendence_pong_game/main/game_screenshot/Screenshot%202025-12-31%20at%2014.36.09.png" 
       alt="Tournament Lobby" width="75%">
</p>


**➡️ 3D Arena & Visual Effects**  
The Babylon.js engine provides smooth lighting, shadows, and camera transitions during gameplay.

<p align="center">
  <img src="https://raw.githubusercontent.com/emily-cloud/transcendence_pong_game/main/game_screenshot/Screenshot%202025-12-31%20at%2014.32.16.png" 
       alt="3D Arena Visual 2" width="75%">
</p>

## 🎓 42 School Project

This project fulfills all requirements of the ft_transcendence project:

## transcendence - Module Overview

### Major Modules

| Major | Content |
|-------|---------|
| ✅ Backend framework | Node.js (Fastify) |
| ✅ Gameplay | Remote players |
| ✅ Devops | Log management (ELK) | 
| ✅ Devops | Designing backend as Microservices |
| ✅ Server-Side Pong | + API |
| ✅ Graphics | 3D (Babylon.js) | 
| ✅ User Management | Standard user management, authentication, users across tournaments |

**TOTAL: 7 Points**

### Minor Modules

| Minor | Content |
|-------|---------|
| ✅ Web | Frontend framework Tailwind CSS |
| ✅ Web | Database (SQLite) |

**TOTAL: 1 Point**

---
**Total Score: 8 Points**

## 📄 License

This project was developed as part of the 42 School curriculum.

## 👥 Author

Huayun Ai
René Kost
Taekeun Kwak
Shenya De Silva
Irene Rivero Casal

## 🙏 Acknowledgments

- 42 School project
- Babylon.js Community
- Fastify Framework
- Elastic Stack Team

---

**Note**: For production, self-signed certificates should be replaced with real SSL certificates, and all passwords/secrets should be managed securely.
