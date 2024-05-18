# Law Guide Scraper

This project is a web scraper that extracts and organizes legal guide content from the LawRato website. The scraper fetches the list of law guides, allows the user to select a topic, and then scrapes the detailed content of the selected topic. The scraped content is saved as a JSON file.

## Features

- **Scrape Law Guides:** Fetches a list of law guides from the LawRato website.
- **User Selection:** Allows the user to select a specific law topic to scrape.
- **Detailed Content Extraction:** Scrapes the detailed content of the selected topic.
- **Save as JSON:** Saves the scraped content in a structured JSON format.

## Installation

1. **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/law-guide-scraper.git
    cd law-guide-scraper
    ```

2. **Create and activate a virtual environment:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3. **Install the dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

## Usage

1. **Run the script:**
    ```bash
    python scraper.py
    ```

2. **Select a topic:**
    - The script will display a list of law topics.
    - Enter the name of the topic you wish to scrape.

3. **View the scraped content:**
    - The scraped content will be saved in `law_guides.json`.

## Code Overview

- **`scraper.py`:** The main script that handles web scraping, user input, and JSON file creation.

### Core Functions

- **`requests.get(url)`:** Makes an HTTP request to the given URL and fetches the content.
- **`BeautifulSoup(response.content, "html.parser")`:** Parses the HTML content using BeautifulSoup.
- **`soup.find_all("div", class_="col-lg-12 col-xs-12 colMb venue-amenities")`:** Finds all the heading elements on the page.
- **`json.dump(scraped_content_json, json_file, indent=4)`:** Saves the scraped content as a JSON file.

## Dependencies

- requests
- beautifulsoup4
- lxml

We hope this scraper helps you efficiently extract and organize legal guide content!
