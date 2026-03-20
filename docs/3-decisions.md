# Key Product Decisions

## 1. Draw Fairness

Draw participation is based on score matching rather than contribution amount, ensuring equal opportunity for all users.

---

## 2. Draw Locking Strategy

Each draw follows a 3-phase lifecycle:
- Announced → dynamic estimates shown
- Executed → results generated

This ensures fairness, consistency, and prevents last-minute changes affecting results.

---

## 3. Eligibility Criteria

Users are eligible for a draw if:
- subscription is active
- user has at least one score

Eligibility is evaluated at lock time.

---

## 4. Contribution Updates

Users can modify contribution percentage anytime.

---

## 5. No Wallet System

Winnings are not stored in an internal wallet.
They are tracked using payout status (pending → paid) to keep system simple.

---

## 6. Winner Verification Simplification

Only one proof upload is required per winner to reduce complexity.

---

---

## 7. Admin-Controlled Execution

Draw execution is manually triggered by admin to ensure control and prevent unintended runs.

---

## 8. Subscription Validation

Access control is enforced using:
- subscriptionStatus

This avoids frequent Stripe API calls and ensures real-time validation.

---

## 9. Visibility & Transparency

Users can view:
- past draw results
- winning numbers
- winner summaries (masked identities)

This improves trust and engagement.

---

## 11. Scope Prioritization

The system focuses on core features:
- subscription
- score tracking
- draw system
- charity selection
- admin controls

Advanced features are excluded to ensure quality delivery within time constraints.

---

## 12. Draw Logic Flexibility

System is designed to support both:
- Random draw
- Algorithm-based weighted draw

---

## 13. Simulation Mode Scope

Simulation mode is included as a conceptual feature:
- Allows admin to test draw logic before publishing
- Implemented as a non-persistent or simplified preview in MVP

---

## 14. Result Publishing Control

Draw results are not immediately visible after execution.
Admin must explicitly publish results.

This ensures:
- validation of results
- controlled release of information
- better administrative control

---

## 15. Monthly Draw Cadence

Draws are scheduled monthly.
Each draw is associated with a specific month and stored for historical tracking and user visibility.