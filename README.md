# Dependency Parsing Accuracy and Dependency Distance
## A Comparison of English and German

This project investigates whether dependency parsing becomes more difficult when connected words are farther apart in a sentence. English and German are compared using Universal Dependencies test data and the Stanza dependency parser.

## Research Question

Does the distance between connected words affect how accurately a computer understands a sentence?

## Hypotheses

**H1:** Parsing accuracy will decrease as the distance between connected words increases.

**H2:** The effect of dependency distance will differ between English and German.

## Dataset

The analysis uses Universal Dependencies test data:

| Language | Sentences | Parser |
|----------|-----------|--------|
| English  | 2,077     | Stanza |
| German   | 977       | Stanza |

A total of **38,539 dependencies** were analysed.

Dependency distance was divided into four groups:

- Short: 1–2 positions
- Medium: 3–5 positions
- Long: 6–10 positions
- Very long: >10 positions

## Method

The analysis follows these steps:

1. Load the English and German Universal Dependencies test data.
2. Run the Stanza dependency parser.
3. Compare predicted dependencies with the gold-standard annotations.
4. Calculate dependency distance between each word and its syntactic head.
5. Calculate parsing accuracy using UAS and LAS.
6. Compare performance across dependency-distance groups.
7. Analyse differences between English and German.
8. Perform error analysis for frequent dependency relations.
9. Use logistic regression to examine the relationship between language, dependency distance, and parsing errors.

## Evaluation

**UAS (Unlabelled Attachment Score)** measures whether the parser identified the correct head word.

**LAS (Labelled Attachment Score)** measures whether the parser identified both the correct head word and the correct dependency relation.

## Main Results

### Overall performance

| Language | UAS | LAS |
|----------|-----|-----|
| English | 92.03% | 89.56% |
| German | 87.46% | 83.19% |

### LAS by dependency distance

| Distance | English | German |
|----------|---------|--------|
| Short | 92.35% | 87.25% |
| Medium | 86.90% | 78.66% |
| Long | 80.79% | 78.11% |
| Very long | 79.37% | 73.32% |

The results show that parsing accuracy generally decreases as dependency distance increases.

## Error Analysis

The highest LAS error rates among frequent dependency relations were:

| Dependency relation | LAS error rate |
|---------------------|----------------|
| German – compound | 67.98% |
| English – parataxis | 55.17% |
| English – appos | 43.92% |
| English – list | 42.76% |
| German – appos | 41.67% |
| English – nmod:unmarked | 41.44% |

These results suggest that dependency distance is not the only factor affecting parsing accuracy.

## Statistical Analysis

Logistic regression was used to test whether dependency distance and language were related to parsing errors.

The short and medium language–distance interactions were statistically significant, while the interaction for very long dependencies was not statistically significant.

## Repository Contents

- `dependency_parsing_analysis.ipynb` – main analysis notebook
- `UD_Multilingual_Error_Analysis.ipynb` – dependency relation error analysis

## Reproducibility

The notebooks contain the analysis used to produce the results reported in the research poster.

## Author

Sai Sandeep Mundru

MSc Natural Language Processing  
Trier University
