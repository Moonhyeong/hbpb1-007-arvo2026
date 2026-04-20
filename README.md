# HBPB1-007 · ARVO 2026 Landing Page

QR-targeted landing page for **ARVO 2026 Poster #126-0156** — *HBPB1-007: Topical Therapeutic Candidate for Geographic Atrophy*.

- **Session:** AMD: New drugs, delivery systems, and mechanisms of action I
- **Meeting:** ARVO 2026, Denver, CO, May 3–7, 2026
- **Publication:** Lim Y. et al., *Adv Sci* 2025, 12(1), 2406018 · [DOI](https://doi.org/10.1002/advs.202406018)

## Structure

```
landing-page/
├── index.html                  single-file landing page (inline CSS/JS)
├── README.md                   this file
├── .nojekyll                   disable Jekyll on GitHub Pages
├── assets/
│   └── poster.pdf              ARVO 2026 poster (drop in before publish)
└── images/
    ├── favicon.svg             site favicon
    ├── og-image.png            1200×630 social card (to produce)
    └── (figure exports)        Key Data figures exported from poster pptx files
```

## Before going live — asset checklist

- [ ] `assets/poster.pdf` — export final poster PDF here
- [ ] Extract and place 4 figures referenced in `index.html`:
  - In vitro MoA panel (from `[3B] In vitro MoA & Activity_Raw data_High res_수정.pptx`)
  - NaIO₃ mouse ONL / C3 IHC (from `in vivo images.pptx`)
  - Posterior ocular distribution panel
  - IOP time-course plot (from DTN250734 preliminary tox report)
- [ ] Replace figure placeholder boxes in `index.html` with `<img>` tags
- [ ] Produce `images/og-image.png` (1200×630) for social sharing

## Local preview

```bash
cd landing-page
python -m http.server 8000
# open http://localhost:8000
```

## Deploy (GitHub Pages)

1. Create public repo `hbpb1-007-arvo2026`
2. Push this folder as repo root
3. Settings → Pages → Deploy from branch `main` / root
4. URL: `https://<username>.github.io/hbpb1-007-arvo2026/`

## Design tokens

Navy `#1E2761` · Teal `#065A82` · Accent `#028090` · Green `#2E7D32` · Ice `#CADCFC` · BG `#F5F8FA` · Font: system sans-serif.

## Contact

- Drug Discovery: Dr. Moon-Hyeong Seo — mhseo@kist.re.kr
- Drug Development: Dr. Do Soo Jang — dosoo.jang@huonsbiopharma.com

---
© 2026 KIST. HBPB1-007 is exclusively licensed to Huons BioPharma (December 2024).
