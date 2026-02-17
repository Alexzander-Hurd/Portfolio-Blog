---
title: Contacts App
description: A ASP.NET minimal API backend consumed by a Sveltekit frontend and optional Wails wrapper for desktop installation.
pubDate: Feb 9 2026
heroImage: ../../../public/images/contacts-hero.png
---
# Project Links: <a href="https://github.com/Alexzander-Hurd/Contacts-App-Backend"><img src="https://img.shields.io/badge/Backend-%23121011.svg?logo=github&logoColor=white"/></a> <a href="https://github.com/Alexzander-Hurd/Contacts-App-Clients"><img src="https://img.shields.io/badge/Clients-%23121011.svg?logo=github&logoColor=white"/></a>

**Quick Stats:**

- Tech stack - ASP.NET Core 8, Minimal API, Sveltekit/Vue, Wails (optional), Tailwind  
- CI/CD - N/A to be added after hosting setup  
- Status - Alpha (functional but not hosted)  
- Licensing - MIT

# Overview

The **Contacts App** is a full-stack address book solution designed to demonstrate a "Write Once, Run Everywhere" architecture. It features a robust RESTful API backend that serves data to **interchangeable frontend clients**. The project features **two distinct frontend implementations (Svelte 5 and Vue 3)**, both capable of running as a standard web application (SPA via Nginx) or as a native desktop application (Windows/Linux via Wails). The application focuses on a modern user experience with reactive UI updates, secure authentication, and seamless data synchronization between the web and desktop contexts.

# Purpose

This project serves as a comprehensive portfolio piece to demonstrate mastery of modern web and desktop technologies: 
1. **Modern State Management:** Utilizing **Svelte 5 Runes** (`$state`, `$derived`, `$effect`) for fine-grained reactivity. 
2. **Minimal API Architecture:** Showcasing clean, lightweight C# endpoints without the overhead of MVC controllers. 
3. **Hybrid Deployment:** Proving the ability to package a single web codebase into a native desktop executable using **Wails**. 
4. **Type Safety:** Implementing end-to-end type safety using OpenAPI schemas generated from the C# backend and consumed by the TypeScript frontend.
5. **Framework Agility:** Demonstrating the ability to port complex logic and state management patterns between **Svelte Runes** and **Vue Composition API** while maintaining feature parity.

# Features

### Core Functionality
- **Authentication & Security:** JWT-based stateless authentication with Role-Based Access Control (Admin vs. Standard User).
- **Contact Management:** Full CRUD operations for contacts with real-time search, filtering, and alphabetical grouping.
- **Groups System:** Create custom groups (e.g., "Marketing", "Engineering") and manage membership via specific endpoints.
- **Favourites:** Quick access to frequently used contacts via a dedicated favourites list.

### User Experience
- **Profile Management:** Self-service profile editing (Name, Email) and security settings (Change Password).
- **"Danger Zone":** GDPR-compliant account deletion (Cascade deletes user data).
- **Reactive UI:** Instant feedback via Toast notifications and Optimistic UI updates using local stores.
- **Responsive Design:** Mobile-first layout using Tailwind CSS, functioning seamlessly on both desktop and mobile browsers.

### Administration
- **Admin Dashboard:** Restricted area for Admins to view all registered users.
- **User Management:** Ability to force-reset user passwords or ban/delete accounts.
- **Role Detection:** Frontend dynamically adapts the UI based on the `IsAdmin` flag in the user session.

# Installation & Usage

### 1. Backend (ASP.NET Core)

```bash
cd Contacts-App-Backend
# Update appsettings.json with your ConnectionString
dotnet ef database update
Auth__SecretKey="your JWT signing secret" dotnet run
# API will launch at http://localhost:5169
```

### 2. Frontend (Web Mode)
#### a) Svelte
```bash
cd Contacts-App-Clients/Svelte 
npm install 
npm run dev OR npm run build
```

#### b) Vue
```bash
cd Contacts-App-Clients/Vue 
npm install 
npm run dev OR npm run build
```

### 3. Desktop App (Wails)

```bash
cd Contacts-App-Clients/Wails
# Build the Frontend app and wrap it in WebView2
./build-script.sh # Linux/Mac only 
# Windows: Manually copy Svelte `build` or Vue `dist` contents to `Wails/frontend/dist` before running `wails build`
# Output: ./bin/ContactsApp.exe
```
# Technical Details

### Architecture
- **Backend:** ASP.NET Core 8 Minimal API using `MapGroup` for organized routing (`/auth`, `/contacts`, `/groups`).
- **Data Access:** Entity Framework Core with a distinct separation between Database Entities and DTOs (Data Transfer Objects).
- **API Client:** `openapi-fetch` wrapper with a custom "Fetch Factory" to inject Auth headers and handle Content-Type logic automatically.
### Frontend Application (Polymorphic)
#### Svelte 5
- **Runes:** Heavy usage of `$state` for local component state and `$derived` for computed lists (e.g., filtering contacts by search query).
- **Global Store:** A `user.svelte.ts` class-based store, utilising Runes for reactivity, that encapsulates the User Session (`Contact` + `IsAdmin`) and handles API synchronization.
- **Components:** Reusable UI components including `ContactCard`, `Sidebar`, `Toast`, and `Modal` (using Svelte Portals).
#### Vue 3
- **Composition API:** Mirrors the Svelte Runes logic using `ref` for reactive state and `computed` for derived lists (e.g., filtering contacts), offering a direct architectural comparison between the two frameworks.
- **State Management:** Utilizes **Pinia** for global stores, featuring a "Shared Mutable State" pattern in the Auth layer to prevent circular dependencies between the API client and the Router.
- **Teleport:** Implements modal logic using Vue's `<Teleport>` to match the DOM placement strategy of Svelte's Portals.
### Wails Integration
- **Shared Build Target:** Sveltekit and Vue build to their `build` and `dist` directories respectively
- **Dynamic Frontend Switching:** The `build_script.sh` bash script allows you to select which frontend to import into the wrapper. This dynamically discovers other folders that share the same parent directory as `Wails/`
- **Embed Logic:** Go binary embeds the `frontend/` folder using `//go:embed`.
- **Environment Switching:** Vite configuration detects the build mode (`--mode desktop`) to swap the API URL from `localhost` to the production remote server.
# Roadmap
- [x] **Core CRUD & Auth** (Completed)
- [x] **Groups & Favorites** (Completed)
- [x] **Admin Dashboard** (Completed)
- [x] **Desktop Cross-Compilation** (Windows builds via Linux/Taskfile)
- [ ] **Polymorphic Frontend:** Re-implement the frontend UI in other frameworks to demonstrate framework agility, using the same Wails host.
	- [x] **Vue** 
	- [ ] **React**
- [ ] **Dockerization:** Containerize the API and Nginx frontend for cloud deployment.
- [ ] **CI/CD:** Github Actions pipeline to auto-build the Windows .exe on release.
# License

- Backend: MIT ([LICENSE](https://github.com/Alexzander-Hurd/Contacts-App-Backend/blob/master/LICENSE))  
- Frontend: MIT ([LICENSE](https://github.com/Alexzander-Hurd/Contacts-App-Clients/blob/master/LICENSE))  