# Journey and participation rules

All thresholds below are assumptions for the simulation. The prototype tests them.

## Journey

| Stage | ID | Definition |
|---|---|---|
| Waitlist joined | S0 | Verified email on the waitlist |
| Invited | S1 | Invite sent in a batch |
| Disclosure opened | S2 | Participant opens the disclosure page |
| Meaningful read | S3 | At least 90 seconds of active time and 80% scroll depth |
| Review submitted | S4 | Question or review submitted, tagged to a disclosure section |
| Qualified review | S5 | Passes the quality gate below |
| Qualified follow-up | S6 | Reviewer requests a meeting or data from the project team, or accepts a team request |
| Acknowledgement (optional) | S-A | Side branch after S4. Never a gate for any stage or credit |

Primary conversion metric: invited participants who reach S5, divided by invited participants.

Wallet connections, acknowledgements and raw transactions are side metrics. They never enter the funnel.

## Eligibility

- One person, one waitlist entry, verified email.
- Participants are invited from the waitlist in batches.
- No wallet is needed at any stage.

## Incentive logic

Currency is non-cash reviewer credit. It buys priority access to future disclosures and a reviewer badge. The simulation uses no cash and no tokens.

| Action | Credit |
|---|---|
| Review submitted | 0 |
| Qualified review | 10 |
| Strong review (rubric 5 of 5, or answered by the project team) | +5 |
| Follow-up accepted | +10 |
| Testnet acknowledgement | 0 (a visible mark only) |

- Cap: three credited reviews per participant per disclosure.
- Credit is stated upfront and awarded only after the quality gate.
- Acknowledgement earns nothing, so connecting a wallet gives no advantage.

## Qualified review gate

All of the following must hold:

1. Tagged to a specific disclosure section.
2. A review of 40 or more words, or a question of 15 or more words.
3. Adds something the disclosure does not state: an unanswered question or a concrete gap.
4. Less than 80% text similarity to any earlier submission.
5. Passes duplicate and bot checks.
6. Reviewer rubric score of 3 out of 5 or higher.

## Exclusions

- Employees and contractors of the project or the platform.
- Submissions flagged as duplicates.
- Submissions that give investment advice, promise returns or claim asset ownership.
- Submissions written to promote a product or a link.

## Duplicate and bot handling

- One entry per normalised email (dots and plus-tags removed).
- More than three participants on one device fingerprint in a batch are held for review.
- The submit button enables only after the meaningful-read threshold.
- Text similarity of 80% or more against any prior submission marks it a duplicate, with no credit.
- A hidden honeypot field catches scripted submissions.
- Maximum of three submissions per participant in 24 hours.

## Optional on-chain acknowledgement

- **Network:** testnet only.
- **When offered:** after S4, with a clear skip option.
- **What it records:** the disclosure version hash and a timestamp, signed by the participant's wallet. The statement shown is "I have read this disclosure version."
- **What it is not:** proof of asset ownership, verified reserves or a guaranteed investment. This copy appears before signing.
- **Decliners:** identical credit and identical access.
- **Failure handling:** a rejected signature, missing testnet gas or an RPC timeout triggers one retry. If it still fails, the review stays valid and the event is logged as `ack_failed` with a reason code.
- **Measurement:** reported in a separate panel, apart from qualified conversion.
