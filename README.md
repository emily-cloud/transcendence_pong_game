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
git clone https://github.com/Zzzhenya/ft_transcnd.git
cd ft_transcnd/transcendence
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

Rene
Jason
Shenya
Irene
Emily

**Owner (Zzzhenya)**
- GitHub: [@Zzzhenya](https://github.com/Zzzhenya)

## 🙏 Acknowledgments

- 42 School for the project
- Babylon.js Community
- Fastify Framework
- Elastic Stack Team

---

**Note**: For production, self-signed certificates should be replaced with real SSL certificates, and all passwords/secrets should be managed securely.
