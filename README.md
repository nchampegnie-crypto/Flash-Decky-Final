# FlashDecky — Instant Flash Cards (Beta Parser)

Make print-ready flash cards from paste, spreadsheets, or screenshots. Teacher-friendly. Duplex alignment with fine-tune offsets. 8 cards per US Letter.

## ✨ Highlights
- **Beta parsing behavior**: term before first `-` / `–` / `—` / `:`; non-matching lines append to the previous definition with smart spacing.
- **Inputs**: paste free-form text, CSV/TSV/XLSX (column mapper), screenshots (PNG/JPG) with OCR (key pulled from Streamlit Secrets).
- **Review & edit**: grid editor (add/delete/bulk paste). Validation flags empty Front/Back. Live card & sheet counts.
- **PDF**: 8 per page, dashed cut lines, **long-edge mirrored** backs (default) + other duplex modes, **back-page X/Y offsets (mm)**, optional corner markers, auto-wrap & gentle font auto-shrink, definition side vertically centered.
- **Per-card footer** (front & back): choose `{subject} • {lesson}` or `{lesson} • {subject}`.

## 🚀 Quickstart
```bash
python -m venv .venv && source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
export OCR_SPACE_API_KEY=YOUR_KEY   # (optional) or put in Streamlit Secrets
streamlit run app.py
```

## 📝 Parsing rules (Beta)
```
^\s*(?:\d+[\.)]\s*)?(?:[•-]\s*)?(?P<term>.+?)\s*(?:[-\u2013\u2014:])\s+(?P<def>.+)\s*$
```
- New item when a line matches the above (optional number/bullet, then TERM, then separator, then DEF).
- Continuations: non-matching lines are appended to previous **DEF** (no extra space if DEF ended with a dash).

## 🔐 OCR Key
Uses **Streamlit Secrets** first (`OCR_SPACE_API_KEY`), then env var. No key field in the UI for screenshots.
