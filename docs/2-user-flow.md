# User Flow

## Public Flow

1. User visits homepage
2. Reads about platform
3. Clicks "Subscribe"
4. Navigates to signup

---

## Registration & Subscription Flow

5. User creates account
6. Selects charity
7. Chooses contribution %
8. Completes Stripe payment
9. Redirected to dashboard

---

## Dashboard Flow

10. User views:
   - subscription status
   - selected charity
   - contribution %
   - scores
   - draw information

---

## Score Flow

11. User enters score
12. System stores score
13. If more than 5 scores:
    - oldest is removed

---

## Draw Lifecycle Flow

### Phase 1: Announced
14. Upcoming draw is visible
15. System shows:
    - estimated participants
    - estimated prize pool

---

### Phase 2: Locked (1 day before draw)
16. System locks:
    - eligible participants
    - prize pool
17. No further changes allowed

---

### Phase 3: Execution
18. Admin runs draw
19. System generates 5 numbers
20. Matching logic executed

---

## Winner Flow

21. Winners identified
22. Records created (status: pending)
23. User sees result in dashboard

---

## Verification Flow

24. User uploads proof (optional)
25. Admin reviews submission
26. Admin approves/rejects

---

## Payout Flow

27. Approved winners marked as "paid"

---

## Charity Flow

28. Contribution deducted during subscription
29. Applied to selected charity
30. Updates apply from next billing cycle