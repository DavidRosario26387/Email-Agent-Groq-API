# 📧 AI LLM-based Cold Email Agent using Groq API

This project is a LangChain-powered Cold Email Generator that scrapes job postings from company career pages and crafts personalized cold emails using **LLM inference via the Groq API**. It's built with modularity in mind and uses `Streamlit` for a clean user interface.

## Features

- Extracts job data (`role`, `experience`, `skills`, `description`) from career page text.
- Generates context-aware cold emails using **Llama3-70B** model via **Groq API**.
- Matches job-required skills with your project portfolio to tailor each email.
- Fully interactive Streamlit web app.
- Built-in HTML cleaning, vector storage for portfolio links (via ChromaDB), and modular code.

---

## 📁 Project Structure

```bash
.
├── chains.py            # Core LLM pipeline (job extraction & email writing)
├── main.py              # Streamlit frontend for the email agent
├── portfolio.py         # Loads and matches portfolio projects based on job skills
├── utils.py             # Text cleaning utilities
├── resources/
│   └── my_portfolio.csv # Portfolio dataset (projects & tech stack)
├── vectorstore/         # ChromaDB persistent vector store
├── requirements.txt     # Dependencies
```

## ⚙️ How It Works
1. Scrape & Clean Webpage
A career/job posting page is loaded using WebBaseLoader.

Raw text is cleaned to remove HTML, URLs, and noise via clean_text().

2. Extract Job Descriptions
LangChain + Groq's Llama3 model parses the cleaned text to extract structured job postings.

Returns structured JSON with role, experience, skills, description.

3. Portfolio Matching
Each job's required skills are matched against a portfolio CSV.

ChromaDB is used for semantic retrieval of the most relevant project links.

4. Email Generation
LLM generates a professional cold email.

Emails reference relevant portfolio projects and are designed for maximum personalization.

Launch the app with:
```
streamlit run main.py
```
Input: A URL to a job posting

Output: Tailored cold email(s) for each detected role

## 📦 Setup & Installation
1. Clone the Repo
```
git clone https://github.com/DavidRosario26387/Email-Agent-Groq-API.git
cd Email-Agent-Groq-API
```
3. Install Dependencies
```
pip install -r requirements.txt
```
4. Add Environment Variables
Create a .env file in the root directory:
```
GROQ_API_KEY=your_groq_api_key_here
```
4. Prepare Portfolio
Ensure resources/my_portfolio.csv exists with the following format:
```
Techstack,Links
AI,https://yourproject.com/ai-solution
Web Development,https://yourproject.com/web-platform
...
```

<img width="841" height="835" alt="image" src="https://github.com/user-attachments/assets/20d99c03-f501-4a8c-bebf-447c0c506148" />
