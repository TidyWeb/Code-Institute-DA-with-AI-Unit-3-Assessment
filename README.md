# Birmingham Healthy Life: A Second Look

## 1. Purpose

*Birmingham Healthy Life: A Second Look* is an ethical revision of my Unit 2 project. I revisit the area-level healthy life expectancy analysis, examine how its methods and claims should be understood, and add checks on proxy overlap, model error, ranking uncertainty and variation hidden by aggregation. It describes patterns across 660 Middle Layer Super Output Areas (MSOAs); it does not explain any individual's health or establish causes.

## 2. The stance

**The aim is the truth about healthy life expectancy, told plainly. Ethical care means not causing avoidable harm and not claiming more than the evidence shows. It does not mean avoiding uncomfortable findings.**

## 3. Start with the site

Read [S1 — Why a second look](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s1-why-a-second-look.html) first, then visit the [deployed project site](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/). The site carries the full story, caveats, lifecycle, notebook pages and interactive dashboard. The Phase 7 reflection is still a draft in the site working clone and has not been published.

## 4. Audience

I wrote this for people who know Birmingham and its neighbouring West Midlands areas, including residents and people who work with local data or services. The site starts with plain-language summaries and visual explanations; the notebooks provide the technical detail for readers who want to follow the calculations.

## 5. What changed from Unit 2

I re-screened the project with the same 27-question ethics screen. The original screen recorded **17 concerns** and **10 no-flags**. In the Unit 3 re-screen, **15 concerns have an investigated-and-recorded response**, **2 remain open pending user testing**, and the **10 no-flags remain no-flags**. An investigated response does not mean that a risk has disappeared.

![The Unit 2 and Unit 3 ethics-screen boards: 17 original concerns and 10 no-flags; in Unit 3, 15 concerns have recorded responses, two remain open pending user testing, and 10 remain no-flags.](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/assets/img/second-look/lamp-board-before-after.svg)

The board and question-by-question evidence are in [S17 — What changed](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/what-changed.html).

## 6. Questions and hypothesis

The carried-over analysis asks how healthy life expectancy varies across Birmingham and nearby areas, whether large differences between neighbouring areas exceed estimate noise, which area measures move with HLE, how well selected measures describe HLE, and what distinguishes the sharpest neighbouring gaps. The original five questions and evidence are set out in [S1](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s1-why-a-second-look.html), [S2](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s2-the-method.html) and [S3](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s3-results-at-a-glance.html).

The hypothesis test in Notebook 04 is:

- **H₀:** neighbouring MSOAs do not differ beyond the noise in their HLE estimates.
- **H₁:** neighbouring MSOAs differ by more than that noise can explain.

Across 1,885 neighbouring pairs, 1,316 (69.8%) exceeded the 1.96 noise threshold; the simulation expected about 5% under noise alone. I reject H₀ for this test. That does not identify causes.

The new ethical questions were whether model features overlap with broad ethnic composition or deprivation, whether prediction errors differ across area groups, how certain the published low rankings are, and how much variation is hidden when LSOA data are averaged to MSOAs. Notebooks 07–09 examine these questions descriptively; none makes a claim about an individual.

## 7. Headline findings from Notebooks 07–09

- **Notebook 07 — proxy and fairness audit:** across 654 MSOAs, the seven model features predicted broad area ethnic-composition shares with cross-validated R² values from 0.277 (Other White) to 0.743 (White British); the other group results are in the notebook. This is evidence of area-level proxy overlap, not a way to infer a person's ethnicity. The model ran low by 0.31 years in the least-deprived third and high by 0.46 years in the most-deprived third; both 95% bootstrap intervals excluded zero. Removing the crime feature changed RMSE by about 0.01 years and R² by about −0.0013.
- **Notebook 08 — uncertainty and ranking:** 10,000 simulations gave 35 of the 66 areas with the lowest published HLE a probability of at least 95% of remaining in the bottom tenth. The other 31 did not meet that threshold. The median 90% rank-interval width was 65 places across all 660 areas.
- **Notebook 09 — aggregation:** of the variance across 3,205 LSOA fuel-poverty percentages, 30.3% was within MSOAs and 69.7% was between LSOA-count-weighted MSOA means. Each LSOA contributes equally to this decomposition. A separate range-versus-range rule flags 255 of 660 MSOAs (38.6%) as “mixed”; it is a descriptive comparison, not a significance test. **Methods note:** the earlier rule compared an internal range with a difference of means, so it was not like-for-like; it flagged 581/660 areas.

