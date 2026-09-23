# PITCH.md

Six lines and a lever. Your words. The last two are scored.

Built: A disruption-care agent that reads bookings, flight status, and policy before answering.
Does: It identifies the passenger, checks the disrupted segment, resolves entitlements, and escalates work outside chat scope.
Number: Stage 2 wire-rule passes improved from 12/15 to 15/15 conversations, with 3 runs per case.
Safety check: Rebooking is held before confirmation, and refund requests never call a refund tool.
Next: Improve adversarial-message handling, then compare the same Stage 1 and Stage 2 suites before and after.
Still broken: The baseline prompt does not reliably acknowledge abuse or legal threats before escalating.
Lever: intelligence

## Priya asked

Costs: The intelligence lever may increase tokens and latency because it adds explicit safety guidance.
Wrong: A passing response can still be phrased poorly, so the judge evidence must be read rather than trusted blindly.
Runs it: The eval harness runs frozen customer cases and checks both tool calls and written responses.
Left out: Refund execution, final booking confirmation, and other irreversible actions remain human or UI-controlled.
