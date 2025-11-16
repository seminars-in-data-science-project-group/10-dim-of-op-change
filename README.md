# Reproducibility Study
### *The Language of Opinion Change on Social Media under the Lens of Communicative Action*

This repository contains the reproducibility work for the study:

**Monti, Corrado, et al. (2022)**  
*The language of opinion change on social media under the lens of communicative action*  

The goal of this project is to reproduce two core empirical results from the original paper:

- **Figure 1** – Odds ratios comparing social dimensions in posts, comments, and post–comment interactions.
- **Table 2** – Logistic regression models predicting opinion change using social dimensions, sentiment, and political variables.

This work was completed as part of the **Seminars in Data Science** course.

# Contents

- **Original GitHub Repository:**  
  [https://github.com/corradomonti/10-dim-of-op-change](https://github.com/corradomonti/10-dim-of-op-change)

- **Original Paper:**  
  *Monti, C. et al., “Ten Dimensions of Opinion Change” (2020)*
  [https://www.nature.com/articles/s41598-022-21720-4](https://www.nature.com/articles/s41598-022-21720-4 )
- [Analysis notebooks](/../../blob/master/notebook/)

- Main data set: [changemyview-sociopol-processed.pickle.gz](https://github.com/corradomonti/10-dim-of-op-change/releases/tag/changemyview-sociopol-processed)  149 MB

- [Human-labelled set of sociopolitical subreddits](/../../blob/master/data/top-2000-sfw-subreddits-labelled.csv)
- [Sociopolitical classifier](/../../blob/master/data/vocabulary-classifier.pickle)

---

## What we reproduced

Odds ratios for each social dimension (Figure 1a)  
Odds ratios for dimensions in original posts (Figure 1b)  

**Figure 1c** – Interaction matrix of post–comment dimensions  
   - The final cell in Notebook 3 requires a file named `matrix_NEW_weighted-comment_discounted`,
     which is not included in the public repository. Because this file is missing, Figure 1c cannot be fully reproduced.  
   - All other analyses in Notebook 3 run successfully.
     
Logistic regression models A–H (Table 2), including pseudo-R² and significance levels

All reproduced results match the original published values.

---

## Repository Contents
```bash
/data
│
├── top-2000-sfw-subreddits-labelled.csv
├── vocabulary-classifier.pickle
└── changemyview-sociopol-processed.pickle.gz # Main dataset (MUST BE DOWNLOADED SEPARATELY AND PLACED HERE)
/notebook
│
├── 1.1_build-sociopol-training-set.py
├── 1.2_build-and-test-sociopol-classifier.ipynb
├── 1.3_apply-sociopol-classifier-on-cmv.ipynb
├── 2_logistic-regression.ipynb # Notebook 2 – generates Table 2
└── 3_odds-ratios.ipynb # Notebook 3 – generates Figure 1
/paper
│
├── fig
│   ├── comments-social-dim-log-reg.pdf
│   └── homophily-matrix.pdf
│
└── tables
    ├── comments-social-dim-log-reg.tex
    ├── homophily-log-reg-length.tex
    └── homophily-log-reg.tex
├── README.md
├── environment.yml
└── .gitignore
```

## Data
We use the processed dataset released by the original authors:

- `changemyview-sociopol-processed.pickle.gz`  
(Download from: https://github.com/corradomonti/10-dim-of-op-change/releases/tag/changemyview-sociopol-processed)

No raw scraping or preprocessing is required.

## How to Run

**Create a Conda environment**
```bash
conda env create -f environment.yml
conda activate cmv-repro
```
**Add missing dependencies (if needed)**
```bash
pip install statsmodels
pip install --upgrade numpy
```
Place the dataset in the /data folder
```bash
changemyview-sociopol-processed.pickle.gz
```
Run the notebooks in order
- 2_logistic-regression.ipynb
- 3_odds-ratios.ipynb

## Known Issues

- Some notebook commands assume **macOS/Linux**.  
  On **Windows**, directory-creation cells must be edited manually.

- The final cell of **Notebook 3** requires a file named:

  `matrix_NEW_weighted-comment_discounted`

  This file is **not included** in the repository, so **Figure 1c cannot be fully reproduced**.

## Reproduction Team (Authors)

- **Piotr** – Introduction, scope of reproducibility  
- **Vlad** – Reproducibility summary, Table 2, discussion  
- **Ayat** – Figure 1 analysis  
- **Nikolas** – Methodology, environment setup
