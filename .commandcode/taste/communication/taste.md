# Communication preferences

- Writes and expects replies in Spanish (informal, direct tone). Confidence: 0.9
- Prefers concise deliverables: a table/summary over per-item narration, grouping items with nothing to report as a single "OK" to save space, and being specific only where a real problem was found. Confidence: 0.8
- Wants the agent to explore the codebase itself (read files, infer the repeated convention) instead of asking the user to describe it. Confidence: 0.75
- When reporting a fix, wants explicit concrete implementation values (e.g. exact blur/opacity numbers) rather than vague claims — especially for a change that didn't visibly take effect before. Confidence: 0.75
- Wants affirmative verification that specific named elements (a field, a button) are fully visible and reachable, including across state variants like different tabs. Confidence: 0.75
- Wants the rationale behind chosen values explained (e.g. why a specific breakpoint/viewport width was picked) plus confirmation it was validated against the real target device/viewport. Confidence: 0.65
- Comfortable delegating visual/aesthetic judgment to the agent on ambiguous design details (e.g. how to adapt a two-segment wordmark to a short name), granting latitude ("tu criterio visual") rather than prescribing every visual decision. Confidence: 0.6
