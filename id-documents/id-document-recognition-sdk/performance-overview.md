---
icon: chart-line
---

# Performance Overview

## ID Document Recognition performance overview

Evaluate representative, authorized document captures with separate development and final-test sets. Record successful extraction, missing-field, recapture, and technical-error outcomes by document type and capture condition.

Measure cold and warm latency with the package version, hardware, configuration, and image policy recorded. Confirm coverage from the supplied release materials before interpreting results.

Use approved documents only. Split data by document and person before threshold or workflow tuning.

Measure field exact-match and field coverage per confirmed document type. Report capture failure, unsupported-document, and recapture rates separately. Measure cold and warm latency by operation. Never treat absent fields as extraction errors without a build-specific expected-field list.

## <i class="fa-chart-line">:chart-line:</i> Record the test configuration

Record the SDK release, device or host, input set, and configuration with each evaluation. Report how many inputs produced a usable result and how many required recapture or produced a technical error. Use the [Linux sample](desktop-and-server/linux/sample-application.md) to confirm the expected output before collecting results.
