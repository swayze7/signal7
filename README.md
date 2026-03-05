# SIGNAL 7

A static 2-page ARG-style puzzle hunt. No build tools required.

## File Structure

```
signal7/
├── index.html          # Stage 1 — The Intercept
├── vault-7x3k9.html    # Stage 2 — The Vault
├── assets/
│   ├── transmission.mp3    # Drop your ElevenLabs audio here
│   └── vault-audio.mp3     # Drop your victory audio here
├── css/
│   └── style.css
└── README.md
```

## Setup

### GitHub Pages

1. Clone or push this repo to GitHub
2. Go to **Settings → Pages**
3. Set source to **main** branch, root `/` (or `/docs` if you move it)
4. Your site will be live at `https://[username].github.io/[repo-name]/`

That's it. No npm, no build step.

### Audio Files

The site works without audio — both players display a fallback message if the
file is missing or fails to load.

When you have your audio:

1. Drop `transmission.mp3` into `assets/` — this plays on the intercept page
2. Drop `vault-audio.mp3` into `assets/` — this plays on the vault page
3. Commit and push

Supported formats: `.mp3`. If you use a different format, update the `<source
type>` attribute in both HTML files.

## The Puzzle

**Stage 1 (`index.html`):**

- Player lands on a fake "intercepted transmission" document viewer
- A large block of redacted (invisible) text in the middle of the document
  reveals the answer when highlighted/selected
- The answer is also visible as narrative text: **Protocol VAULT-7X3K9**
- Player can navigate to `vault-7x3k9.html` directly, OR type `VAULT-7X3K9`
  into the access code field at the bottom

**Hint timers (auto-appear, no interaction needed):**

- 3 minutes: "Try selecting the redacted text"
- 6 minutes: "The answer is a URL path"

**Input validation:**

- Case-insensitive
- Uses SHA-256 (SubtleCrypto) to compare hashes — the answer string is not
  stored as plain text in the JS validation logic

**Stage 2 (`vault-7x3k9.html`):**

- Black screen intro → "CLEARANCE VERIFIED" → page fades in
- Shows elapsed time since `index.html` was first loaded (stored in
  `localStorage`, cleared on vault page load so it resets for replays)
- A second hidden redacted block contains an easter egg message
- Background 60Hz hum via Web Audio API (auto-starts on first interaction,
  toggleable via the ◈ HUM button in the bottom-right corner)

## Sending the Link

Just send the raw `index.html` URL. No context, no explanation. The page does
the rest.
