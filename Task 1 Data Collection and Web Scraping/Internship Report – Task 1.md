Perfect 👍. I’ll structure your **internship report** in a clean format so you can submit it directly. I’ll keep it professional, clear, and easy to follow.

---

# **Internship Report – Task 1**

**Company:** Codveda Technologies
**Intern:** Emmanuel Umeogu
**Task Title:** Data Collection and Web Scraping

---

## **1. Introduction**

As part of my internship at Codveda Technologies, I was assigned **Task 1: Data Collection and Web Scraping**. The objective of this task was to collect structured data from a website using Python-based web scraping techniques.

The key goals included:

* Identifying a suitable website for scraping.
* Inspecting the HTML structure of the website.
* Using `requests` and `BeautifulSoup` libraries to extract data.
* Storing the scraped data in a structured format (CSV/JSON).
* Handling pagination to collect data across multiple pages.

For this task, I selected **Books to Scrape ([https://books.toscrape.com/](https://books.toscrape.com/))** – a publicly available practice website for web scraping, containing structured product listings.

---

## **2. Tools and Libraries**

* **Python 3**
* **Requests** – for sending HTTP requests.
* **BeautifulSoup (bs4)** – for parsing HTML and extracting data.
* **Pandas** – for structuring and exporting data into CSV format.

Installation (via terminal or Jupyter Notebook):

```bash
pip install requests beautifulsoup4 pandas
```

---

## **3. Methodology & Steps**

### **Step 1: Website Selection & Structure Analysis**

* Chosen website: **Books to Scrape**.
* Each product is contained in `<article class="product_pod">`.
* Extracted details:

  * Title → `<h3><a title="..."></a></h3>`
  * Price → `<p class="price_color">`
  * Availability → `<p class="instock availability">`

---

### **Step 2: Basic Scraping for One Page**

```python
import requests
from bs4 import BeautifulSoup
import pandas as pd

# Target URL
url = "https://books.toscrape.com/catalogue/page-1.html"

# Send request
response = requests.get(url)
soup = BeautifulSoup(response.text, "html.parser")

# Extract book data
books = []
for book in soup.find_all("article", class_="product_pod"):
    title = book.h3.a["title"]
    price = book.find("p", class_="price_color").text
    availability = book.find("p", class_="instock availability").text.strip()
    
    books.append({
        "Title": title,
        "Price": price,
        "Availability": availability
    })

# Convert to DataFrame
df = pd.DataFrame(books)

# Save to CSV
df.to_csv("books_page1.csv", index=False)

print("Scraping complete! Data saved to books_page1.csv")
```

---

### **Step 3: Handling Pagination (Multiple Pages)**

```python
all_books = []

# Loop through multiple pages
for page in range(1, 6):  # Scraping first 5 pages
    url = f"https://books.toscrape.com/catalogue/page-{page}.html"
    response = requests.get(url)
    soup = BeautifulSoup(response.text, "html.parser")

    for book in soup.find_all("article", class_="product_pod"):
        title = book.h3.a["title"]
        price = book.find("p", class_="price_color").text
        availability = book.find("p", class_="instock availability").text.strip()
        
        all_books.append({
            "Title": title,
            "Price": price,
            "Availability": availability
        })

# Save full dataset
df = pd.DataFrame(all_books)
df.to_csv("all_books.csv", index=False)

print("Scraping complete! Data saved to all_books.csv")
```

---

## **4. Results**

* The scraper successfully collected data from the first **5 pages** of the site.
* Extracted data fields:

  * **Book Title**
  * **Price**
  * **Availability**
* Data was saved in structured CSV format (`books_page1.csv` and `all_books.csv`).

**Sample Output (CSV):**

| Title                                 | Price  | Availability |
| ------------------------------------- | ------ | ------------ |
| A Light in the Attic                  | £51.77 | In stock     |
| Tipping the Velvet                    | £53.74 | In stock     |
| Soumission                            | £50.10 | In stock     |
| Sharp Objects                         | £47.82 | In stock     |
| Sapiens: A Brief History of Humankind | £54.23 | In stock     |

---

## **5. Challenges & Solutions**

* **Pagination:** Solved by looping through pages dynamically.
* **Whitespace in Availability:** Used `.strip()` to clean text.
* **Dynamic Content:** This project used a static site; for JavaScript-heavy sites, libraries like `selenium` or `requests_html` would be required.

---

## **6. Conclusion**

This task provided hands-on experience with **web scraping** using Python. I successfully extracted product data from a target website, structured it with Pandas, and stored it in CSV format. The techniques learned (requests, BeautifulSoup parsing, pagination handling) will serve as a foundation for more complex scraping tasks, including handling dynamic content and larger datasets.

---

Would you like me to also **format this report into a professional PDF** (with proper fonts and headings) so you can submit it neatly to Codveda?
