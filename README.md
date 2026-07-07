# Intrinsic Evaluation of Word Embeddings: GloVe vs Word2Vec vs fastText

**Author:** Jana Ashour

## Task

Intrinsic evaluation of pretrained word embeddings using semantic and syntactic
analogy tests (the classic `a:b :: c:?` format), comparing embedding models and
embedding dimensionality.

## Contents

- `word_embedding_evaluation_glove_word2vec_fasttext.ipynb` — notebook loading
  embeddings, running analogy tests, and computing accuracy
- `word_embedding_evaluation_glove_word2vec_fasttext_report.pdf` — written report
  with full results tables and analysis

## Parts

1. **GloVe vs Word2Vec (Skip-gram) vs fastText**, all at 300 dimensions — 10
   semantic and 10 syntactic analogy tests per model
2. **GloVe at 300d vs 100d vs 50d** — isolating the effect of embedding
   dimensionality on analogy accuracy, holding the model fixed

## Key Results

**Part 1 — Model comparison (300d):**

| Model      | Semantic Accuracy | Syntactic Accuracy |
|------------|--------------------|---------------------|
| GloVe      | 50.00%             | 60.00%              |
| Word2Vec   | 40.00%             | 50.00%              |
| fastText   | 70.00%             | 70.00%              |

**Part 2 — Dimensionality comparison (GloVe):**

| Dimension | Semantic Accuracy | Syntactic Accuracy |
|-----------|--------------------|---------------------|
| 300d      | 50%                | 60%                 |
| 100d      | 40%                | 50%                 |
| 50d       | 30%                | 40%                 |

## Findings

- **fastText consistently outperforms** GloVe and Word2Vec on both semantic and
  syntactic analogies, driven by its character n-gram subword modeling, which
  helps with morphology and rare/out-of-vocabulary words.
- **GloVe** does better on syntactic than semantic analogies, suggesting its
  global co-occurrence statistics capture systematic syntactic regularities
  more reliably than varied, context-dependent semantic relationships.
- **Word2Vec** has the weakest performance of the three, limited by its
  reliance on local context windows only, with no subword or global
  co-occurrence information.
- **Dimensionality matters**: accuracy drops steadily as embedding size
  shrinks (300d → 100d → 50d), with syntactic accuracy consistently ~10
  percentage points higher than semantic accuracy at every dimension,
  indicating syntactic structure compresses more gracefully than semantic
  meaning.
- Across all models, syntactic tasks show a smaller performance spread (20%)
  than semantic tasks (30%), reinforcing that semantic relationships are
  harder and more varied to capture than syntactic ones.
