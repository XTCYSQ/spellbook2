---

## 2026-03-09 - Use a single Gemini API key in SpellBook demo page
**What:** Switched the frontend Gemini key configuration to use a single API key (no rotation) and reset the persisted key index.
**Why:** The demo should consistently use the newly created restricted key without cycling through older keys that may be blocked or out of quota.
**How:** Updated `GEMINI_KEYS` to contain only the new key and initialized `geminiKeyIndex` to `0` (also overwriting any previously stored `geminiKeyIndex` in `localStorage`).
**Files:**
- index.html
- AI_DECISIONS.md
**Alternatives:**
- Keep multiple keys and rotate on errors.
**Trade-offs:**
- No fallback if the single key hits quota or becomes blocked.
