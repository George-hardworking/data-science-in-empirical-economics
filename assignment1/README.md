# Assignment 1: Text Mining & Topic Modeling

## Project Information

| Item | Description |
|---|---|
| Course | IPEN 5810 — Data Science in Empirical Economics |
| Topic | Text Mining and Topic Modeling on MPC Meeting Minutes |
| Data | MPC (Monetary Policy Committee) minutes text |
| Framework | Natural Language Processing, Topic Modeling |

## Overview

This assignment analyzes MPC meeting minutes using a variety of text mining techniques. The notebook implements a complete NLP pipeline: text preprocessing (lowercasing, contraction expansion, tokenization, stopword removal, stemming, and lemmatization), document frequency analysis, TF-IDF feature extraction, and LDA (Latent Dirichlet Allocation) topic modeling.

The analysis identifies latent themes in central bank communications, interprets topic-word distributions, and evaluates model coherence using NPMI (Normalized Pointwise Mutual Information).

## Tasks

1. **Text Preprocessing** (20 pts): Load MPC minutes, perform lowercasing, contraction expansion, tokenization, ASCII filtering, stopword removal, stemming (Porter), and lemmatization (WordNet).
2. **Document Frequency Ranking** (15 pts): Compute and rank stems by document frequency; visualize top terms.
3. **TF-IDF Analysis** (25 pts): Compute TF-IDF scores, rank terms, filter low-score terms (threshold > 3,500), and construct filtered document-term matrix.
4. **LDA Topic Modeling** (40 pts): Train LDA with 30 topics (Dirichlet priors: 50/k, 200/vocab_size, 5,000 iterations). Display top-15 words per topic, visualize topic-word distributions, perform NPMI coherence sweep across [10, 15, 20, 25, 30] topics, and provide economic interpretation of three selected topics.

## Repository Structure

```text
assignment1/
├── raw/
│   └── mpc_minutes.txt               # Raw MPC meeting minutes text
├── scripts/
│   └── assignment1_kaibiao.ipynb     # Main analysis notebook
├── output/                           # Generated outputs (tables, figures)
├── docs/
│   └── hw1.pdf                       # Assignment instructions
└── README.md
```

## Main Analysis File

```text
scripts/assignment1_kaibiao.ipynb
```

The notebook is structured as:

1. Import packages and build stopword set
2. Load raw data and preprocess (contraction expansion, tokenization, stemming, lemmatization)
3. Document frequency ranking and visualization
4. TF-IDF computation, ranking, and threshold filtering
5. LDA topic model estimation (30 topics)
6. NPMI-based topic count optimization
7. Topic visualization and economic interpretation

## Environment

Python 3.10+ is recommended.

Key packages include:

- `pandas`, `numpy`
- `nltk` (stopwords, PorterStemmer, WordNetLemmatizer, word_tokenize)
- `scikit-learn` (TfidfVectorizer, LatentDirichletAllocation, CountVectorizer)
- `matplotlib`
- `gensim` (CoherenceModel for NPMI evaluation)
- `contractions`
- `tqdm`

## How to Run

From the repository root:

```bash
jupyter nbconvert \
  --to notebook \
  --execute assignment1/scripts/assignment1_kaibiao.ipynb \
  --output assignment1_kaibiao_executed.ipynb \
  --output-dir assignment1/output \
  --ExecutePreprocessor.kernel_name=5020_env
```

Or run interactively in Jupyter using the `5020_env` kernel.

## Outputs

Running the notebook generates:

- TF-IDF ranking tables and filtered document-term matrix
- Document frequency bar charts
- LDA topic-word distribution tables and visualizations
- NPMI coherence scores across candidate topic counts
- Topic interpretation notes for 30 identified themes

## Notes on Reproducibility

- Random state is set to `0` in LDA for reproducibility.
- A custom expanded stopword set is used (NLTK + scikit-learn + manual additions).
- The notebook should be run from a clean kernel for final reproduction.

## License

This assignment is for course project submission and academic use.
