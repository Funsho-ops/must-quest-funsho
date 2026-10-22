# Experiment brief: deep-linked section prompt in the invitation email

All baseline figures are synthetic. The simulation illustrates the method and does not predict real results.

## Channel and question

**Channel:** email invitation to the waitlist.
**Question:** does an invite that names one disclosure section, states the time cost and states the credit rule produce more qualified reviews than a standard invite?

## Hypothesis

Invitees who receive a specific, bounded task submit more qualified reviews than invitees who receive an open request to read the full disclosure.

## Arms

| | Control | Treatment |
|---|---|---|
| Invite content | Standard invite, link to the top of the disclosure | Names one section, states a 3-minute time cost and the credit rule |
| Landing | Full disclosure page | Deep link to that section with the structured prompt |
| Acknowledgement | Optional, same copy | Optional, same copy |

Both arms use the same sender, send time and disclosure version.

## Assignment

Random 50/50 by hash of the normalised email, in equal batches. Each invite link is single-use and bound to one email, so a forwarded invite cannot create an unverified participant.

## Metrics

- **Primary:** qualified conversion, S5 / S1.
- **Step conversion:** S2 to S3, S3 to S4, S4 to S5.
- **Guardrails:** quality rate, duplicate rate, decliner parity, acknowledgement failure rate.
- **Never used as success:** wallet connections, acknowledgements, raw transactions, email opens.

## Sample and power

- Baseline: 41.7% (synthetic). Target: 50.0%, a 20% relative lift.
- Pilot of 200 per arm: about 39% power. Directional only.
- Decision test: about 560 per arm for 80% power. Recompute with the real baseline.

## Decision rules

1. Any guardrail breach in the PRD stop-rule table pauses the arm.
2. If the pilot lift is under 5% relative, end the test.
3. If control S2 to S3 conversion is below control S3 to S4 conversion, disclosure reading is the real bottleneck. Re-run the scoring in `intent.md` before scaling.
4. Otherwise, scale to the decision-test sample.

## Abuse risks specific to this test

- **Credit attracts farmers.** Credit posts only after the quality gate, capped at three reviews per disclosure.
- **Forwarded invites.** Single-use tokens bound to one email.
- **The time claim.** If median time to submit exceeds the stated 3 minutes by more than 50%, change the copy. A false time promise biases the result.

## Next validation step

Run the pilot with step-level events live. The first read-out is the control arm's step conversions, because they confirm or reject the bottleneck choice before any lift is measured.