The findings and limits are discussed in [S11 — How certain are the rankings?](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/how-certain-are-the-rankings.html), [S12 — Proxies, fairness and crime](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/proxies-fairness-and-crime.html) and [S16 — What aggregation hides](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/what-aggregation-hides.html).

## 8. Data, sources, licences and ethics

The analysis combines ONS healthy life expectancy and geography data, Census 2021 tables from Nomis, DESNZ fuel-poverty data, Defra modelled pollution, Police.uk crime and anti-social-behaviour records, and Food environment assessment tool (Feat) data. Periods differ: HLE covers 2019–2023 and other measures mainly cover 2021–2024. The [source register](data/source-register.csv) records provenance, date, geography, limitations, revision risk, licence and attribution for each source; [raw-data notes](data/raw/README.md) describe the downloaded files.

Licence terms vary. ONS, Nomis, DESNZ and Defra sources use the Open Government Licence v3.0 where the register says it applies; the ONS boundary files require Ordnance Survey attribution. MSOA names are adapted from the House of Commons Library under the Open Parliament Licence. Feat requests a specific citation, recorded in the source register and site. No person-level records are published. My legal and social interpretation, including UK GDPR, the Data (Use and Access) Act 2025, the Equality Act 2010 and the EU AI Act scope screen, is in [S13 — Law and governance](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/law-and-governance.html). It is my reading, not legal advice.

## 9. Dashboards

