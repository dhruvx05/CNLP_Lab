# Experiment 5: Subword Tokenization and POS Tagging

**Name:** Aantriksh Sood  
**SAP ID:** 500124259  

## Objective
To implement advanced subword-level tokenization utilizing BPE and SentencePiece architectures, and to perform Part-of-Speech (POS) tagging for linguistic syntax analysis using NLP toolkits.

## Procedure & Implementation
This experiment focuses on breaking down texts into subword units and categorizing tokens by their grammatical roles.

1.  **BPE Tokenization (`5.1`):**
    *   **Pretrained:** Loading a GPT-2 tokenizer <sup>(`GPT2Tokenizer.from_pretrained()`)</sup> to encode and convert sample text into subword identifiers and tokens <sup>(`encode()`, `convert_ids_to_tokens()`)</sup>.
    *   **From Scratch:** Instantiating a native tokenizer <sup>(`Tokenizer(BPE())`)</sup>, applying whitespace pre-tokenization <sup>(`Whitespace()`)</sup>, and training it on the provided text file <sup>(`BpeTrainer()`, `train()`)</sup>.

2.  **SentencePiece Tokenization (`5.2`):**
    *   **Pretrained:** Utilizing a T5 tokenizer <sup>(`T5Tokenizer.from_pretrained()`)</sup> to segment the text into SentencePiece subword elements <sup>(`encode()`, `convert_ids_to_tokens()`)</sup>.
    *   **From Scratch:** Training a native SentencePiece model directly on the raw text file <sup>(`spm.SentencePieceTrainer.train()`)</sup> and encoding the string via the trained processor <sup>(`spm.SentencePieceProcessor()`, `encode_as_pieces()`)</sup>.

3.  **Part-of-Speech Tagging on Short Text (`5.3`):**
    *   **spaCy:** Processing the sentence through the `en_core_web_sm` pipeline <sup>(`nlp(sentence)`)</sup> and iterating over tokens to extract and explain their POS tags <sup>(`token.pos_`, `spacy.explain()`)</sup>.
    *   **NLTK:** Utilizing NLTK's standard word tokenizer <sup>(`nltk.word_tokenize()`)</sup> followed by the perceptron tagger <sup>(`nltk.pos_tag()`)</sup> to identify part-of-speech roles.

4.  **POS Tagging with Frequency Analysis (`5.4`):**
    *   Parsing a large unstructured text file via the spaCy pipeline <sup>(`nlp(text)`)</sup>.
    *   Aggregating POS tag frequencies alongside the tokens themselves utilizing standard collection modules <sup>(`Counter()`)</sup>.
    *   Extracting the most prominent syntactical elements <sup>(`most_common(20)`)</sup>.

## Observations
| Analysis Task | Key Observation Parameter | Visualization/Method |
| :--- | :--- | :--- |
| **Pretrained BPE** | Subword token granularity | `GPT2Tokenizer` output ids/tokens |
| **Native BPE** | Custom vocabulary induction | `tokenizers.BPE` trainer output |
| **SentencePiece** | Language-agnostic string tokenization | `spm.SentencePieceProcessor` output |
| **POS Tagging (Short)** | Grammatical categorization of individual words | `spaCy` & `NLTK` tag sets |
| **POS Tagging (Large)** | Distribution of syntactical classes across a corpus | Frequency counting (`Counter`) |

## Result Interpretation & Learnings
*   **Subword Granularity:** Subword tokenization (BPE/SentencePiece) effectively resolves out-of-vocabulary (OOV) issues by breaking down rare words into frequent character sub-sequences, striking a balance between character-level and word-level tokenization.
*   **Pretrained vs. Custom Models:** While pretrained tokenizers rely on massive, generalized vocabularies (e.g., GPT-2, T5), custom tokenizers induce a vocabulary specifically tailored to the nuances of the training corpus.
*   **Syntactical Analysis:** POS tagging accurately classifies words according to their contextual grammatical roles (noun, verb, adjective), which is a prerequisite for downstream tasks like syntactic parsing or named entity recognition.
*   **Toolkit Discrepancies:** Different NLP toolkits (spaCy vs. NLTK) may employ divergent tag sets and underlying models (statistical vs. rule-based) resulting in slightly varied POS classifications for identical text.
