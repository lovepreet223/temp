# IIT Madras Online Degree Discourse Scraper

This project provides a Python-based tool to **scrape posts and topics from the IIT Madras Online Degree Discourse forum** for a specified date range. It uses Selenium (with undetected-chromedriver) for authentication and Requests for efficient data fetching.

---

## Features

- **Date Range Filtering:** Scrape only topics created within your chosen start and end dates.
- **Page Limit Control:** Limit how many forum pages to scrape, for faster or more exhaustive runs.
- **Google SSO Support:** Handles login via Google Single Sign-On (SSO) using Selenium.
- **Structured Output:** Saves scraped data as a JSON file for easy analysis.

---

## File Structure

- `config.py`: Set your scraping parameters here (dates, pages).
- `discourse_scrapper.py`: Main script for scraping the forum.

---

## Getting Started

### 1. Install Dependencies
pip install selenium undetected-chromedriver beautifulsoup4 requests


### 2. Configure Your Scraping Parameters

Open `config.py` and adjust these variables as needed:

DATE_FORMAT = "%Y-%m-%d"
START_DATE = datetime.strptime("2025-01-01", DATE_FORMAT) # <-- Change this
END_DATE = datetime.strptime("2025-04-14", DATE_FORMAT) # <-- And this
PAGES = 10 # <-- And this!

- **START_DATE** and **END_DATE**: Only topics created between these dates will be scraped.
- **PAGES**: This is a special variable. It controls how many pages of topics to fetch from Discourse.  
  - **Tip:** If you want to ensure you cover all topics within your date range, you can increase this number.  
  - **Experiment:** Adjust `PAGES` up or down depending on how many topics you expect or how exhaustive you want the scrape to be.

### 3. Run the Scraper
python discourse_scrapper.py


- On first run, a Chrome window will open for you to log in via Google SSO.
- Once logged in, press ENTER in your terminal to continue.
- The script will save your login cookies for future runs.

### 4. Output

- Scraped data is saved to `scraped_data.json` in the current directory.
- Each entry includes:
  - Topic title and URL
  - First post content
  - All subsequent posts (with URLs and text, including links)

---

## Notes & Tips

- **Authentication:** The script saves your login cookies after the first run, so you don't need to log in every time.
- **Forum Category:** By default, it scrapes the "TDS Knowledge Base" category. You can change `CATEGORY_URL` in the script if needed.
- **Respect Rate Limits:** Avoid setting `PAGES` too high to prevent overloading the forum.

---

## Example: Customizing Your Scrape

Suppose you want to scrape only topics from February 2025 and limit to 5 pages:

config.py
START_DATE = datetime.strptime("2025-02-01", DATE_FORMAT)
END_DATE = datetime.strptime("2025-02-28", DATE_FORMAT)
PAGES = 5


---

## Troubleshooting

- **Login Issues:** If login fails, delete `discourse_cookies.pkl` and rerun the script.
- **Missing Data:** Increase `PAGES` if you think some topics in your date range are missing.
- **Dependencies:** Ensure Chrome browser is installed and matches your ChromeDriver version.

---

## License

MIT License

---

## Contributions

Pull requests and suggestions welcome!

---

Enjoy exploring the IITM Online Degree Discourse forum data!

