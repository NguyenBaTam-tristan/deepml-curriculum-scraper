# deepml-curriculum-scraper

Scrape the full catalogue of [Deep-ML](https://www.deep-ml.com) (Problems, Math, Labs, Projects) into CSV/JSON, as input for a personalised daily study plan.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/NguyenBaTam-tristan/deepml-curriculum-scraper/blob/main/deep_ml.ipynb)

## Output

One row per item: `section`, `id`, `title`, `difficulty`, `category`, `tags`, `url`, plus `access`, `steps` and `popularity` where the site shows them.

## Usage

1. Open `deep_ml.ipynb` in Google Colab (button above).
2. Run the install cell, then the scraper cell:
```python
   !pip -q install playwright nest_asyncio
   !playwright install chromium
   !playwright install-deps chromium
```
3. `deepml_v2_<timestamp>.csv` and `.json` are downloaded when it finishes.

## How it works

Deep-ML renders its lists on the client (Next.js), so the notebook drives headless Chromium with Playwright and reads the rendered DOM, walking every page of the pagination bar. Items are de-duplicated by URL.

## Notes

- For personal use only. Check Deep-ML's terms of service and keep the request rate low.
- Scraped data is not included in this repo.
- If the site changes its markup, the selectors may need updating.
