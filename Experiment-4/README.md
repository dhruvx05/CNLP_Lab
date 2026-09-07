# Experiment 4: Term Frequency and Named Entity Recognition

**Name:** Aantriksh Sood  
**SAP ID:** 500124259  

## Objective
To implement and analyze Term-Frequency (TF), Inverse Document Frequency (IDF), and Named Entity Recognition (NER) algorithms on textual data, exploring both toolkit-based and foundational from-scratch approaches.

## Procedure & Implementation
This experiment involves multiple phases to compute term frequencies and significance across documents:

1.  **Toolkit-based TF & NER (`4.1`):**
    *   Processing the dataset (`4.1_4.2_input.txt`) utilizing an NLP toolkit <sup>(`spacy.load()`, `nlp(text)`)</sup>.
    *   Extracting term frequencies and named entities <sup>(`Counter()`, `doc.ents`)</sup>.
    *   Identifying the top 10 most frequent terms <sup>(`Counter.most_common(10)`)</sup>.
    *   Exporting the full frequency distribution to a CSV file <sup>(`pd.DataFrame().to_csv()`)</sup>.

2.  **Native Term-Frequency Analysis (`4.2`):**
    *   Executing the same TF calculation on `4.1_4.2_input.txt` strictly using native Python structures (without NLP libraries) <sup>(`dict`, `str.split()`)</sup>.
    *   Isolating the top 10 terms natively <sup>(`sorted(dict.items(), key=lambda x: x[1], reverse=True)`)</sup>.
    *   Saving the resulting `(Term, Frequency)` pairings into a CSV formatted file <sup>(`csv.writer()`)</sup>.

3.  **Native TF-IDF Computation (`4.3`):**
    *   Processing multiple sample documents purely through Python <sup>(`list` of strings)</sup>.
    *   Executing fundamental text preprocessing: lowercasing, punctuation removal, and tokenization <sup>(`str.lower()`, `str.translate()`)</sup>.
    *   Calculating Term Frequency (TF) for each term per document <sup>(`dict`)</sup>.
    *   Computing Document Frequency (DF) across the document corpus <sup>(`set()` for unique terms)</sup>.
    *   Deriving Inverse Document Frequency (IDF) utilizing the logarithmic formula <sup>(`math.log(total_docs / freq)`)</sup>.
    *   Computing the final TF-IDF scores for every term in every document.
    *   Extracting and displaying the top 10 terms with the highest TF-IDF scores for each document.

## Observations
| Analysis Task | Key Observation Parameter | Visualization/Method |
| :--- | :--- | :--- |
| **Toolkit TF & NER** | Entity identification and overall word counts | NLP Library & CSV Export |
| **Native TF Analysis**| Word frequency without specialized libraries | Native Python dicts & CSV Export |
| **TF-IDF Pipeline** | Term significance relative to document corpus | Custom Mathematical Functions (TF, DF, IDF) |
| **Top 10 Terms** | Extraction of highest scoring/frequency elements | Sorting/Ranking Algorithms |

## Result Interpretation & Learnings
*   **Algorithmic Proficiency:** The experiment develops a deep understanding of core statistical NLP algorithms by implementing them from the ground up natively in Python.
*   **Library Validation:** Comparing toolkit-generated results against native implementations solidifies trust and understanding in how high-level NLP libraries operate under the hood.
*   **Information Retrieval Mechanics:** The native TF-IDF implementation clearly illustrates how rare, highly descriptive words receive higher significance scores compared to common vocabulary.
*   **Statistical Representation:** Saving output data formats into structured tabular forms (CSV) bridges the gap between unstructured text and structured dataset analysis.
