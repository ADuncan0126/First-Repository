---
icon: wrench
---

# Troubleshooting

| Symptom                 | Recovery                                                                                      |
| ----------------------- | --------------------------------------------------------------------------------------------- |
| Engine or model missing | Supply the matching authorized assets and restart.                                            |
| Loader failure          | Check matching architecture and vendor-compatible libraries. Do not symlink OpenSSL versions. |
| License failure         | Check the required variable or root `license.txt`.                                            |
| Port in use             | Stop the conflicting process or use a separate supported configuration.                       |
| `413`, `422`, or `503`  | Reduce input below 15 MB, fix request validation, or check runtime readiness.                 |
| Camera unavailable      | Grant browser or desktop camera permission, then retry.                                       |

`/health` reports configuration, not successful inference. For ID Document Liveness, allow cold start and retry a failed worker once with an approved fixture.

If the issue persists, see [Contact & Support](contact-and-support.md) for what to include in a report.

## <i class="fa-list-check">:list-check:</i> Identify where the failure starts

Check installation, activation, and inference in that order. Run a known-good test input after the app or service reports ready. Include the first failing step and error code in your support request.
