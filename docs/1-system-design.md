# System Design

## Overview

This platform is a subscription-based web application that combines golf score tracking, a monthly draw system, and charity contributions.

The architecture is designed as a full-stack Next.js application using API routes for backend functionality. The system follows a modular structure to ensure scalability and future support for mobile applications.

---

## Architecture

Client (Next.js UI)
        ↓
API Layer (Next.js API Routes)
        ↓
Service Layer (Business Logic)
        ↓
Database (PostgreSQL via Prisma + Supabase)

---

## Core Modules

### 1. Authentication & Subscription
- Authentication handled using NextAuth
- Stripe used for subscription payments (monthly/yearly)
- Subscription lifecycle managed via webhooks
- Subscription fields stored:
  - stripeCustomerId
  - stripeSubscriptionId
  - subscriptionStatus
- Access control enforced on every request

---

### 2. Score Management System
- Each user can store a maximum of 5 scores
- Each score includes:
  - value (1–45)
  - date
- When a new score is added:
  - the oldest score is automatically removed
- Scores are displayed in reverse chronological order

---

### 3. Draw Engine

#### Draw Lifecycle
1. Announced → estimated data shown
2. Locked (1 day before draw date) → final participants & pool
3. Executed → numbers generated and winners calculated

#### Logic
- Draw generates 5 random numbers (1–45)
- Matching logic:
  - 5 matches → jackpot
  - 4 matches → tier 2
  - 3 matches → tier 3

---

### 4. Prize Pool System
- Pool derived from active subscribers at lock time
- Distribution:
  - 40% → 5-match (jackpot)
  - 35% → 4-match
  - 25% → 3-match
- Jackpot rollover supported if no 5-match winner

---

### 5. Charity System
- Users select a charity during signup
- Contribution percentage (minimum 10%)
- Applied at subscription payment level
- Changes apply from next billing cycle

---

### 6. Winner Management System
- Winners stored with:
  - userId
  - drawId
  - matchCount
  - prizeAmount
  - status (pending, approved, paid)
- Proof upload supported (single file)
- Admin verifies and updates payout status

---

## Database Design

### Tables

#### users
- id
- email
- role
- charityId
- contributionPercentage
- stripeCustomerId
- stripeSubscriptionId
- subscriptionStatus
- currentPeriodEnd

#### scores
- id
- userId
- value
- date

#### draws
- id
- numbers
- drawDate
- lockDate
- totalPool
- participantsCount
- jackpotCarryForward
- status (announced, locked, completed)

#### winners
- id
- userId
- drawId
- matchCount
- prizeAmount
- status

#### charities
- id
- name
- description
- image

---

## Scalability Considerations

- API-first design allows mobile app integration
- Draw snapshot locking ensures consistency and fairness
- Business logic separated into service layer
- Database schema supports future extensions