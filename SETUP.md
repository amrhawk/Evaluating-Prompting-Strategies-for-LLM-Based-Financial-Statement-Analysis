# Setup

## Requirements
- Python 3.11+
- Gemini API key: https://aistudio.google.com/apikey

## 1. Get the project

```bash
unzip financial-statement-llm-analyzer.zip
cd financial-statement-llm-analyzer
```

Or:

```bash
git clone <repo-url>
cd financial-statement-llm-analyzer
```

## 2. Install dependencies

```bash
python3 -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## 3. Configure the API key

```bash
cp .env.example .env               # Windows: copy .env.example .env
```

Edit `.env`:

```
GEMINI_API_KEY=your-key-here
GEMINI_MODEL=gemini-3.5-flash-lite
```

## 4. Dataset (optional)

The evaluation dataset and extracted text are already included. Only needed to
restore source PDFs or rebuild from scratch:

```bash
git clone --depth 1 https://github.com/patronus-ai/financebench.git
python scripts/build_ground_truth.py
```

## 5. Run the app

```bash
streamlit run app.py
```

Opens at http://localhost:8501

## 6. Reproduce the results

```bash
python scripts/run_experiments.py     # 20 statements x 4 strategies
python scripts/execute_notebook.py    # charts + analysis notebook
```

Results are written to `outputs/`.
