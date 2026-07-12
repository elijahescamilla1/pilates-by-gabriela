# Pilates by Gabriela

Portfolio / booking site for Gabriela — BASI-certified Pilates instructor in Los Angeles.

Static site: a single `index.html` plus a `media/` folder. No build step, no dependencies.
Implemented from the Claude Design project "Pilates by Gabriela v3".

## Run locally

```sh
python3 -m http.server 8000
# open http://localhost:8000
```

## Deploy

Works on any static host (GitHub Pages, Netlify, Vercel, Cloudflare Pages). Point it at the repo root.

## Notes

- Booking CTAs link out to the Square site (`pilates-by-gabriela.square.site`); the checkout modal is a visual demo and does not process payments.
- `media/about.jpg` currently reuses one of the studio photos (IMG_6604) as a stand-in for the About portrait from the design mockup — swap it when the final photo is picked.
