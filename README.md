# The Ethics of a Birmingham Healthy Life

## Purpose

The Code Institute's Unit 3 assessment is an exercise in the ethical handling of data. I had just built, for Unit 2, a large and complex investigation into healthy life expectancy in Birmingham and its surrounding areas, drawing on data about ethnicity, sex, income, crime and other features of local life. It seemed an ideal project against which to apply an ethics-first lens.

I began by looking back at the work I'd done on the Code Institute's ethics module in their LMS. To help my fellow students with that module, I built a web page called [Ethical Considerations in AI](https://tidyweb.github.io/ethical-considerations-in-ai/). Inside that, I built a utility I called [Signal Box](https://tidyweb.github.io/ethical-considerations-in-ai/#screening-tool), which was a way to check ethical considerations using 27 yes or no questions about who a data project could harm and how. Each question has a lamp: orange for a concern, yellow once the concern has been investigated and recorded, grey where no concern was raised. Signal Box is my own study material, not official Code Institute material.

*The Ethics of a Birmingham Healthy Life* is an ethical revision of my Unit 2 project. I revisit the Birmingham Healthy Life area-level healthy life expectancy analysis because it was rich in ethical dilemmas.  I here examine how its methods and claims should be understood, and add checks on proxy overlap, model error, ranking uncertainty and variation hidden by aggregation. It describes patterns across 660 Middle Layer Super Output Areas (MSOAs); NB: It does not explain any individual's health or establish causes.

I want what's in this project to be available to people who work with data and to people who don't. So the dashboard has two views. It opens in the **Plain view**: a short list of plain questions, such as where people have the fewest years in good health, each answered in a sentence or two without jargon. The **Detailed view**, one click away, keeps the full technical dashboard, with every measure, the uncertainty ranges and the data tables.

Running Signal Box over real work also showed up its own weak spots. The pop-up never said how to clear an orange lamp, and nothing defined what earned a yellow one. I fixed both on 19 October 2026, so this project is partly a test of whether the tool does its job.

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

I wrote this for people who know Birmingham and its neighbouring West Midlands areas, including residents and people who work with local data or services. Some of them work with data and some don't, so each gets a different way in.

**If you don't work with data**, start with the [dashboard](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/dashboard/). It opens in the Plain view. Pick a question from "What would you like to know?" and the answer comes back in a sentence or two, with the map showing what it's talking about. Click any area and you get one plain sentence about it. Uncertainty is described the way a weather forecast would describe it: an area is "clearly", "probably" or "possibly" among the lowest. On the story pages, every chapter opens with an "In short" box.

**If you do**, one click on Detailed view gets you the full technical dashboard: every measure, the rank ranges, the data tables and the CSV download. The story chapters carry the reasoning. The nine notebooks carry the calculations, and you can re-run them.

The Plain view leaves the model's predictions out on purpose. A predicted figure next to a real one reads like a verdict on a place: it's doing worse than it should. The model can't carry that weight, and Signal Box flagged the risk (Q14, outputs treated as proof). The predictions stay in the notebooks, with their limits stated, for readers who can weigh them.

Three testers tried the site and the Detailed view on 20 October 2026 and found every task clear (section 11).

## 4. Results of applying Signal Box

My first application of Signal Box recorded **17 concerns** and **10 no-flags**. In Unit 3, after the say-it-out-loud re-test, **14 are investigated and recorded**, **3 remain open by decision (Q4, Q18 and Q21)**, and **10 remain no-flags**. A recorded response does not mean the risk has gone; a no-flag does not prove safety. Signal Box is a screening aid, not a legal assessment.

Before I turn a lamp yellow, I must be able to say what could go wrong, who it would happen to, what deals with it, and who is responsible. If I cannot say that in a sentence or two, the lamp stays orange. Applying this sharper test moved Q4 back to orange; that is a finding of testing the tool on my own work.

I looked at each of the three and decided to go ahead anyway:

- **Q4 — Benefit to me, cost to others:** I gain assessment and portfolio evidence while people in named areas could bear stigma. I accept that as the cost of trying to get to the truth about these differences, and I keep it down with broad labels, honest uncertainty and a policy on naming places.
- **Q18 — Affected people left out of design and testing:** The study covers 660 areas and several million people. There's no practical way to involve them all, and publishing area-level statistics doesn't need their permission.
- **Q21 — Tested only in a demo, not real use:** This is a course project, built to be assessed, not for anyone to rely on, so it won't be tested in real use.

The guide develops the Code Institute LMS lesson “Ethical considerations in AI” with independent research, including UNESCO’s AI ethics Recommendation, the OECD AI Principles, NIST’s AI Risk Management Framework, UK GDPR changes under the Data (Use and Access) Act 2025, ICO guidance and the EU AI Act. It is independent study material, not official Code Institute material; its legal checks are dated 14 October 2026.

![The Unit 2 and Unit 3 Signal Box boards: 17 original concerns and 10 no-flags; in Unit 3, 14 are investigated and recorded, three remain open by decision (Q4, Q18 and Q21), and 10 remain no-flags.](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/assets/img/second-look/signal-box-before-after.png)

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
- **Tableau Public:** [Birmingham HLE](https://public.tableau.com/views/BirminghamHLEFinal/Dashboard1). This Tableau dashboard was created for Unit 2 and is included here unchanged. The Plain view for non-technical readers is in the main dashboard on the project site; the Tableau workbook is a supporting technical view for readers who want to explore the data in a BI tool.

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

The project was tested on Python 3.14.7 and requires Python 3.12 or later. For a fresh copy, create and activate a virtual environment, then install the pinned packages and notebook tooling:

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

User testing is complete. On 20 October 2026, three testers ran the QA test on the live site and rated every task green: 18 out of 18. The test was built before the Plain view existed, so it covers the Detailed view (the full technical dashboard) and the story pages. The anonymised results are in [data/testing](data/testing/). The results don't close Q4, Q18 or Q21, which stay open by decision (section 4). Before testing, my own review of the dashboard and site led to fixes for search, labels, navigation and plain-English wording.

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
| **2.1 — Explain insights to technical and non-technical readers** | The [dashboard](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/dashboard/)'s Plain view (plain questions with plain answers) and Detailed view (the full technical dashboard), described in [section 3](#3-audience); user testing with three testers, all tasks green ([section 11](#user-testing)); this README, the plain-language sections in [Why a second look](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s1-why-a-second-look.html), [The method](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s2-the-method.html) and [Results at a glance](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/s3-results-at-a-glance.html), [How certain are the rankings](https://tidyweb.github.io/Birmingham-Healthy-Life-Second-Look/story/how-certain-are-the-rankings.html), and the notebook pages. |
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
