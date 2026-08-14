# NAL Pipeline Prototype

A lightweight web interface for running the NAL literature relevance screening pipeline.

The prototype allows a user to enter a research question, upload a CSV containing article titles and abstracts, and download a CSV containing model-generated relevance scores.

## How It Works

1. Enter a research question.
2. Upload a CSV file containing:
   - `Title`
   - `Abstract Note`
3. Click **Run**.
4. The application evaluates each article against the research question.
5. Download the resulting CSV with an additional `Relevance_Score` column.

## Relevance Scoring

Each document is assigned an integer relevance score from 0–3:

- **0** — Not related to the research question
- **1** — Related, but does not directly address the question
- **2** — Contains important information related to the question
- **3** — Entirely and specifically about the question

## Implementation

The prototype uses:

- Python
- FastAPI
- pandas
- OpenAI API
- Parallel API requests with rate limiting
- Render for web deployment

The current implementation uses `gpt-5-mini` for relevance scoring.

## Running Locally

Install the required dependencies:

    pip install -r requirements.txt

Set your OpenAI API key as an environment variable:

    OPENAI_API_KEY=your_api_key

Start the application:

    uvicorn app:app --reload

Then open the local URL shown by Uvicorn in your browser.

## Input Format

The uploaded CSV must contain the following columns:

    Title
    Abstract Note

Other columns in the uploaded CSV are preserved in the output.

## Output

The downloaded CSV contains the original input data plus:

    Relevance_Score

## Status

This is an early prototype developed to demonstrate a standalone web interface for the NAL literature screening pipeline and provide greater control over model selection, prompting, and pipeline behavior.

## License

This project is licensed under the MIT License.
