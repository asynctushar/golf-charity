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
14. Upcoming monthly draw is visible
15. System shows:
    - estimated participants
    - estimated prize pool

---

### Phase 2: Locked (1 day before draw)
16. System locks:
    - eligible participants
    - prize pool
17. No further changes affect this draw

---

### Phase 3: Simulation (Admin Only)
18. Admin can run simulation of draw logic
19. Used for validation and testing

---

### Phase 4: Execution
20. Admin runs draw
21. System generates 5 numbers
22. Matching logic executed

---

### Phase 5: Publish
23. Admin publishes results
24. Users can view:
    - draw numbers
    - winners
    - prize distribution


## Verification Flow

25. User uploads proof (optional)
26. Admin reviews submission
27. Admin approves/rejects

---

## Payout Flow

28. Approved winners marked as "paid"

---

## Charity Flow

29. Contribution deducted during subscription
30. Applied to selected charity
31. Updates apply from next billing cycle