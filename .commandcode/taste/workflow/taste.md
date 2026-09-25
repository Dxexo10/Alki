# Workflow preferences

- Prefers processing files in small batches (3-4 at a time), explicitly avoiding large batches of 6+, to avoid overloading the process. Confidence: 0.8
- Expects heavy use of search tooling (e.g. grep/ripgrep across the repo) to find references and map scope before editing. Confidence: 0.7
- Expects the agent to read each referenced file before editing rather than assuming its contents ("read them first, don't assume"). Confidence: 0.7
- When a fix is requested, expects it applied to ALL affected screens/files at once (centralizing in shared CSS when possible) rather than patching a single screen — repeatedly frustrated by fixes that were only applied to one screen. Confidence: 0.8
- Expects verification that a change actually produces the intended visible/rendered result (e.g. confirm the spacing/effect is really visible, not just declared in CSS) before considering it done. Confidence: 0.7
- When a bug that was supposedly already fixed reappears, wants a specific root-cause explanation (why the earlier fix didn't cover it) plus a preventive fix that sweeps the whole project for the same anti-pattern so it can't recur in other files. Confidence: 0.8
- Once the same class of bug recurs across multiple files (e.g. content cut off behind a fixed bottom bar), stops wanting per-file patches and demands a single systemic root-cause fix applied project-wide before touching anything else. Confidence: 0.85
- After a systemic/root-cause fix, wants a breakdown of how many screens it resolved on its own vs. which needed extra per-screen intervention. Confidence: 0.75
- Treats this project as a mockup/prototype: prefers simulated static data over real integrations (e.g. fill a fixed test address instead of calling real geolocation). Confidence: 0.7
- For the mockup, wants cross-screen state simulated via localStorage or a shared in-memory variable in shared.js (e.g. a newly published item persists and shows on the panel, related counters update) — no backend required. Confidence: 0.7
- When a screen breaks, prefers fixing it by comparing it against a known-working equivalent screen and adopting the SAME pattern/classes (replacing whatever differs), explicitly rejecting "patching on top" of the broken file. Confidence: 0.75
- Expects equivalent/paired screens (client ↔ provider, rental ↔ services) to stay in strict parity: any fix or visual/functional treatment applied to one screen must also be applied to its counterpart, and unintentional divergences (one has a fix the other lacks) must be detected and corrected. Confidence: 0.8
- When a divergence is found, wants a proactive audit of ALL equivalent screen pairs (not just the reported one) before continuing, so the same class of desync can't hide elsewhere. Confidence: 0.75
- Documentation/specs must be derived from the real source of truth (extract the exact existing values from the actual files like design-system.css / shared.js) — never invent or approximate values, and flag when the code contradicts its own comments. Confidence: 0.85
- For a "reference document" request, keep the scope to the new doc only: do not modify any existing source/HTML files unless explicitly asked. Confidence: 0.6
- After a global rename/find-replace, expects a final search confirming zero remaining mentions of the old name across the repo, and treats residual matches in unrelated config/paths (e.g. a project folder path in settings) as out of scope rather than something to force-change. Confidence: 0.75
- Rebrands must be exhaustive across the whole project — every file type (HTML titles/visible text, CSS/JS comments and internal references, docs) plus non-visible internal identifiers like localStorage keys — not just user-facing strings. Confidence: 0.7
