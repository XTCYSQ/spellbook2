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

## 2026-03-09 - Replace Gemini frontend chat with Tawk.to (human-to-human)
**What:** Added Tawk.to embed script and disabled the custom Gemini-based chat widget UI.
**Why:** GitHub Pages is static and Gemini API quota/billing issues block the demo; Tawk.to provides reliable human support chat without a backend.
**How:** Embedded the Tawk.to widget (`embed.tawk.to/69aec5927ac1721c39912d81/1jj9b7h1a`), forced-hide `#chat-toggle`/`#chat-win`, and made `openChat()`/`closeChat()` maximize/minimize Tawk.to when available.
**Files:**
- index.html
- AI_DECISIONS.md
**Alternatives:**
- Keep Gemini chat and fix quotas/billing.
- Use a different live chat provider (Crisp, Intercom, etc.).
**Trade-offs:**
- Loses AI auto-replies; requires manual operator responses in the Tawk.to dashboard/app.
