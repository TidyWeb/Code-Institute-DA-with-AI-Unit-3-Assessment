# The Ethics of a Birmingham Healthy Life

## Purpose

I built [Ethical Considerations in AI](https://tidyweb.github.io/ethical-considerations-in-ai/) as an independent companion to the Code Institute LMS lesson for fellow students, then created [Signal Box: the AI ethics check](https://tidyweb.github.io/ethical-considerations-in-ai/#screening-tool) within it. I applied Signal Box to my Unit 2 Birmingham Healthy Life project; Unit 3 is that ethical rework and a practical test of whether Signal Box works. The guide is my own study material, not official Code Institute material; its [source repository](https://github.com/TidyWeb/ethical-considerations-in-ai) records the work. Applying Signal Box also exposed weaknesses in the tool, which I fixed on 19 October 2026: the pop-up did not explain how to clear an orange lamp, the guidance repeated itself, and there was no test for what earned yellow.

*The Ethics of a Birmingham Healthy Life* is an ethical revision of my Unit 2 project. I revisit the Birmingham Healthy Life area-level healthy life expectancy analysis because it was rich in ethical dilemmas.  I here examine how its methods and claims should be understood, and add checks on proxy overlap, model error, ranking uncertainty and variation hidden by aggregation. It describes patterns across 660 Middle Layer Super Output Areas (MSOAs); NB: It does not explain any individual's health or establish causes.

## 1. Start with the site

Open **[The Ethics of a Birmingham Healthy Life](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/)**. On the homepage, choose **The story**, then begin with [**Why a second look**](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s1-why-a-second-look.html). The site brings together the full story, its caveats, notebook pages and interactive dashboard.

**Quick links:** [Open the site](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/) · [Start the story: Why a second look](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s1-why-a-second-look.html) · [Leaflet dashboard](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/dashboard/) · [Full findings](#6-headline-findings-from-notebooks-0709) · [Run the notebooks](#9-notebooks-and-how-to-run-them) · [Evaluation](#11-testing-and-evaluation) · [Known issues](#13-known-issues-and-bugs) · [Criteria map](#15-learning-outcome-criteria-map) · [Project board](https://github.com/users/TidyWeb/projects/2)

**Project board:** [Unit 3 project board](https://github.com/users/TidyWeb/projects/2)

### At a glance

My checks describe area-level patterns and do not establish causes:

- **Ranking uncertainty:** 35 of the 66 MSOAs with the lowest published HLE had at least a 95% simulated probability of remaining in the bottom tenth; the other 31 did not meet that threshold. A published rank is not certain.
- **Model error by deprivation:** the model ran low by 0.31 years in the least-deprived third of MSOAs and high by 0.46 years in the most-deprived third; both 95% bootstrap intervals excluded zero. These are area-level prediction errors.
- **Aggregation:** 30.3% of the variance across 3,205 Lower Layer Super Output Area (LSOA) fuel-poverty percentages was within MSOAs, with each LSOA contributing equally. This is a descriptive decomposition, not a significance test.

## 2. The stance

**The aim is the truth about healthy life expectancy, told plainly. Ethical care means not causing avoidable harm and not claiming more than the evidence shows. It does not mean avoiding uncomfortable findings.**

## 3. Audience

I wrote this for people who know Birmingham and its neighbouring West Midlands areas, including residents and people who work with local data or services. The site starts with plain-language summaries and visual explanations; the notebooks provide the technical detail for readers who want to follow the calculations.

## 4. Results of applying Signal Box

My first application of Signal Box recorded **17 concerns** and **10 no-flags**. In Unit 3, after the say-it-out-loud re-test, **14 are investigated and recorded**, **3 remain open (Q4, Q18 and Q21)**, and **10 remain no-flags**. A recorded response does not mean the risk has gone; a no-flag does not prove safety. Signal Box is a screening aid, not a legal assessment.

Before I turn a lamp yellow, I must be able to say what could go wrong, who it would happen to, what deals with it, and who is responsible. If I cannot say that in a sentence or two, the lamp stays orange. Applying this sharper test moved Q4 back to orange; that is a finding of testing the tool on my own work.

- **Q4 — Benefit to me, cost to others:** I gain assessment and portfolio evidence while people in named areas could bear stigma. This stays open until user testing with three Birmingham readers is recorded.
- **Q18 — Affected people left out of design and testing:** I will re-judge this when the readers’ feedback and any changes are recorded.
- **Q21 — Tested only in a demo, not real use:** I will re-judge this when their testing in use is recorded.

The guide develops the Code Institute LMS lesson “Ethical considerations in AI” with independent research, including UNESCO’s AI ethics Recommendation, the OECD AI Principles, NIST’s AI Risk Management Framework, UK GDPR changes under the Data (Use and Access) Act 2025, ICO guidance and the EU AI Act. It is independent study material, not official Code Institute material; its legal checks are dated 14 October 2026.

![The Unit 2 and Unit 3 Signal Box boards: 17 original concerns and 10 no-flags; in Unit 3, 14 are investigated and recorded, three remain open (Q4, Q18 and Q21), and 10 remain no-flags.](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/assets/img/second-look/lamp-board-before-after.svg)

The board, all 15 verbatim say-it-out-loud statements and the question-by-question evidence are in [What changed](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/what-changed.html).

## 5. Questions and hypothesis

The carried-over analysis asks how healthy life expectancy varies across Birmingham and nearby areas, whether large differences between neighbouring areas exceed estimate noise, which area measures move with HLE, how well selected measures describe HLE, and what distinguishes the sharpest neighbouring gaps. The original five questions and evidence are set out in [Why a second look](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s1-why-a-second-look.html), [The method](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s2-the-method.html) and [Results at a glance](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s3-results-at-a-glance.html).

The hypothesis test in Notebook 04 is:

- **H₀:** neighbouring MSOAs do not differ beyond the noise in their HLE estimates.
- **H₁:** neighbouring MSOAs differ by more than that noise can explain.

Across 1,885 neighbouring pairs, 1,316 (69.8%) exceeded the 1.96 noise threshold; the simulation expected about 5% under noise alone. I reject H₀ for this test. That does not identify causes.

The new ethical questions were whether model features overlap with broad ethnic composition or deprivation, whether prediction errors differ across area groups, how certain the published low rankings are, and how much variation is hidden when LSOA data are averaged to MSOAs. Notebooks 07–09 examine these questions descriptively; none makes a claim about an individual.

## 6. Headline findings from Notebooks 07–09

- **Notebook 07 — proxy and fairness audit:** across 654 MSOAs, the seven model features predicted broad area ethnic-composition shares with cross-validated R² values from 0.277 (Other White) to 0.743 (White British); the other group results are in the notebook. This is evidence of area-level proxy overlap, not a way to infer a person's ethnicity. The model ran low by 0.31 years in the least-deprived third and high by 0.46 years in the most-deprived third; both 95% bootstrap intervals excluded zero. Removing the crime feature changed RMSE by about 0.01 years and R² by about −0.0013.
- **Notebook 08 — uncertainty and ranking:** 10,000 simulations gave 35 of the 66 areas with the lowest published HLE a probability of at least 95% of remaining in the bottom tenth. The other 31 did not meet that threshold. The median 90% rank-interval width was 65 places across all 660 areas.
- **Notebook 09 — aggregation:** of the variance across 3,205 LSOA fuel-poverty percentages, 30.3% was within MSOAs and 69.7% was between LSOA-count-weighted MSOA means. Each LSOA contributes equally to this decomposition. A separate range-versus-range rule flags 255 of 660 MSOAs (38.6%) as “mixed”; it is a descriptive comparison, not a significance test. **Methods note:** the earlier rule compared an internal range with a difference of means, so it was not like-for-like; it flagged 581/660 areas.

The findings and limits are discussed in [How certain are the rankings?](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/how-certain-are-the-rankings.html), [Proxies, fairness and crime](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/proxies-fairness-and-crime.html) and [What aggregation hides](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/what-aggregation-hides.html).

## 7. Data, sources, licences and ethics

The analysis combines ONS healthy life expectancy and geography data, Census 2021 tables from Nomis, DESNZ fuel-poverty data, Defra modelled pollution, Police.uk crime and anti-social-behaviour records, and Food environment assessment tool (Feat) data. Periods differ: HLE covers 2019–2023 and other measures mainly cover 2021–2024. The [source register](data/source-register.csv) records provenance, date, geography, limitations, revision risk, licence and attribution for each source; [raw-data notes](data/raw/README.md) describe the downloaded files.

Licence terms vary. ONS, Nomis, DESNZ and Defra sources use the Open Government Licence v3.0 where the register says it applies; the ONS boundary files require Ordnance Survey attribution. MSOA names are adapted from the House of Commons Library under the Open Parliament Licence. Feat requests a specific citation, recorded in the source register and site. No person-level records are published. My legal and social interpretation, including UK GDPR, the Data (Use and Access) Act 2025, the Equality Act 2010 and the EU AI Act scope check, is in [Law and governance](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/law-and-governance.html). It is my reading, not legal advice.

## 8. Dashboards

- **Custom dashboard:** the [Leaflet dashboard](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/dashboard/) maps area-level results and provides uncertainty and caveat controls.
- **Tableau Public:** [Birmingham HLE](https://public.tableau.com/views/BirminghamHLEFinal/Dashboard1). This Tableau dashboard was created for Unit 2 and is included here unchanged.

![Screenshot of the custom Leaflet dashboard with its area map, controls and selected-area information.](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/assets/img/dashboard-card.webp)

![Screenshot of the current Tableau Public workbook, with an HLE map, local-authority box plots and an HLE–income scatter plot.](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/assets/img/tableau-dashboard.webp)

## 9. Notebooks and how to run them

Run the notebooks in numerical order. Each reads saved outputs from earlier notebooks and writes its own outputs under `data/cleaned/`.

1. [01 — Source Exploration](notebooks/A%20%E2%80%94%20Source%20Exploration/01_Source_Exploration.ipynb): inspect HLE estimates, geography and the initial area comparisons.
2. [02 — Data Preparation](notebooks/B%20%E2%80%94%20Data%20Preparation/02_Data_Preparation.ipynb): prepare source measures at MSOA grain and record coverage and exclusions.
3. [03 — Joined Table and Exploration](notebooks/C%20%E2%80%94%20Joined%20Table%20and%20Exploration/03_Joined_Table_and_Exploration.ipynb): join the measures and explore associations and overlap.
4. [04 — Hypothesis and Neighbour Gaps](notebooks/D%20%E2%80%94%20Hypothesis%20and%20Neighbour%20Gaps/04_Hypothesis_and_Neighbour_Gaps.ipynb): test neighbour gaps against simulated estimate noise.
5. [05 — Machine Learning](notebooks/E%20%E2%80%94%20Machine%20Learning/05_Machine_Learning.ipynb): cluster area profiles and evaluate a linear HLE model.
6. [06 — Hotspots](notebooks/F%20%E2%80%94%20Hotspots/06_Hotspots.ipynb): examine selected large-gap neighbourhoods and their area-level characteristics.
7. [07 — Proxy and Fairness Audit](notebooks/G%20%E2%80%94%20Proxy%20and%20Fairness%20Audit/07_Proxy_and_Fairness_Audit.ipynb): test proxy overlap, group error patterns and crime-feature sensitivity.
8. [08 — Uncertainty and Ranking](notebooks/H%20%E2%80%94%20Uncertainty%20and%20Ranking/08_Uncertainty_and_Ranking.ipynb): simulate uncertainty in area ranks and bottom-tenth membership.
9. [09 — Aggregation](notebooks/I%20%E2%80%94%20Aggregation/09_Aggregation.ipynb): measure within- and between-MSOA fuel-poverty variation and compare ranges.

For a fresh copy, install Python 3.14.7, create and activate a virtual environment, then install the pinned packages and notebook tooling:

```bash
git clone https://github.com/TidyWeb/Code-Institute-DA-with-AI-Unit-3-Assessment.git
cd Code-Institute-DA-with-AI-Unit-3-Assessment
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python -m pip install nbconvert
python -m ipykernel install --user --name unit3 --display-name "Python (unit3)"
jupyter notebook
```

Open Notebook 01, select the `Python (unit3)` kernel, and run each notebook through 09. Paths are derived from the project files; no machine-specific paths are required. For the separate site build, follow the instructions in the [site repository](https://github.com/TidyWeb/Birmingham-Healthy-Life-Second-Look).

## 10. Technologies

The analysis and build scripts require Python 3.12 or later and were tested on Python 3.14.7. They use Jupyter, pandas, NumPy, SciPy, scikit-learn, GeoPandas, Shapely, Matplotlib and Seaborn. The project site uses Python to build HTML from Markdown and notebooks; its interface uses HTML, CSS, JavaScript and Leaflet. Tableau Public provides the separate business-intelligence workbook. The pinned Python packages are listed in [requirements.txt](requirements.txt).

## 11. Testing and evaluation

A fresh GitHub clone ran Notebooks 01–09 in order. All **120 files** in `data/cleaned/` matched the committed files. Saved notebook outputs also matched, apart from Notebook 02 printing the environment folder name; this is a path label only.

A clean site build produced 40 pages. The internal link checker found **0 problems across 2,160 links on 42 pages**. Automated external checks found two link issues: the Open Parliament Licence page returns HTTP 403, and a third-party generated report contains a dead YData link. A desktop accessibility audit checked page titles, one H1 per page, `en-GB`, image alt text, sampled keyboard navigation and focus, and selected colour contrasts. Automated checks do not replace user testing.

### User testing

User testing is under way with three Birmingham readers. I will re-judge Q4, Q18 and Q21 when their testing is recorded. My review of the dashboard and site led to fixes for search, labels, navigation and plain-English wording. That review helped identify problems, but it does not show how other readers understand the results. The site explains the limits and uncertainty; feedback from readers would help assess whether those explanations are clear.

## 12. Deployment and rebuild

The static site is published through GitHub Pages from the separate [site repository](https://github.com/TidyWeb/Birmingham-Healthy-Life-Second-Look). To rebuild it, clone both repositories as sibling folders, install the analysis requirements and the site's documented Markdown builder dependency, execute notebooks 01–09, then run the dashboard builder, site builder and link checker from the site repository. Its README gives the exact commands and generated-folder scope.

## 13. Known issues and bugs

- The Open Parliament Licence page returns HTTP 403 to automated checks; the link is retained.
- A third-party generated profile, `reports/ydata/hle---msoa-rows.html`, contains a dead external link.

## 14. Lifecycle

[Lifecycle](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/lifecycle.html) records how I would monitor source releases, review methods and outputs, correct the site, and retire or replace it if its data or purpose no longer supports the claims. The update calendar links source changes to the notebooks and rebuild steps.

## 15. Learning-outcome criteria map

| Criterion | Evidence |
|---|---|
| **1.1 — Ethics, privacy and governance in the method** | [The method](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s2-the-method.html), [Proxies, fairness and crime](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/proxies-fairness-and-crime.html), [Law and governance](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/law-and-governance.html), and [Notebooks 07–09](#9-notebooks-and-how-to-run-them). |
| **1.2 — Legal and social implications** | [Law and governance](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/law-and-governance.html), [Proxies, fairness and crime](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/proxies-fairness-and-crime.html). |
| **2.1 — Explain insights to technical and non-technical readers** | This README, the plain-language sections in [Why a second look](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s1-why-a-second-look.html), [The method](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s2-the-method.html) and [Results at a glance](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s3-results-at-a-glance.html), [How certain are the rankings](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/how-certain-are-the-rankings.html), and the notebook pages. |
| **2.2 — Visualisation and narrative** | [Results at a glance](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s3-results-at-a-glance.html), [How certain are the rankings](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/how-certain-are-the-rankings.html), [What aggregation hides](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/what-aggregation-hides.html), and the custom dashboard. |
| **2.3 — Structured and accessible documentation** | This README, the [source register](data/source-register.csv), the nine notebooks, and the linked site chapters. |
| **3.1 — Project lifecycle plan** | [Lifecycle](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/lifecycle.html) records implementation, maintenance, updates, evaluation, correction and retirement. |
| **3.2 — Practical reflection** | Not evidenced in the published project. |

## 16. How I used AI

Claude helped with planning and review. Codex wrote code and drafts under my direction. I chose the questions and sources, made the methodological decisions, reran the analysis, checked numbers against the saved outputs and corrected errors. I am responsible for the final claims and wording.

## 17. Credits and attribution

I credit [*Lives on the Line*](https://jcheshire.com/featured-maps/lives-on-the-line/) by James Cheshire and Oliver O'Brien as an inspiration for asking how health outcomes vary across nearby places. Patrick Moran's spatial-statistics concept, Moran's I, helped me account for spatial dependence; I calculated it in NumPy following the [PySAL ESDA implementation](https://github.com/pysal/esda/blob/main/esda/moran.py).

Data sources include [ONS healthy life expectancy](https://www.ons.gov.uk/peoplepopulationandcommunity/healthandsocialcare/healthandlifeexpectancies/datasets/healthstatelifeexpectancyestimatesformiddlelayersuperoutputareasenglandandwales), [ONS small-area income estimates](https://www.ons.gov.uk/employmentandlabourmarket/peopleinwork/earningsandworkinghours/datasets/smallareaincomeestimatesformiddlelayersuperoutputareasenglandandwales), [Nomis Census 2021](https://www.nomisweb.co.uk/census/2021/bulk), [DESNZ fuel poverty](https://www.gov.uk/government/statistics/sub-regional-fuel-poverty-data-2026-2024-data), [Defra pollution mapping](https://uk-air.defra.gov.uk/data/pcm-data), [Police.uk](https://data.police.uk/data/), and the [Food environment assessment tool](https://www.feat-tool.org.uk/about). Feat requests the citation: *Food environment assessment tool (Feat) 2023, MRC Epidemiology Unit, University of Cambridge*; see its [citation guidance](https://www.feat-tool.org.uk/faq).

I adapted local area names from the [House of Commons Library MSOA Names lookup](https://houseofcommonslibrary.github.io/msoanames/). Public-sector sources are credited under their recorded terms, including the [Open Government Licence v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/), [Ordnance Survey](https://www.ordnancesurvey.co.uk/licensing/), and the [Open Parliament Licence](https://www.parliament.uk/site-information/copyright-parliament/open-parliament-licence/). For the legal sources cited in the Law and governance chapter, see the [EU AI Act on EUR-Lex](https://eur-lex.europa.eu/eli/reg/2024/1689/2026-07-27/eng), [UK GDPR](https://www.legislation.gov.uk/eur/2016/679/contents), the [Data (Use and Access) Act 2025](https://www.legislation.gov.uk/ukpga/2025/18/contents), and the [Equality Act 2010](https://www.legislation.gov.uk/ukpga/2010/15/contents).
