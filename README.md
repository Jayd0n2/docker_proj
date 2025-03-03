<h1>📖 Translator Project</h1>

<h2>📝 Overview</h2>

This project provides an English-to-French translation pipeline using the Hugging Face transformers library. It runs in a Jupyter Notebook (Translator.ipynb) and processes .srt subtitle files to translate English captions into French.

<h2>✨ Features</h2>

- 🚀 Translates English text to French using the google-t5/t5-base model.

-📜 Supports subtitle translation from .srt files.

-📦 Containerized with Docker and Jupyter Notebook for easy deployment.

<h2>🔧 Prerequisites</h2>

Ensure you have the following installed:

- 🐳 Docker (if running in a containerized environment)

- 🐍 Python 3.x

<h2>📦 Required Python packages: </h2>

transformers

pysrt

<h2>⚙️ Installation</h2>

🚀 Running with Docker

Build the Docker container:

docker-compose up --build

Access the Jupyter Notebook by opening your browser and navigating to:

http://localhost:8000/?token=iambatman

🖥️ Running Locally (Without Docker)

Install dependencies:

pip install transformers pysrt

Open Jupyter Notebook:

jupyter notebook

Run Translator.ipynb to translate text or subtitle files.

🚀 Usage

🔡 Translate a Sentence

from transformers import pipeline
translator = pipeline("translation_en_to_fr")
result = translator("my name is Jaydon and I am a programmer")
print(result[0]['translation_text'])  # Output: "je m'appelle Jaydon et je suis programmeur."

<h2>📜 Translate Subtitle File (.srt)</h2>

import pysrt
subs = pysrt.open("captions_english.srt")

for i in subs:
    fr_text = translator(i.text)[0]['translation_text']
    i.text = fr_text

subs.save("captions_french.srt")

<h2>📂 Project Structure</h2>

.
├── 📒 Translator.ipynb       # Jupyter Notebook for translation
├── 📝 captions_english.srt   # Example subtitle file (input)
├── 📜 captions_french.srt    # Translated subtitle file (output)
├── 🐳 Dockerfile             # Docker setup
├── ⚙️ compose.yml            # Docker Compose configuration
└── 📖 README.md              # Project documentation

<h2>⚠️ Notes</h2>

The project defaults to using google-t5/t5-base. If deploying in production, explicitly specify the model and revision to avoid version mismatches.

Ensure captions_english.srt is available before running the script.
