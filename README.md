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

---

## Overview

**Project Name**: GroupExpense

GroupExpense is built to be the "single source of truth" for small groups. Whether it’s splitting rent, tracking a weekend trip, or managing club funds, the goal is speed and simplicity. We wanted to build something mobile-friendly that students can actually use to settle debts without awkward conversations.

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

## Project Structure

```text
group-expense/
├─ frontend/          # React application
│  ├─ src/
│  └─ package.json
├─ backend/           # API and Logic
│  ├─ src/
│  └─ package.json
├─ docker-compose.yml # Container orchestration
├─ README.md
└─ .gitignore
