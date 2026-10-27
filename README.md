# ContentLens AI — YouTube & Website Summarizer

ContentLens AI is an LLM-powered application that summarizes YouTube videos and website content into five concise bullet points. It extracts available video transcripts or webpage text and uses a Groq-hosted language model with LangChain summarization components to generate readable summaries.

## Features

- **YouTube Summarization:** Retrieves available English transcripts from supported YouTube videos.
- **Website Summarization:** Extracts text from supported website URLs.
- **LLM-Powered Summaries:** Converts extracted content into five concise bullet points.
- **Prompt Engineering:** Uses a custom prompt to guide summary structure, conciseness, and source-grounded responses.
- **URL Validation:** Checks whether the provided input is a valid URL.
- **Input and Error Handling:** Handles missing or unreadable content and reports application errors.
- **Interactive Interface:** Provides a simple web interface using Streamlit.

## Tech Stack

- **Language:** Python
- **LLM Integration:** Groq
- **LLM Framework:** LangChain
- **Model:** `openai/gpt-oss-120b` via Groq
- **Document Loaders:** LangChain YouTube and unstructured URL loaders
- **Frontend:** Streamlit
- **Validation:** `validators`

## How It Works

1. The user enters a YouTube video URL or a website URL.
2. The application validates the URL and identifies the content source.
3. For YouTube videos, it attempts to retrieve the available English transcript. For websites, it extracts page content using the URL loader.
4. LangChain's summarization chain passes the extracted content to the configured language model.
5. The model generates a summary in five concise bullet points, which is displayed in the Streamlit application.

## Project Structure

```text
ContentLens-AI/
├── app.py
├── requirements.txt
├── .env.example
└── README.md
```

*Adjust the project structure above to match the actual files in your repository.*

## Getting Started

### Prerequisites

- Python 3.10 or a compatible version supported by your dependencies
- A Groq API key
- Internet access to retrieve supported YouTube transcripts and webpage content

### 1. Clone the Repository

```bash
git clone <YOUR_REPOSITORY_URL>
cd ContentLens-AI
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

Activate it:

**Windows**
```bash
venv\Scripts\activate
```

**macOS / Linux**
```bash
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure Your Groq API Key

Run the application and enter your Groq API key in the provided input field. If you later switch to environment-variable configuration, document the required variable in your `.env.example`.

**Security note:** Never commit API keys or other secrets to GitHub.

### 5. Run the Application

```bash
streamlit run app.py
```

Open the local URL displayed in the terminal.

## Example Prompt

The application uses a prompt along these lines:

> Summarize the content below in five concise bullet points. Use only facts from the content. If it is too short or unrelated, say so briefly.

The prompt helps guide the output format and encourages the model to stay grounded in the extracted content. It does not guarantee that every generated statement will be factually correct.

## Use Cases

- Quickly reviewing the main points of YouTube videos.
- Extracting key information from online articles and webpages.
- Supporting research and learning workflows.
- Exploring LLM-based text summarization and document-loading pipelines.

## Limitations

- YouTube summarization depends on transcript availability and supported languages.
- Some websites block automated content extraction or require JavaScript rendering.
- Very long content may exceed the model's context limits because the current implementation uses a `stuff` summarization chain.
- Generated summaries may omit important details or contain inaccuracies and should be checked against the source.

## Future Improvements

- Add support for longer documents through map-reduce or refine summarization strategies.
- Allow users to choose summary length and output format.
- Add source references or timestamps to help users verify important claims.
- Add automated tests for URL validation, content extraction, and summarization.
- Improve handling of rate limits, unavailable transcripts, and model errors.

## Learning Outcomes

This project explores LLM-powered summarization, prompt engineering, document loaders, LangChain chains, external model APIs, URL validation, and Streamlit application development.

## Author

**Arun Arumugam**

Aspiring AI/ML Engineer | Python | Machine Learning | Generative AI | LLM Applications
