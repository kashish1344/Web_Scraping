This code scrapes the law guides page on Indian Kanoon for a given topic and saves the scraped content to a JSON file.

Usage:

Run the code:
python scrape_law_guides.py
The code will ask you to enter the topic that you want to scrape.

Enter the topic and press Enter.

The code will scrape the law guides for the topic that you entered and save the scraped content to a JSON file called law_guides.json in the current directory.

Example:

Enter the topic that you want to scrape: divorce-law
The code will scrape the law guides for the topic "divorce law" and save the scraped content to a JSON file called law_guides.json.

You can then use the JSON file to access the scraped content. For example, the following code will print the title and content of the first scraped page:

Python
import json

with open("law_guides.json", "r") as json_file:
    scraped_content_json = json.load(json_file)

first_scraped_page = scraped_content_json["https://lawrato.com/indian-kanoon/divorce-law-guides/1"]

title = first_scraped_page["title"]
content = first_scraped_page["content"]

print(title)
print(content)
Use code with caution. Learn more
