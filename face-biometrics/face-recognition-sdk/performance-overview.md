---
icon: chart-line
---

# Performance Overview

## Face Recognition performance overview

Evaluate 1:1 pairs only. Keep identity-disjoint development and test splits. Include same-person and different-person pairs captured under representative conditions.

Record false-match and false-non-match rates at each operating threshold. Record no-face, invalid-image, and recapture rates separately. Measure cold and warm latency, then report percentile latency and hardware details. Do not reuse templates outside the approved evaluation.

## <i class="fa-chart-line">:chart-line:</i> Record the test configuration

Record the SDK release, device or host, input set, and configuration with each evaluation. Report how many inputs produced a usable result and how many required recapture or produced a technical error. Use the [Linux sample](desktop-and-server/linux/sample-application.md) to confirm the expected output before collecting results.
