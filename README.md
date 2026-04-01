# Nia Labs — Landing Page

Premium single-page landing for **Nia Labs**, an AI automation agency by Глеб Давыдов.

**Live:** https://kitveff.github.io/nialabs/

---

## Preview

Open `index.html` directly in any modern browser — no local server required.

```
open index.html          # macOS
start index.html         # Windows
xdg-open index.html      # Linux
```

All fonts load from Google Fonts CDN. An internet connection is required for fonts and the embedded chat widget.

---

## Deploy

### GitLab Pages (free)

1. Push this repository to GitLab.
2. Create a `.gitlab-ci.yml` at the project root:

```yaml
pages:
  stage: deploy
  script:
    - mkdir -p public
    - cp index.html public/index.html
  artifacts:
    paths:
      - public
  only:
    - main
```

3. Push the file — GitLab CI will deploy automatically.
4. Your site will be live at `https://<your-username>.gitlab.io/<repo-name>/`.

### Netlify (drag-and-drop, free)

1. Go to [netlify.com](https://netlify.com) and log in.
2. Click **"Add new site → Deploy manually"**.
3. Drag the project folder (containing `index.html`) onto the upload area.
4. Netlify gives you a live URL instantly. Optionally assign a custom domain.

### Any static host

Upload `index.html` to any static hosting provider (Vercel, Cloudflare Pages, AWS S3 + CloudFront, etc.). The file is self-contained — no build step needed.

---

## Replacing Placeholders

Search the file for `REPLACE` comments and update the values below.

| Placeholder | Where | Description |
|---|---|---|
| `TELEGRAM_HANDLE` | `index.html` (×5) | Your Telegram username without `@`, e.g. `glebdavydov` |

Quick replace (macOS/Linux):

```bash
sed -i '' 's/TELEGRAM_HANDLE/your_tg_username/g' index.html
```

---

## Live Chat

The hero section embeds a live chat widget powered by **NextBot**. The widget is loaded via an `<iframe>` — no API keys or environment variables are required on the hosting side.

To update the widget configuration (bot ID, colors, welcome message, quick-reply buttons), replace the `src` URL of the `<iframe id="NextBot_chatWidgetIframe">` element in `index.html`.

---

## Tech Stack

- **Vanilla HTML / CSS / JS** — zero dependencies, no build tooling
- **Google Fonts** — Playfair Display + Inter
- **NextBot** — embedded live chat widget via iframe
- **CSS animations** — staggered word reveal, card fade-in via IntersectionObserver, particle canvas
- **Mobile-first responsive** — breakpoints at 640 px and 1024 px
