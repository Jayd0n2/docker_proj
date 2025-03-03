English to French Subtitle Translator

This project demonstrates how to use the Hugging Face transformers library to translate English text into French. It includes a script that translates subtitles from an English .srt file into French.

Features

Uses the transformers library with the pipeline function for translation.

Translates English text into French using the default google-t5/t5-base model.

Reads English subtitles from an .srt file, translates them, and saves the translated content into a new .srt file.

Requirements

Make sure you have the following dependencies installed:

pip install transformers pysrt torch tensorflow

Usage

Basic Translation

To perform a simple translation of a sentence:

from transformers import pipeline

translator = pipeline("translation_en_to_fr")
fr = translator("my name is Jaydon and I am a programmer")
print(fr[0]['translation_text'])  # Output: "je m'appelle Jaydon et je suis programmeur."

Translating Subtitle Files

To translate an English .srt subtitle file into French:

import pysrt
from transformers import pipeline

# Load translation model
translator = pipeline("translation_en_to_fr")

# Open subtitle file
subs = pysrt.open("captions_english.srt")

# Translate each subtitle line
for i in subs:
    fr_text = translator(i.text)[0]['translation_text']
    i.text = fr_text

# Save the translated subtitles
subs.save("captions_french.srt")

Notes

The script uses the google-t5/t5-base model by default. You can specify another model explicitly if needed.

Running the script for large subtitle files may take some time depending on your system’s performance.

Using a preloaded model for translation in production is recommended to avoid repeated downloads.


