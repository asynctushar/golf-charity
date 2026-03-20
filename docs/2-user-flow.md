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

### Phase 2: Simulation (Admin Only)
16. Admin can run simulation of draw logic
17. Used for validation and testing

---

### Phase 3: Execution
18. Admin runs draw
19. System generates 5 numbers
20. Matching logic executed

---

### Phase 4: Publish
21. Admin publishes results
22. Users can view:
    - draw numbers
    - winners
    - prize distribution


## Verification Flow

23. User uploads proof (optional)
24. Admin reviews submission
25. Admin approves/rejects

---

## Payout Flow

26. Approved winners marked as "paid"

---

## Charity Flow

27. Contribution deducted during subscription
28. Applied to selected charity
29. Updates apply from next billing cycle