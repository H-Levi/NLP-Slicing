# NLP Second Assignment
## Text Processing, Slicing and Model Interaction
> Slicing algorithm for large context windows in ChatGPT 3.5. 

## Content

- [Overview](#overview)
- [Data Extraction](#data-extraction)
- [Slicing Algorithm](#slicing-algorithm)
- [Text Preprocessing](#text-preprocessing)
- [Cosine Similarity Check](#cosine-similarity-check)
- [Slice Efficiency Test](#slice-efficiency-test)
- [LLMA Model Interaction](#llma-model-interaction)
- [Files Used](#files-used)

---

## Overview

> This project decelops a slicing algorithm for handling large context windows for ChatGPT 3.5. It satrts by scraping medical content from Wikipedia, cleaning, and preprocessing the text. The algorithm ensures efficient slicing by considering both cosine similarity checks and window size limits. The resulting sliced data is then used to interact with an LLM Model.

## Data Extraction

- Identify the subject of interest, focusing on 'Medical Science' for data extraction.
- Use Wikipedia API to search and retrieve comprehensive information related to the chosen medical topic.
- Implement measures to restrict the dataset size, ensuring efficient processing and storage.
- Save the extracted content in a structured JSON file for subsequent analysis and utilization.
- clean the extracted data, eliminated unnecessary elements and saved the cleaned content in a text file.


## Slicing Algorithm

- Break down the input text into sentences using NLTK's sentence tokenizer.
- Create slices within a specified size limit, utilizing an iterative approach to concatenate sentences.
- Assess the cosine similarity between the current slice and previous slices after preprocessing.
- Ensure the new slice is not too similar to any of the existing slices before appending to the list.
- Obtain a list of unpreprocessed slices that meet the size criteria and minimize redundancy through similarity checks.

---

## Text Preprocessing

- Eliminate special characters, preserving hashtags and mentions.
- Employ NLTK's tokenizer to break down the text into words.
- Convert all words to lowercase for consistency.
- Exclude common English stopwords to focus on meaningful words.
- Apply WordNetLemmatizer to reduce words to their base form.

## Cosine Similarity Check

- Transform text slices into TF-IDF (Term Frequency-Inverse Document Frequency) vectors.
- Compute the cosine similarity between the vectors to measure their similarity.
- Compare the similarity score against a specified threshold (default is 0.7).
- Determine if the slices are similar enough based on the threshold.

## Slice Efficiency Test

- Join text slices to reconstruct the original text and writes it to a specified output file.
- Calculates the similarity between the original and regenerated texts using cosine similarity.
- The calculated similarity score and additional information about the text sizes and word counts are printed for evaluation.

## LLMA Model Interaction

- Initialize the Replicate client using the provided API token and defines the LLM model named "meta/llama-2-70b-chat."
- Read text slices from 'slices.txt' and stream them to the model as initial input.
- Prompt the user to input questions, and continue to interact with the model based on the stored input, providing answers to user questions.

## Files Used

- Files within this project are dynamically generated during code execution.
- medical_data_2MB.json: Original JSON file containing medical information collected from Wikipedia.
- cleaned_medical_data.txt: Cleaned version of medical_data_2MB.json, obtained through text preprocessing.
- regenerated_medical_data.txt: Text file constructed by reattaching text slices for efficiency evaluation.
- slices.txt: Text file containing all prepared slices, ready for interaction with the LLM model.


[back to top](#content)
