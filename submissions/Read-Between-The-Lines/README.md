# [Team Name]: Is It Preeclampsia, or Just an Early Delivery?

OpenBio 2026 Datathon, Track 1: Maternal-Fetal Cell Communication in Preeclampsia

## Team

| Name | Role |
|---|---|
| [Name] | [Role] |

## Research Question

In placental tissue, how much of the difference in gene activity between early-onset preeclampsia and control pregnancies could be explained by when delivery happened (starter question 6)?

## Data Used

- [x] GSE203507 bulk RNA-seq (required): 30 villous placenta samples, one per pregnancy
- [x] Zeisel/Admati gene browser, for five genes (required): FLT1, ENG, PAPPA2, LEP, HLA-G
- [ ] Admati/Skarbianskis single-cell pseudobulk files (optional): not used; the early-onset comparison has only 3 control donors
- [ ] Other public data: none

## How to Run

1. Clone the [datathon repository](https://github.com/Harvard-Undergraduate-OpenBio/openbio-datathon-2026) and put this folder at `submissions/<this-folder>/`. The notebook finds the data package at `track-01/data` automatically. It also runs unchanged from `track-01/notebooks/`.
2. Create the environment by following [Track 1 Setup](https://github.com/Harvard-Undergraduate-OpenBio/openbio-datathon-2026/blob/main/track-01/1-setup.md) (`conda env create -f environment/environment.yml`).
3. Open `notebooks/track01_workflow.ipynb` and choose **Restart & Run All**. It takes about 20 minutes on a laptop and 40 minutes or more on free Google Colab. Most of the time goes to the 20 repeated draws in Section 10. Figures and tables are written to `notebooks/results/`.

Reproducibility details:

- Notebook: `notebooks/track01_workflow.ipynb` (single notebook, runs top to bottom)
- Where we ran it: Google Colab and our own computer, with Python 3.13, PyDESeq2 0.6.0 and pandas 2.3. The saved outputs and every number in our documents come from this setup.
- Software version note: PyDESeq2 0.6.0 needs Python 3.12 or newer. The datathon's conda environment uses Python 3.11, which installs PyDESeq2 0.5.4. That version gives slightly different gene counts (for example 522 instead of 532 genes for preeclampsia vs preterm controls) but the same conclusions.
- Random seed: 2026 (`numpy.random.default_rng`). Used only for plot jitter and the random 5-vs-5 draws in Section 10. All other results are deterministic.

## Files

| Path | Contents |
|---|---|
| `notebooks/` | The analysis notebook |
| `figures/` | Exported graphs, including `headline.png` |
| `docs/article.md` | Science communication article, following the [HUDP article guide](https://github.com/Harvard-Undergraduate-OpenBio/openbio-datathon-2026/blob/main/docs/article-guide.md) |
| `docs/analysis-plan.md` | The comparisons, model and thresholds we chose |
| `docs/hypothesis-card.md` | Our hypothesis and how to test it |
| `docs/presentation-outline.md` | Outline for the recorded presentation |

## Key Findings

We compared 15 early-onset preeclampsia placentas with 5 preterm controls delivered in the same weeks, and with 5 term controls delivered about 9 weeks later. Preeclampsia differed from each control group in the same number of genes (532 each, at least 2-fold, adjusted p < 0.05), though only 240 genes were shared between the two lists. At equal group sizes (5 vs 5), timing alone (preterm vs term controls) changed 86 genes. That is more than random splits (0 to 17), but about six times fewer than preeclampsia (median 537). About half (53%) of the differences against term controls held up against same-time controls, and about a quarter (28%) looked driven by timing. Core preeclampsia genes (FLT1, ENG, LEP, PAPPA2) were raised regardless of delivery week. In the gene browser, FLT1, PAPPA2 and LEP sit mainly in trophoblast cells and ENG mainly in blood-vessel cells.

## Limitations

- Only 5 controls of each type.
- Preterm controls are spontaneous preterm births, which often involve inflammation, so they are not a healthy 31-week placenta.
- Bulk tissue mixes many cell types.
- All preeclampsia cases are early onset.
- Growth restriction occurs only in the preeclampsia group, which reduces power when we adjust for it.
- Our random-split noise baseline mixes preterm and term controls, so it still contains some timing signal.
- Results show association, not cause.

## Presentation

Video link: [add your unlisted YouTube link]

## Data Citations

1. Ackerman WE, Buhimschi IA, Buhimschi CS, et al. Molecular subphenotyping using placental transcriptomics in early-onset preeclampsia and fetal growth restriction. NCBI GEO [GSE203507](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE203507).
2. Admati I, Skarbianskis N, et al. Two molecular faces of preeclampsia. [Zeisel lab placenta PE gene browser](https://storage.googleapis.com/www_zeisellab/PE_web/pe_web_test_v1.html); data on [Figshare](https://doi.org/10.6084/m9.figshare.23264102.v1) (CC BY 4.0).
3. Muzellec B, et al. PyDESeq2: a Python package for bulk RNA-seq differential expression analysis. Bioinformatics (2023).
