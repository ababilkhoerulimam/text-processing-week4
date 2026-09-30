<div align="center">
  <h1>text-processing-week4</h1>
  <p><strong>Hacker News Web Scraping and Text Preprocessing Pipeline</strong></p>

  <p align="center">
    <img src="https://img.shields.io/badge/Course-Text_Processing-blue?style=flat-square" alt="Course">
    <img src="https://img.shields.io/badge/Language-Python_3.11-3776AB?style=flat-square&logo=python&logoColor=white" alt="Language">
    <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="License">
    <img src="https://img.shields.io/badge/Status-Completed-success?style=flat-square" alt="Status">
  </p>

  <p align="center">
    Practical implementation of multi-source web scraping (HTML parsing and Firebase REST API) followed by a sequential natural language text preprocessing pipeline on Hacker News article titles.
  </p>
</div>

## Tech Stack

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black)
![Markdown](https://img.shields.io/badge/markdown-%23000000.svg?style=for-the-badge&logo=markdown&logoColor=white)
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)

## Project Overview

This repository contains the coursework implementation for Text Processing Week 4 (Exercise 3 and Exercise 4). The project demonstrates data acquisition from Hacker News using two distinct collection strategies, followed by an end-to-end natural language preprocessing workflow.

### Team Members
- Ababil Khoerul Imam (NIM 152)
- Bethania Putri Junjungsari Nugraha (NIM 115)

Data Science Study Program, Faculty of Mathematics and Natural Sciences, Universitas Negeri Surabaya.

## Repository Structure

```text
text-processing-week4/
├── ababil bethania_exercise 4.ipynb  # Primary notebook containing scraping and preprocessing workflows
├── hackernews_stories.csv            # Structured dataset of 30 top stories acquired via Firebase API
├── hackernews_preprocessed.csv       # Cleaned dataset with original and preprocessed article titles
├── LICENSE                           # MIT License
└── README.md                         # Project documentation
```

## Workflow and Methodology

### 1. Web Scraping (Exercise 3)

The data ingestion stage evaluates two collection approaches against Hacker News (`https://news.ycombinator.com/`):

1. **HTTP Request and HTML Parsing**: Direct GET request to the front page using `requests`, parsed via `BeautifulSoup`. Extracts story ID, title, URL from `.athing` elements, along with upvotes and authors from `.subtext` rows.
2. **Official Firebase REST API**: Programmatic retrieval from `https://hacker-news.firebaseio.com/v0/`. Fetches IDs from `topstories.json` and details for the top 30 stories from `item/{id}.json`. Delivers structured numeric metrics and UNIX timestamps without CSS fragility.
3. **Exploratory Data Analysis**: Evaluates score and comment distributions, identifies prolific submitters, and visualizes the top 10 stories by upvote score. Raw API records are saved to `hackernews_stories.csv`.

### 2. Text Preprocessing (Exercise 4)

The text cleaning pipeline processes the `title` field through ten ordered transformation steps:

1. **HTML Removal**: Strips markup tags using regex matching (`<.*?>`).
2. **Hashtag Removal**: Removes social hashtag identifiers (`#\w+`).
3. **Case Folding**: Converts all characters to standard lowercase format.
4. **URL and Email Sanitization**: Strips web links (`https?://\S+|www\.\S+`) and email addresses (`\S+@\S+`).
5. **Punctuation and Symbol Filtering**: Strips standard ASCII symbols and Unicode punctuation variants (including en-dashes, em-dashes, and typographical quotation marks).
6. **Emoji Removal**: Strips unicode graphical emojis using the `demoji` library.
7. **Tokenization**: Splits normalized sentences into individual lexical tokens using `nltk.word_tokenize`.
8. **Stopword Filtering**: Excludes low-information English tokens using the NLTK English stopword lexicon.
9. **Stemming**: Normalizes word forms to morphological roots using the Porter Stemmer algorithm (`PorterStemmer`).
10. **Reconstruction**: Joins cleaned tokens into whitespace-delimited strings for downstream text modeling and exports the result to `hackernews_preprocessed.csv`.

## Getting Started

### Prerequisites

Ensure Python 3.10+ is installed. Required libraries:

```bash
pip install requests beautifulsoup4 pandas matplotlib demoji nltk
```

### Running the Notebook

Clone the repository and launch Jupyter Notebook or Google Colab:

```bash
git clone https://github.com/ababilkhoerulimam/text-processing-week4.git
cd text-processing-week4
jupyter notebook "ababil bethania_exercise 4.ipynb"
```

The notebook automatically handles necessary NLTK resource downloads (`punkt`, `punkt_tab`, and `stopwords`) during execution.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
