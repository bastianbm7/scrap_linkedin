# LinkedIn Job Scraper

Selenium-based scraper that automates browsing LinkedIn's public job search results and extracts structured job posting data (title, company, location, full description) for a given search query.

## What it does

- Launches a Chrome session via Selenium and opens a LinkedIn Jobs search URL (configurable keywords/location, e.g. "data scientist").
- Waits for the results list to render, then iterates through the visible job cards, clicking each one and expanding its "Show more" description panel.
- Extracts the job title, company/location line, and full job description text for each listing.

## Tech stack

Python, Selenium WebDriver, ChromeDriver.

## Project structure

```
scrap_linkedin.ipynb   # Scraping logic and extraction loop
requirements.txt
```

## How to run

```bash
pip install -r requirements.txt
```

This project needs a matching ChromeDriver executable, which isn't included here (it's a large, platform-specific binary). Get one automatically instead of downloading it by hand:

```bash
pip install webdriver-manager
```

```python
from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from webdriver_manager.chrome import ChromeDriverManager

driver = webdriver.Chrome(service=Service(ChromeDriverManager().install()))
```

and swap that in for the `Service(driver_path)` call at the top of the notebook (which originally pointed at a local `chromedriver-win64/chromedriver.exe`).

## Notes

Scraping LinkedIn is subject to their Terms of Service — this project was built for personal job-search automation on a small scale, not for large-scale or commercial scraping.
