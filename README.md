# Humanizer

Paste in text and it writes 3 rewrites in different styles (varied rhythm, plain and direct, conversational), scores each one, and shows you the best.

It's one HTML file with no build step and no server. It calls the Claude API straight from your browser using your own API key.

## How it works

1. **Rewrite** with Claude at high temperature, with rules against predictable phrasing (raises perplexity).
2. **Vary rhythm**: mixes short and long sentences, fragments, varied openers (raises burstiness).
3. **Strip AI tells**: about 60 stock phrases, em dashes, formulaic transitions, tidy three-item lists.
4. **Pick the best**: scores all 3 versions with a local heuristic and surfaces the lowest. The score combines sentence-length variation, AI-tell density, repeated sentence openers and vocabulary repetition.

The score is an approximation built from the same signals detectors use. It is **not** ZeroGPT's model, so check results in whatever detector you care about.

## Use it

**Option A: GitHub Pages (use it from any device)**
1. Push this repo to GitHub (public repo, or private on a paid plan).
2. Go to repo **Settings → Pages → Build and deployment**, set Source to *Deploy from a branch*, choose `main` and `/ (root)`, then click Save.
3. After about a minute it's live at `https://<your-username>.github.io/humanizer/`.

**Option B: Locally**
Just double-click `index.html` to open it in your browser.

Then paste your Anthropic API key (from https://console.anthropic.com → API Keys) into the key field at the top.

## About your API key

- The key is saved only in your browser's localStorage (uncheck "Remember on this device" to avoid that) and is sent only to `api.anthropic.com`.
- **Never commit your key to this repo.** It's typed into the page, not stored in the code, so the repo itself stays safe to make public.
- Each run makes 3 API calls. Set a monthly spend limit in the Anthropic console if you want a cap.
