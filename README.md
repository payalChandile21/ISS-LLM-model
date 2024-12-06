
# ISS-LLM-Model

## Overview

The **ISS-LLM-Model** project is focused on integrating **Large Language Models (LLMs)** with AI and machine learning techniques to address specific use cases within the **International Space Station (ISS)** domain. The project leverages **NASA's real-time APIs** and web scraping of NASA data to provide accurate, up-to-date insights into ISS operations, research, and missions. 

By combining NASA's vast data resources with the power of LLMs like GPT-4, this project aims to improve **mission efficiency**, provide intelligent assistance, and enhance decision-making processes.

## Project Goals

- Develop an AI-powered assistant for real-time insights into ISS missions and operations.
- Integrate **NASA APIs** for fetching live data such as current ISS location, telemetry, and space research updates.
- Utilize web scraping to collect additional data from NASA's public websites, including mission logs, research papers, and announcements.
- Implement **Large Language Models** to process and interpret this data for human-readable outputs and actionable insights.

## Features

- **Real-Time Data Access**:
  - Fetch live ISS telemetry and positional data using NASA's APIs.
  - Provide updates on ongoing ISS experiments and research.
- **Document Processing**:
  - Summarize NASA research papers and mission updates.
- **Data Enrichment**:
  - Extract supplementary information via web scraping from NASA’s public resources.
- **AI-Powered Insights**:
  - Use GPT-4 to answer complex queries, analyze mission logs, and provide actionable recommendations.

## Technologies Used

- **Large Language Models (LLM)**: OpenAI GPT-4 (or other available models).
- **NASA APIs**: For real-time ISS data and other space-related information.
- **Web Scraping**: Python libraries like `BeautifulSoup` and `Scrapy` for extracting data from NASA's public websites.
- **Python**: Core language for API interaction, data processing, and model integration.
- **FAISS**: For efficient similarity search and embeddings indexing.

## NASA API Integration

The project integrates the following NASA APIs:
- **NASA’s ISS Current Location API**: Provides real-time geographic coordinates of the ISS.
- **NASA Open APIs**: Offers data on upcoming missions, satellite imagery, space weather, and more.

### Example Usage

1. Fetch ISS location:
   ```python
   import requests

   response = requests.get("http://api.open-notify.org/iss-now.json")
   data = response.json()
   print(f"ISS is currently at latitude {data['iss_position']['latitude']} and longitude {data['iss_position']['longitude']}.")
   ```

2. Fetch data from NASA's Mars Rover Photos API:
   ```python
   API_KEY = "your_nasa_api_key"
   response = requests.get(f"https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&api_key={API_KEY}")
   photos = response.json()
   print(f"Found {len(photos['photos'])} Mars rover photos.")
   ```

## Web Scraping NASA Data

To collect additional information not covered by APIs, the project uses web scraping. For instance:
- **Mission Logs**: Scraped from NASA's mission overview pages.
- **Research Papers**: Extracted from NASA's public research repositories.

### Example Code

1. Scraping mission details:
   ```python
   from bs4 import BeautifulSoup
   import requests

   url = "https://www.nasa.gov/missions"
   response = requests.get(url)
   soup = BeautifulSoup(response.text, 'html.parser')

   missions = soup.find_all('div', class_='mission-title')
   for mission in missions:
       print(mission.text.strip())
   ```

2. Scraping research data:
   ```python
   url = "https://ntrs.nasa.gov/"
   response = requests.get(url)
   soup = BeautifulSoup(response.text, 'html.parser')

   papers = soup.find_all('a', class_='paper-title')
   for paper in papers[:5]:
       print(paper.text.strip())
   ```

## Setup and Installation

### Prerequisites

1. Python 3.7 or higher
2. OpenAI API key (for GPT-4 access)
3. NASA API key (sign up at [NASA Open APIs](https://api.nasa.gov/))
4. Required Python libraries:
   - `openai`
   - `requests`
   - `beautifulsoup4`
   - `faiss-cpu`
   - `numpy`
   - `pandas`

### Steps

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/ISS-LLM-Model.git
   ```

2. Install the required Python dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Set up your **OpenAI** and **NASA API keys**:
   - Obtain API keys and add them to a `.env` file or pass them directly in the code.

4. Run the application:
   ```bash
   python main.py
   ```

5. Start interacting with real-time data and AI-powered insights.

## Project Structure

```
ISS-LLM-Model/
│
├── data/                # Store documents, mission logs, research papers
├── models/              # Pre-trained models and fine-tuned weights
├── src/                 # Source code for API integration, scraping, and model inference
├── main.py              # Main script for running the application
├── requirements.txt     # List of dependencies
├── README.md            # Project documentation
└── config/              # Configuration files (API keys, model settings)
```

## Example Usage

1. Query the model:
   ```python
   from model import query_model

   response = query_model("What are the ongoing experiments on the ISS?")
   print(response)
   ```

2. Fetch and summarize scraped data:
   ```python
   from scraper import fetch_mission_logs

   logs = fetch_mission_logs()
   for log in logs:
       print(log)
   ```

## Contributing

We welcome contributions to the ISS-LLM-Model project. Here are a few ways you can help:

1. Fork the repository and submit a pull request.
2. Report any bugs or issues.
3. Suggest features or improvements.

## Acknowledgments

- OpenAI for GPT-4 API.
- NASA for providing access to their APIs and data resources.
- FAISS for fast similarity search.
- BeautifulSoup and Scrapy for web scraping utilities.
