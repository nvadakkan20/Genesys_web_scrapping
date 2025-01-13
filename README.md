# Genesys Scrapping Project

This project is designed to scrape details such as Customer Name, Location, Industry, Auther, Auther Designation from customer stories listed in the Genesys website and save the extracted data into a CSV file. The main script for this project is `web_scrap.ipynb`.

## Tools Used

- **Requests**: Employed to send HTTP requests to the Genesys customer stories page and fetch the HTML content.
- **BeautifulSoup**: Used to parse the fetched HTML content, allowing navigation and search within the HTML tree structure to extract relevant data.
- **Pandas**: Utilized to store and manipulate the extracted data, creating a DataFrame and saving it to a CSV file.
- **OpenAI**: The language model is used to fill in missing fields when the data cannot be directly extracted.

## How It Works
The Project is done within the Jupiter notebook, each line of code can be tested and view the result by running the cells.

1. **Install Dependencies**: The first cell installs the required libraries using `%pip install requests pandas BeautifulSoup openai`.

2. **Import Libraries**: The necessary libraries are imported, including `requests`, `BeautifulSoup`, `pandas`, `openai`, and `json`.

3. **Fetch Page Content**: The URL of the customer stories page is defined, and the page content is fetched using the `requests` library.

4. **Parse HTML Content**: The fetched HTML content is parsed using `BeautifulSoup`.

5. **Extract Story Links**: Customer story links are extracted from the parsed HTML content based on specific product criteria (i.e Genesys Cloud products). For that purpose the links are extracted only for '**`Genesys Cloud`**' and '**`Genesys Cloud ex`**' product categories.
The extracted links are then stored in the `story_links` variable.

6. **Extract Data from Each Story**: For each customer story link, the page content is fetched and parsed. Relevant details such as customer name, industry, location, partners, author name, and author designation are extracted. These details are stored in the `data` variable.

7. **Fallback to OpenAI**: If any fields are missing, the raw text content of the page is sent to the OpenAI GPT API to extract the missing data.Eventhough the use of AI can increase the latency for the generation of data, it is used here since in some cases where datasets are present but scattered through the story pages which is not possible to extract from HTML tree structure directly.

8. **Save Data to CSV**: The extracted data is stored in a Pandas DataFrame and saved to a CSV file named `customer_stories_data.csv`.

## Running the Script

To run the script, open the `web_scrap.ipynb` file in Jupyter Notebook or JupyterLab and execute the cells in order. The final output will be a CSV file containing the extracted customer stories data.

Note: Replace OpenAI_API_KEY with your openai api key in the code in order to process the fetching of missing datasets with AI.

## Conclusion

This project demonstrates how to use various tools and libraries to scrape and process web data. By leveraging, Requests, BeautifulSoup, Pandas, and OpenAI, we can efficiently extract and save structured data from a dynamic website. The extracted data is stored in the `data` variable and saved to a CSV file for further analysis.
