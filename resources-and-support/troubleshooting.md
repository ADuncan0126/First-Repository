# Troubleshooting

## Troubleshooting

| Symptom                 | Recovery                                                                                      |
| ----------------------- | --------------------------------------------------------------------------------------------- |
| Engine or model missing | Supply the matching authorized assets and restart.                                            |
| Loader failure          | Check matching architecture and vendor-compatible libraries. Do not symlink OpenSSL versions. |
| License failure         | Check the required variable or root `license.txt`.                                            |
| Port in use             | Stop the conflicting process or use a separate supported configuration.                       |
| `413`, `422`, or `503`  | Reduce input below 15 MB, fix request validation, or check runtime readiness.                 |
| Camera unavailable      | Grant browser or desktop camera permission, then retry.                                       |

`/health` reports configuration, not successful inference. For ID Document Liveness, allow cold start and retry a failed worker once with an approved fixture.
