---
'@mastra/client-js': patch
---

Fixed workflow run streams silently dropping events when a network chunk boundary split a multi-byte character. In Studio this left workflow graph step nodes stuck in the running state with a growing timer even though the step and the run had completed ([#17821](https://github.com/mastra-ai/mastra/issues/17821)). The stream parser now decodes across chunk boundaries correctly, and a single malformed record no longer blocks all events after it.