- **Custom dashboard:** the [Leaflet dashboard](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/dashboard/) maps area-level results and provides uncertainty and caveat controls.
- **Tableau Public:** [Birmingham HLE](https://public.tableau.com/views/BirminghamHLEFinal/Dashboard1). The existing workbook is linked here; its uncertainty sheet is not yet added. **Uncertainty sheet: Phil to add.**

![Screenshot of the custom Leaflet dashboard with its area map, controls and selected-area information.](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/assets/img/dashboard-card.webp)

![Screenshot of the current Tableau Public workbook, with an HLE map, local-authority box plots and an HLE–income scatter plot.](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/assets/img/tableau-dashboard.webp)

## 10. Notebooks and how to run them

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

## 11. Technologies

The analysis and build scripts use Python 3.14.7, Jupyter, pandas, NumPy, SciPy, scikit-learn, GeoPandas, Shapely, Matplotlib and Seaborn. The project site uses Python to build HTML from Markdown and notebooks; its interface uses HTML, CSS, JavaScript and Leaflet. Tableau Public provides the separate business-intelligence workbook. The pinned Python packages are listed in [requirements.txt](requirements.txt).

## 12. Testing and evaluation

A fresh GitHub clone ran Notebooks 01–09 headlessly in order. All **120 files** in `data/cleaned/` were byte-identical to the committed files. Saved notebook outputs also matched, apart from Notebook 02 printing the fresh environment folder name (`.venv-unit3` rather than `.venv`); that is a path label only.

The clean-clone site build produced 40 pages. The internal checker found **0 problems across 2,160 links on 42 pages**. The working-site external check queried 54 addresses; the only two not serving a page were the known Parliament 403 (verified manually on 17 October 2026) and a dead YData link embedded in the unchanged third-party generated report. I also checked this README's links: all 14 local targets resolve; of 34 unique external URLs, 33 returned 200, 202 or a redirect, and the Open Parliament Licence returned the known 403 described below. Phase 6's desktop accessibility audit checked 41 pages: page titles, one H1, `en-GB`, non-empty image alt text, sampled keyboard navigation and focus, and measured colour-token pairs passed the recorded checks. These checks do not replace user testing.

### User testing

**Not yet done. Phil: add the session dates, participant descriptions without identifying details, tasks, what readers understood or found confusing, and changes made.** Until then, the two user-testing questions remain open in S17.

## 13. Deployment and rebuild

The static site is published through GitHub Pages from the separate [site repository](https://github.com/TidyWeb/Birmingham-Healthy-Life-Second-Look). To rebuild it, clone both repositories as sibling folders, install the analysis requirements and the site's documented Markdown builder dependency, execute notebooks 01–09, then run the dashboard builder, site builder and link checker from the site repository. Its README gives the exact commands and generated-folder scope. The live site currently reflects the latest pushed site commit; the Phase 7 site additions have not been pushed.

## 14. Known issues and bugs

- The Open Parliament Licence page returns HTTP 403 to automated checks; I verified it manually on 17 October 2026 and retained the link.
- A dead YData external link is inside the third-party generated profile `reports/ydata/hle---msoa-rows.html` (copied to the site's generated files). I left that third-party file unchanged.
- The Tableau uncertainty sheet, user testing, and Phil's rewrite of the S18 reflection draft remain outstanding. No substantive data-output difference appeared in the clean-clone rerun.

## 15. Lifecycle

[S14 — Lifecycle](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/lifecycle.html) records how I would monitor source releases, review methods and outputs, correct the site, and retire or replace it if its data or purpose no longer supports the claims. The update calendar links source changes to the notebooks and rebuild steps.

## 16. Learning-outcome criteria map

| Criterion | Evidence |
|---|---|
| **1.1 — Ethics, privacy and governance in the method** | [S2 — The method](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s2-the-method.html), [S12 — Proxy and fairness audit](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/proxies-fairness-and-crime.html), [S13 — Law and governance](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/law-and-governance.html), and [Notebooks 07–09](#10-notebooks-and-how-to-run-them). |
| **1.2 — Legal and social implications** | [S13 — Law and governance](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/law-and-governance.html), [S12 — Proxy and fairness audit](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/proxies-fairness-and-crime.html). |
| **2.1 — Explain insights to technical and non-technical readers** | This README, the plain-language sections in [S1](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s1-why-a-second-look.html), [S2](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s2-the-method.html) and [S3](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s3-results-at-a-glance.html), [S11](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/how-certain-are-the-rankings.html), and the notebook pages. |
| **2.2 — Visualisation and narrative** | [S3 — Results at a glance](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s3-results-at-a-glance.html), [S11](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/how-certain-are-the-rankings.html), [S16](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/what-aggregation-hides.html), and the custom dashboard. User testing remains pending. |
| **2.3 — Structured and accessible documentation** | This README, the [source register](data/source-register.csv), the nine notebooks, and the linked site chapters. |
| **3.1 — Project lifecycle plan** | [S14 — Lifecycle](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/lifecycle.html) records implementation, maintenance, updates, evaluation, correction and retirement. |
| **3.2 — Practical reflection** | S18 is a first-person draft in the local site clone and has not been published; Phil's rewrite remains outstanding. |

## 17. How I used AI

Claude helped with planning and review. Codex wrote code and drafts under my direction. I chose the questions and sources, made the methodological decisions, reran the analysis, checked numbers against the saved outputs and corrected errors. I am responsible for the final claims and wording. The S18 text is still a draft for me to rewrite.

## 18. Credits and attribution

I credit [*Lives on the Line*](https://jcheshire.com/featured-maps/lives-on-the-line/) by James Cheshire and Oliver O'Brien as an inspiration for asking how health outcomes vary across nearby places. Patrick Moran's spatial-statistics concept, Moran's I, helped me account for spatial dependence; I calculated it in NumPy following the [PySAL ESDA implementation](https://github.com/pysal/esda/blob/main/esda/moran.py).

Data sources include [ONS healthy life expectancy](https://www.ons.gov.uk/peoplepopulationandcommunity/healthandsocialcare/healthandlifeexpectancies/datasets/healthstatelifeexpectancyestimatesformiddlelayersuperoutputareasenglandandwales), [ONS small-area income estimates](https://www.ons.gov.uk/employmentandlabourmarket/peopleinwork/earningsandworkinghours/datasets/smallareaincomeestimatesformiddlelayersuperoutputareasenglandandwales), [Nomis Census 2021](https://www.nomisweb.co.uk/census/2021/bulk), [DESNZ fuel poverty](https://www.gov.uk/government/statistics/sub-regional-fuel-poverty-data-2026-2024-data), [Defra pollution mapping](https://uk-air.defra.gov.uk/data/pcm-data), [Police.uk](https://data.police.uk/data/), and the [Food environment assessment tool](https://www.feat-tool.org.uk/about). Feat requests the citation: *Food environment assessment tool (Feat) 2023, MRC Epidemiology Unit, University of Cambridge*; see its [citation guidance](https://www.feat-tool.org.uk/faq).

I adapted local area names from the [House of Commons Library MSOA Names lookup](https://houseofcommonslibrary.github.io/msoanames/). Public-sector sources are credited under their recorded terms, including the [Open Government Licence v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/), [Ordnance Survey](https://www.ordnancesurvey.co.uk/licensing/), and the [Open Parliament Licence](https://www.parliament.uk/site-information/copyright-parliament/open-parliament-licence/). For the legal sources cited in S13, see the [EU AI Act on EUR-Lex](https://eur-lex.europa.eu/eli/reg/2024/1689/2026-07-27/eng), [UK GDPR](https://www.legislation.gov.uk/eur/2016/679/contents), the [Data (Use and Access) Act 2025](https://www.legislation.gov.uk/ukpga/2025/18/contents), and the [Equality Act 2010](https://www.legislation.gov.uk/ukpga/2010/15/contents).
