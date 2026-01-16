# Playwright-based Notion Crawler

A **synchronous web crawler** built with Playwright, designed to visit a list of Notion pages, capture their fully rendered content, and extract structured information from each page.

Note: this version of the crawler is designed to visit Notion pages which contain song listing and extract their corresponding PDF charts.

---

## Features


- **Playwright-based** dynamic crawler (Chromium with JavaScript enabled).
- **Synchronous crawl loop**: pages are processed sequentially for stability and traceability.
- **Page-level processing module**: the crawler main loop is site-agnostic and delegates extraction logic to a dedicated page processor.
- **Configurable test runs**: optional crawl limit via stop_number.
- **Controlled pacing**: randomized delay between page visits.
- **Structured result collection**: special cases (e.g. empty pages) are tracked and written to JSON.
- **Explicit logging**: separate loggers for general activity and crawl errors.

---

## How it works

- Index scraper module: retrieves a Notion index page and generates a list of individual page URLs to crawl.
- Crawler main module: iterates over the collected Notion URLs, loads each page with Playwright, waits for domcontentloaded, and passes control to the page processor.
- Page processing module: extracts structured information from the rendered page and returns results to the crawler.
- Error isolation: failures on individual pages are logged without stopping the crawl.

--


## Requirements

- Python 3.9+
- Playwright
- BeautifulSoup4
- requests

1. Install dependencies: `pip install beautifulsoup4 playwright requests`
2. To complete Playwright installation, run in terminal: `playwright install`.

---

## Configuration

- Example:

```json
{
    "job_url": "https://wikiwilko.notion.site/SONGS-WITH-CHARTS-XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
}
```


- **job_url:** specifies the seed URL from which the crawl process starts.

---

## Usage

- Crawler usage example:

- **STEP 1:**

```Configure config.json values```.

- **STEP 2:**

```python main.py```

- **STEP 3**:

```Crawling results are stored in 'output' dir```

---

## Logs

- crawler.log: general activity
- crawler_errors.log: errors during crawling

---

## License

This project is licensed under the MIT License – see the LICENSE file for details.

---

## Disclaimer 

This tool is for educational purposes only. Users are responsible for complying with the Terms of Service of any website they crawl, including Notion.

---

## Contributions & Issues

Feel free to open issues or pull requests.
For major changes, please open an issue first to discuss.

---

## Acknowledgements

- Uses BeautifulSoup, Playwright and Requests.





