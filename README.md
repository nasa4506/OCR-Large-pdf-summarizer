# OCR-Large-pdf-summarizer
This app allows users to upload scanned PDFs, extract text using OCR, summarize the extracted content using LLaMA 3 from Ollama, and download a clean, styled PDF containing the summaries.

Key Features:

EasyOCR + OpenCV-based OCR pipeline

Parallel processing for speed

Local LLM-based summarization (LLaMA 3)

Custom summarization prompt

Structured HTML -> PDF export via WeasyPrint

🔍 How It Works

1. Upload and Prompt

Upload any scanned PDF

Input a custom prompt that defines how the summary should be structured (HTML format supported)

2. Image Preprocessing

Pages are rendered as high-resolution images

Grayscale conversion, Gaussian blurring, and adaptive thresholding applied for better OCR quality

3. EasyOCR for Text Extraction

Each preprocessed page image is passed to EasyOCR

Uses paragraph=True for grouped text output

Output is saved for each page and stitched together

4. Ollama + LLaMA 3 Summarization

Raw OCR text is split into 4000-character chunks

Each chunk is passed to LLaMA 3 via ollama.chat() with the user's custom prompt

Structured summaries are stored and displayed

5. HTML to PDF Export

Summaries are embedded in semantic HTML (headings, lists, tables)

Rendered and saved as PDF via WeasyPrint

✅ Why It's Better

Feature

This App

Traditional Approach

OCR Quality

EasyOCR + OpenCV

Plain Tesseract

Speed

Threaded OCR pipeline

Serial OCR

Summarization

Local LLM (LLaMA 3)

None or remote API

Output Format

Styled PDF via HTML

Plain text or markdown

Custom Prompt

Fully user-configurable prompt

Hardcoded logic

🧰 Tech Stack

OCR: EasyOCR

Preprocessing: OpenCV

PDF Handling: PyMuPDF (fitz)

Summarization: Ollama (LLaMA 3.1 8B)

UI: Streamlit

Export: WeasyPrint (HTML → PDF)

📆 Installation

# Clone the repo
https://github.com/yourusername/pdf-ocr-summarizer.git
cd pdf-ocr-summarizer

# Create virtual environment
python -m venv venv
venv\Scripts\activate  # On Windows

# Install dependencies
pip install -r requirements.txt

# Start Ollama in a separate terminal
ollama run llama3

# Run the Streamlit app
streamlit run project.py

📂 File Structure

.
├── project.py                 # Main Streamlit App
├── requirements.txt           # All dependencies
└── README.md                  # This file

🧲 Future Enhancements

Multilingual OCR support

Table detection and extraction

Dynamic prompt suggestions

Interactive document preview

Caching and document versioning

✍️ License

MIT License. Feel free to use, modify, and contribute.
