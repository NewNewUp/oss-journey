# Never convert a retryable error into a generic one

A proxy mapped Gemini 429 RESOURCE_EXHAUSTED into a generic 500 no-credentials after its retry loop drained. The 429 carried a reset time. When a retry chain drains, preserve the original status and Retry-After: an empty 500 is indistinguishable from broken, and breaks caller backoff.
