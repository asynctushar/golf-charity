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

#### Draw Configuration
- Admin can configure draw settings:
  - draw type: random (implemented) or algorithmic (future-ready)
  - draw date (monthly cadence)
- System is designed to support both:
  - Random generation (lottery-style)
  - Algorithmic weighting (based on score frequency)

---

#### Draw Lifecycle

Each draw follows a controlled lifecycle:

1. Announced
   - Upcoming draw is visible to users
   - Estimated participants and prize pool displayed

2. Simulation (Pre-analysis)
   - Admin can run test simulations of draw logic
   - Helps validate draw configuration before publishing results
   - Does not affect actual draw data

3. Executed
   - System generates 5 numbers
   - Matching logic applied against user scores
   - Winners are determined

4. Published
   - Admin publishes draw results
   - Results become visible to users
   - Ensures control over timing and validation

---

#### Draw Logic

- Default implementation: random number generation (1–45)
- Matching rules:
  - 5 matches → jackpot
  - 4 matches → tier 2
  - 3 matches → tier 3

---

#### Monthly Cadence

- Draws occur once per month
- Each draw is uniquely identified by month/year
- Historical draws are stored and viewable

---

#### Jackpot Rollover

- If no 5-match winner:
  - jackpot amount is carried forward to next draw
- Stored as:
  - `jackpotCarryForward` in draw table


### 4. Prize Pool System
- Pool derived from active subscribers
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
- name
- charityId
- contributionPercentage
- stripeCustomerId
- stripeSubscriptionId
- subscriptionStatus

#### scores
- id
- userId
- value
- date

#### draws
- id
- numbers
- drawDate
- totalPool
- participantsCount
- type (random, algorithm-based)
- jackpotCarryForward
- status (announced, completed)

#### winners
- id
- userId
- drawId
- matchCount
- prizeAmount
- status
- proof
- proofStatus

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