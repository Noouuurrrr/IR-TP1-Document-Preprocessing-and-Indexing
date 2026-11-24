# IR-TP1-Document-Preprocessing-and-Indexing

## How to Run the Notebook
1. Open `tpl_preprocessing_indexing.ipynb` in Google Colab or Jupyter Notebook.
2. Run all cells sequentially (`Runtime -> Run all` in Colab).
3. Inspect the generated outputs inside the `results/` directory.

## Implementation Choices
- **Preprocessing**: Lowercasing, regex punctuation removal (`[^a-z0-9\s]`), whitespace tokenization, NLTK English stop-word filtering, and NLTK `PorterStemmer` applied sequentially across versions A, B, and C.
- **Representations**: Sorted vocabularies, binary term-document matrices, and term-frequency (TF) matrices computed directly in Python and formatted via `pandas` for display and CSV export.
- **Positional Inverted Index**: Built using `collections.defaultdict` mapping each term to document IDs and zero-based token positions, queried through `search_term()`.

## Main Results & Interpretation
Lowercasing merges case variants such as capitalized titles or uppercase terms, while removing stop words eliminates frequent function words, reducing vocabulary size, total postings, and stored token positions while shifting positions of remaining tokens. Applying Porter stemming further decreases vocabulary size and postings by grouping inflected or morphological variants under common stems. However, preprocessing does not always improve retrieval: dropping stop words can alter exact phrase or specific queries, and stemming may over-stem distinct concepts or under-stem valid variants, potentially affecting precision or recall depending on the query.
