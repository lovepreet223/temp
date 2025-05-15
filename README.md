# TDS Content Scraper

This project provides a Python-based web scraper for extracting content from the [TDS website](https://tds.s-anand.net/#/2025-01) using [Playwright](https://playwright.dev/python/). It navigates through the site's sidebar, scrapes each content page, and saves the results (including titles, hierarchy, content, and links) into a structured JSON file.

---

## Project Structure
.
├── config.py
├── content_scraper.py
└── README.md

---

## Files Overview

- **config.py**  
  Contains configuration variables, specifically the path to Playwright browsers for Conda environments.

- **content_scraper.py**  
  Main script that launches a Chromium browser, navigates the TDS website, scrapes all sidebar-linked content, and saves the results to `tds_scraped_data.json`.

---

## Prerequisites

- Python 3.7+
- [Playwright for Python](https://playwright.dev/python/docs/intro)
- [Miniconda](https://docs.conda.io/en/latest/miniconda.html) (if using Conda environments)

---

## Setup Instructions

1. **Install Dependencies**

    ```
    pip install playwright
    playwright install
    ```

    If using Conda, ensure Playwright browsers are installed in your Conda environment:

    ```
    playwright install
    ```

2. **Configure Browser Path**

    Edit `config.py` to set the correct path to your Playwright browsers.  
    Example (default provided):

    ```
    PLAYWRIGHT_BROWSERS_PATH = r"C:\Users\<YourUsername>\miniconda3\playwright"
    ```

---

## Usage

Run the scraper with:

`python content_scraper.py`


- The browser will open and automatically navigate through all sidebar links.
- Scraped data will be saved to `tds_scraped_data.json` in the current directory.

---

## Output

- **tds_scraped_data.json**  
  A JSON file containing an array of objects, each with:
  - `title`: Page title
  - `hierarchy`: List representing the folder structure in the sidebar
  - `content`: Main textual content of the page
  - `links`: All links found in the content (with text and URL)
  - `url`: Full URL to the scraped page

---

## Customization

- **Headless Mode**  
  By default, the browser runs in non-headless mode (`headless=False`).  
  To run without opening a browser window, set `headless=True` in `content_scraper.py`.

- **Timeouts and User-Agent**  
  You can adjust timeouts or the user-agent string in `content_scraper.py` for more robust scraping.

---

## Troubleshooting

- **Playwright Browser Not Found:**  
  Ensure `PLAYWRIGHT_BROWSERS_PATH` in `config.py` matches the actual location of Playwright browsers, especially if using Conda.

- **Timeouts:**  
  If you encounter timeouts, try increasing timeout values in the script.

- **Permission Issues:**  
  Run the script with appropriate permissions or in a virtual environment.

---

## License

MIT License

---

## Acknowledgements

- [Playwright for Python](https://playwright.dev/python/)
- [TDS by S Anand](https://tds.s-anand.net/)

---

*Happy scraping!*

