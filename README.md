# persian-gpt
This project is about text generation by gpt 2, which is used to produce poems from famous Iranian poets
ParsGPT 🦁



How to use
You can use this model directly with a pipeline for text generation:

Installing requirements
pip install -U transformers
pip install -U hazm
How to generate using pipeline
from transformers import pipeline
import hazm


normalizer = hazm.Normalizer(persian_numbers=False)

def normalize_input(text):
    text = normalizer.normalize(text)
    return text

def sents_as_output(text, num_sents=1):
    sents = hazm.sent_tokenize(text)
    if num_sents > 0:
        return " ".join(sents[:num_sents])
    return " ".join(sents[0])


generator = pipeline('text-generation', "HooshvareLab/gpt2-fa")
text = "در یک اتفاق شگفت انگیز، پژوهشگران"
text = normalize_input(text)


