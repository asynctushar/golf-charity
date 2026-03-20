# Key Product Decisions

## 1. Draw Fairness

Draw participation is based on score matching rather than contribution amount, ensuring equal opportunity for all users.

---

## 2. Draw Locking Strategy

Each draw follows a 3-phase lifecycle:
- Announced → dynamic estimates shown
- Locked (1 day before draw date) → participants and pool finalized
- Executed → results generated

This ensures fairness, consistency, and prevents last-minute changes affecting results.

---

## 3. Eligibility Criteria

Users are eligible for a draw if:
- subscription is active
- currentPeriodEnd is valid
- user has at least one score

Eligibility is evaluated at lock time.

---

## 4. Contribution Updates

Users can modify contribution percentage anytime, but changes apply from the next billing cycle to avoid inconsistencies.

---

## 5. No Wallet System

Winnings are not stored in an internal wallet.
They are tracked using payout status (pending → paid) to keep system simple.

---

## 6. Winner Verification Simplification

Only one proof upload is required per winner to reduce complexity.

---

## 7. Draw Logic Scope

Only random draw logic is implemented for MVP.
Algorithm-based weighted draw is excluded.

---

## 8. Admin-Controlled Execution

Draw execution is manually triggered by admin to ensure control and prevent unintended runs.

---

## 9. Subscription Validation

Access control is enforced using:
- subscriptionStatus
- currentPeriodEnd

This avoids frequent Stripe API calls and ensures real-time validation.

---

## 10. Visibility & Transparency

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