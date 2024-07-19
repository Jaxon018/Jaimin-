import requests
from bs4 import BeautifulSoup
import pandas as pd
import json

# Define the URL of the website to scrape
url = "http://quotes.toscrape.com/"

# Send a GET request to fetch the webpage content
response = requests.get(url)
response.raise_for_status()  # Check for request errors

# Parse the webpage content with BeautifulSoup
soup = BeautifulSoup(response.text, 'html.parser')

# Extract data (quotes and authors in this example)
quotes = soup.find_all('div', class_='quote')

# Create lists to store the extracted data
data = []
for quote in quotes:
    text = quote.find('span', class_='text').get_text()
    author = quote.find('small', class_='author').get_text()
    data.append({'text': text, 'author': author})

# Convert data to a DataFrame
df = pd.DataFrame(data)

# Save data to CSV
df.to_csv('quotes.csv', index=False)

# Save data to JSON
with open('quotes.json', 'w') as json_file:
    json.dump(data, json_file, indent=4)

print("Data has been saved to quotes.csv and quotes.json")
