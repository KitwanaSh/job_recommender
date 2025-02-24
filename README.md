# AI-Powered Career Recommendation System

![Python Logo](https://en.m.wikipedia.org/wiki/File:Python-logo-notext.svg)
![Jupyter Notebook Logo](https://upload.wikimedia.org/wikipedia/commons/3/38/Jupyter_logo.svg)
![Anaconda Logo](https://searchvectorlogo.com/wp-content/uploads/2020/10/anaconda-inc-logo-vector.png)

This project implements an **AI-powered career recommendation system** that matches job seekers with relevant job postings based on their skills. The system uses **natural language processing (NLP)** and **cosine similarity** to analyze job descriptions and find the best matches for a user's skill set. It leverages job posting data collected from multiple countries using the **Adzuna Jobs API**.

---

## Table of Contents
1. [Project Overview](#project-overview)
2. [Features](#features)
3. [Data Collection](#data-collection)
4. [Technical Implementation](#technical-implementation)
5. [Skill Extraction](#skill-extraction)
6. [Recommendation System](#recommendation-system)
7. [Results](#results)
8. [Future Improvements](#future-improvements)
9. [Setup and Installation](#setup-and-installation)
10. [Contributing](#contributing)
11. [License](#license)

---

## Project Overview

The **AI-Powered Career Recommendation System** is designed to help job seekers find relevant job opportunities by matching their skills with job postings. The system:
- Collects job posting data from multiple countries using the **Adzuna Jobs API**.
- Extracts skills from job descriptions using **NLP techniques**.
- Builds a **skill-job matrix** to represent the relationship between jobs and skills.
- Recommends jobs based on **cosine similarity** between a user's skill set and job requirements.

This project demonstrates expertise in **data collection, NLP, machine learning, and recommendation systems**.

---

## Features

- **Data Collection**: Fetches job postings from multiple countries using the Adzuna API.
- **Skill Extraction**: Identifies relevant skills from job descriptions using **spaCy** and a custom skill keyword library.
- **Recommendation Engine**: Uses **cosine similarity** to match user skills with job requirements.
- **Scalable Design**: Handles large datasets efficiently using sparse matrices.
- **Customizable**: Allows users to adjust the number of recommendations and similarity thresholds.

---

## Data Collection

Job posting data is collected using the **Adzuna Jobs API**, which provides detailed information including:
- Job titles
- Descriptions
- Salary information
- Company details
- Location data
- Job categories

### Data Collection Process
1. **API Configuration**: The Adzuna API is accessed using an API ID and key stored in environment variables.
2. **Job Fetching**:
   - The `get_job_data()` function fetches a single page of job listings from a specific country.
   - The `fetch_all_jobs_from_all_countries()` function iterates through all countries and pages to collect job listings.
3. **Error Handling**: Includes robust error handling for failed API requests and rate limiting to avoid overloading the API.

---

## Technical Implementation

### Dependencies
The project uses the following Python libraries:
- `requests`: For API calls.
- `pandas` & `numpy`: For data manipulation.
- `spacy`: For natural language processing.
- `scikit-learn`: For text vectorization and similarity calculations.
- `matplotlib` & `seaborn`: For visualization.

### Skill Extraction Setup
- A comprehensive set of **skill keywords** is defined across multiple domains (e.g., Business, IT, Healthcare, Marketing).
- **spaCy** is used for advanced text processing, including:
  - Loading the English language model.
  - Creating a `PhraseMatcher` for efficient skill keyword matching.
  - Converting skill keywords into spaCy patterns.

---

## Skill Extraction

The `extract_skills()` function processes job descriptions to identify mentioned skills:
1. Converts text to lowercase for consistent matching.
2. Uses spaCy's `PhraseMatcher` to find skill keyword matches.
3. Returns unique skills found in each description.

This creates a **structured representation of skills** for each job posting, which is used to build the skill-job matrix.

---

## Recommendation System

The recommendation system works in several steps:

### 1. User Profile Creation
- Takes a list of user skills.
- Creates a binary vector matching the skill matrix format.

### 2. Similarity Calculation
- Uses **cosine similarity** to compare the user profile with job skill requirements.
- Handles both sparse and dense matrices efficiently.

### 3. Recommendation Generation
- Sorts jobs by similarity score.
- Returns the top N most relevant positions, including:
  - Job title
  - Category
  - Similarity score

---

## Results

The system successfully recommends jobs based on user skills, with the following outcomes:
- High accuracy in matching user skills with job requirements.
- Scalable design capable of handling large datasets.
- Customizable recommendations based on user preferences.

### Example Output
| Job Title            | Category          | Similarity Score |
|----------------------|-------------------|------------------|
| Data Scientist       | IT Jobs           | 0.95             |
| Marketing Manager    | Marketing Jobs    | 0.92             |
| Software Engineer    | Engineering Jobs  | 0.90             |

---

## Future Improvements

To enhance the system further, consider the following improvements:

### 1. **Expand Data Sources**
   - Incorporate job postings from additional platforms (e.g., LinkedIn, Indeed).
   - Collect more diverse data to improve recommendation accuracy.

### 2. **Build an Interactive Dashboard**
   - Create a user-friendly interface using **Streamlit** or **Dash**.
   - Allow users to input skills, view recommendations, and explore job details.

### 3. **Try Different Models**
   - Experiment with advanced recommendation algorithms:
     - **Collaborative Filtering**: Recommend jobs based on what similar users have chosen.
     - **Hybrid Models**: Combine content-based and collaborative filtering for better recommendations.
   - Use **deep learning models** (e.g., neural networks) for skill extraction and matching.

### 4. **Add Additional Features**
   - Include **salary predictions** based on job trends.
   - Provide **skill gap analysis** to help users identify areas for improvement.
   - Add **geographic filters** to recommend jobs in specific locations.

### 5. **Improve Skill Extraction**
   - Use **pre-trained language models** (e.g., BERT) for more accurate skill extraction.
   - Expand the skill keyword library to cover more domains and emerging skills.

---

## Setup and Installation

### Prerequisites
- Python 3.8+
- Adzuna API ID and key (stored in environment variables).

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/KitwanaSh/job_recommender.git
   cd __job_recommender__
   ```
2. Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```
3. Download the spaCy English model:
    ```bash
    python -m spacy download en_core_web_sm
    ```
### Contributing
Contributions are welcome! If you'd like to contribute, please:
1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Submit a pull request with a detailed description of your changes.

### License
This project is licensed under the MIT License. See the LICENSE file for details.

### Acknowledgments
- Adzuna for providing the job posting data.
- spaCy and scikit-learn for their powerful NLP and machine learning tools.
- The open-source community for their contributions to Python libraries.