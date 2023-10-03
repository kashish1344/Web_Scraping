# **Scrape law guides from Indian Kanoon**

import requests
from bs4 import BeautifulSoup
import json

def scrape_law_guides(topic):
  """Scrape law guides from Indian Kanoon for a given topic and save the scraped content to a JSON file.

  Args:
    topic: The topic of the law guides that you want to scrape.

  Returns:
    None.
  """

  # Install the required dependencies.
  # pip install requests bs4 json

  # Make a request to the law guides page on Indian Kanoon.
  response = requests.get(f"https://lawrato.com/indian-kanoon/law-guides/{topic}")

  # Extract the HTML response as a BeautifulSoup object.
  soup = BeautifulSoup(response.content, "html.parser")

  # Find all href links on the page.
  href_links = []
  for link in soup.find_all("a"):
    if link.has_attr("href"):
      href_links.append(link["href"])

  # Create a JSON object to store the scraped content.
  scraped_content_json = {}

  # Iterate over the href links and scrape the content of each page.
  for href_link in href_links:

    # Make a request to the href link.
    response = requests.get(href_link)

    # Extract the HTML response as a BeautifulSoup object.
    soup = BeautifulSoup(response.content, "html.parser")

    # Extract the heading and content of the page.
    heading = soup.find("h1").text
    content = soup.find_all("p")
    content = [paragraph.text.strip() for paragraph in content]

    # Create a JSON object for the scraped content.
    scraped_content_json[href_link] = {
      "title": heading,
      "content": content,
    }

  # Save the scraped content to a JSON file.
  with open("law_guides.json", "w") as json_file:
    json.dump(scraped_content_json, json_file, indent=4)

if __name__ == "__main__":
  # Get the topic that you want to scrape.
  topic = input("Enter the topic that you want to scrape: ")

  # Scrape the law guides for the given topic.
  scrape_law_guides(topic)

Use code with caution. Learn more
Use code with caution.
This code is provided for educational purposes only. Use it with caution and take responsibility for your actions.

Learn more.
For more information on scraping, please see the following resources:

Scrapy documentation: https://doc.scrapy.org/en/latest/
Beautiful Soup documentation: https://www.crummy.com/software/BeautifulSoup/bs4/doc/
Enjoy!
Python
# **Python code to print the title and content of the first scraped page**

import json

with open("law_guides.json", "r") as json_file:
  scraped_content_json = json.load(json_file)

first_scraped_page = scraped_content_json["https://lawrato.com/indian-kanoon/divorce-law-guides/1"]

title = first_scraped_page["title"]
content = first_scraped_page["content"]

print(title)
print(content)
