# GroupExpense – Shared Expense Manager

**Stop arguing about money.**

GroupExpense is a straightforward web app designed to help roommates, friends, and travel groups track shared costs without the headache. Instead of messy spreadsheets or "I'll pay you back later" texts, this app keeps a clear record of who paid what and settles the math instantly.

---

## Table of Contents

- [Overview](#overview)
- [The Problem](#the-problem)
- [Target Users](#target-users)
- [Key Features](#key-features)
- [Success Metrics](#success-metrics)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [MoSCoW](#moscow)
- [Software Design](#software-design)

---

## Overview

**Project Name**: GroupExpense

GroupExpense is built to be the "single source of truth" for small groups. Whether it's splitting rent, tracking a weekend trip, or managing club funds, the goal is speed and simplicity. We wanted to build something mobile-friendly that students can actually use to settle debts without awkward conversations.

## The Problem

- **Messy Records:** Keeping track of expenses on WhatsApp or Notes is a nightmare. Things get buried, forgotten, or deleted.
- **The "Who Paid?" Confusion:** After a long trip or a semester of hostel life, nobody remembers who covered the Uber, the dinner, or the Wi-Fi bill.
- **Math Errors:** Manual splitting almost always leads to mistakes (and arguments).

**Our Solution:** You log the expense, and the app automatically updates everyone's balance.

## Target Users

**Ravi – The Roommate**
*20-year-old engineering student.*
He lives in a hostel with three others. He needs a way to track the mess bill, cleaning supplies, and late-night snacks without constantly nagging his roommates for cash.

**Priya – The Trip Organizer**
*21-year-old student who loves travel.*
She books the hotels and transport upfront. She hates chasing people for their share and wants a link she can send that shows everyone exactly what they owe.

**Arjun – The Club Treasurer**
*College club organizer.*
He handles reimbursements for events. He needs transparency so he can show the student council exactly where the budget went.

## Key Features

- **Context-Based Groups:** Create separate spaces for "Room 302," "Goa Trip," or "Farewell Party."
- **Smart Splitting:** Split bills equally or assign specific amounts to specific people.
- **The Dashboard:** A clean view showing net balances (e.g., "You owe Ravi ₹500").
- **Settle Up:** A simple button to wipe the debt once you've paid via UPI or cash.
- **Activity Log:** A transparent history of every transaction.

## Success Metrics

- **Adoption:** Test users should be able to create a group and log an expense in under 2 minutes.
- **Performance:** Balances must update in real-time (under 10 seconds).
- **Accuracy:** Zero calculation errors during testing, even with uneven splits.

## Assumptions & Constraints

- **No Payment Processing:** We don't handle real money. You settle up externally (UPI, Cash, etc.); we just track the numbers.
- **Small Scale:** Optimized for small groups (2–15 people), not enterprise finance.
- **Free Tier:** The project is designed to run on free-tier infrastructure (GitHub, Docker Hub, Free Cloud DBs).

---

## Tech Stack

*(Proposed stack - adjustable based on implementation)*

- **Frontend**: React (Vite)
- **Backend**: Node.js (Express)
- **Database**: PostgreSQL (Prisma ORM)
- **DevOps**: Docker & Docker Compose
- **Version Control**: Git

---

## MoSCoW

| Priority    | User Stories                        | Count |
| ----------- | ----------------------------------- | ----- |
| MUST HAVE   | US-01,02,03,04,05,08,09,10,11,16,17 | 11    |
| SHOULD HAVE | US-06,07,13,14,15,18                | 6     |
| COULD HAVE  | US-12,19,20,21,22,23,24             | 7     |
| WON'T HAVE  | US-25                               | 1     |

---

## Project Structure

```text
group-expense/
├─ frontend/          # React application
│  ├─ src/
│  └─ package.json
├─ backend/           # API and Logic
│  ├─ src/
│  └─ package.json
├─ docs/
│  └─ design/         # Architecture diagrams & Figma screenshots
├─ docker-compose.yml # Container orchestration
├─ README.md
└─ .gitignore
```

---

## Getting Started

### Quick Start – Local Development

```bash
git clone https://github.com/<your-username>/group-expense.git
cd group-expense
docker-compose up --build
```

App runs at `http://localhost:5173`

### Branching Strategy (GitHub Flow)

- `main` — stable, always deployable
- Feature branches: `feature/<story-id>-<short-description>`
- Open a Pull Request to `main` after each feature
- Delete branch after merge

### Local Development Tools

- **Node.js** v20 LTS
- **npm** v10
- **Docker Desktop** v4.x
- **VS Code** with ESLint and Prettier
- **Git** v2.x
- **Postman** for API testing

---

## Software Design

GroupExpense follows a **client-server, layered architecture** with three independent layers: React frontend, Express backend, and PostgreSQL database, each running in its own Docker container. All layers communicate via a REST API, keeping coupling low and making each layer independently replaceable. Auth, expense, and balance logic are separated into their own modules to maintain high cohesion.

### Architecture Diagram

![Architecture Diagram](docs/design/architecture.png)

### UI Wireframes (Figma)

[View Figma Prototype](<your-figma-link>)

| Screen | UI Decision |
| ------ | ----------- |
| Login / Sign Up | Minimal form — reduces friction for first-time users |
| Group List Dashboard | Red/green balance indicators — instant visual clarity |
| Group Detail View | Member avatars + amounts — scannable on mobile |
| Add Expense | Equal/custom split toggle on one screen — reduces errors |
| Settle Up | Single confirm button — prevents accidental taps |
| Activity Log | Pinned search bar — find any transaction quickly |

### Key Design Decisions

1. **REST API between frontend and backend** — keeps layers fully decoupled
2. **Prisma ORM over raw SQL** — type-safe queries, easier to maintain
3. **Separated auth into its own module** — changes to login don't affect expense logic
4. **Docker Compose for local dev** — consistent environment across all team members
5. **No in-app payments** — keeps scope achievable and avoids security compliance overhead
