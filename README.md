# FlashDecky — Instant Flash Cards (Beta Parser, fixed)

- Beta parser: TERM before first `-`/`–`/`—`/`:`; continuation lines appended to DEF.
- Editor dtype fixes to avoid Streamlit TextColumn type errors.
- OCR key auto from Streamlit Secrets (`OCR_SPACE_API_KEY`), fallback env var.
- Footer printed inside each card (front & back). Duplex modes + offsets.

## Run
```bash
python -m venv .venv && source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
streamlit run app.py
```
