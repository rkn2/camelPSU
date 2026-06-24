# Deliverables

Full narrative descriptions. For current status see `STATE.json → deliverables[]`.

---

## D1 — Python Notebook Telemetry Framework

**Due:** End of Year 1 (December 2027) — operational for pilot  
**Owner:** Becca (Napolitano)  
**Type:** Software

### Description
The telemetry layer hooks directly into the IPython kernel to capture timestamped revision histories, cell-level code diffs, interpreter errors and warnings, execution patterns, and inactivity/idle timers. Data is transmitted via asynchronous API calls to a centralized FastAPI backend. The system flags "unproductive frustration" when a student triggers consecutive errors in a single cell or remains inactive for multiple minutes. Must be operational before Year 1 pilot data collection (Fall 2027).

### Success criteria
- Framework captures timestamped events at cell-execution granularity
- FastAPI backend receives and stores JSONL streams
- Teacher dashboard shows real-time class-level progress
- No data loss during typical 45-minute classroom session

### Dependencies
- Server infrastructure (Penn State ICDS)
- IRB approval (must precede any student data collection)

---

## D2 — Composable Courseware Modules (Algebra + Statistics)

**Due:** Year 1 summer (for teacher PD); complete by end Year 2  
**Owner:** Wesley Reinhart (architecture); Becca (integration)  
**Type:** Software + curriculum

### Description
YAML-manifest-driven Python notebook framework with plug-and-play components (context, dataset, model, analysis). L01-02 already implemented and deployed from prior work; L03 prototyped. Two industrial contexts: (1) AFM/materials data from 2DCC-MIP for statistical complexity; (2) cooling system time-series from Zuo for structural/provenance complexity. Complexity dials allow swapping dataset, model type, and number of variables without full rewrite.

### Success criteria
- At least 2 complete modules ready for Year 1 summer institute
- Teachers can successfully run modules in summer PD without researcher support
- Agentic AI tool integrated for patching transitions and updating narrative cells
- Full suite complete for all listed partner schools by Year 2

### Dependencies
- Dataset preparation (Reinhart: 2DCC LiST; Zuo: campus cooling + data center)
- D1 (telemetry must hook into the notebooks)

---

## D3 — Teacher Professional Development Program

**Due:** Summer 2027 (Year 1 institute); Year 2 expanded cohort  
**Owner:** Kathy Hill, Robert Mayne, Amber Cesare  
**Type:** Educational program

### Description
One-week summer institutes at Penn State where teachers work directly with engineering faculty and authentic datasets through the full modeling cycle. Year 1: 10 math teachers from rural PA districts. Year 2: 35 additional teachers (total 45). Academic-year NEIC (Networked Evaluation and Improvement Community) with monthly virtual meetings using PDSA cycles. Teachers are trained as co-researchers: annotation protocols, data ethics, systematic documentation.

### Success criteria
- Year 1: ≥10 teachers complete summer institute; NEIC running monthly
- Teachers successfully implement modules in their Algebra/Statistics courses
- Fidelity of Implementation (FoI) protocol deployed and tracked
- Year 2: ≥35 additional teachers onboarded

### Dependencies
- D2 (modules must exist for PD content)
- School partnership agreements (7 districts committed)

---

## D4 — Pilot Dataset (Year 1)

**Due:** End of Year 1 (December 2027)  
**Owner:** Becca + James Yao  
**Type:** Dataset

### Description
Pilot data from 2 sites (~100 students total): one Title I school and one rural school. Data includes process-level telemetry, pre/post assessments, student work artifacts, classroom observation data. This round establishes inter-rater reliability (Cohen's κ ≥ 0.70) and refines protocols before full-scale collection.

### Success criteria
- ~100 students across 2 sites
- All 4 data layers collected (telemetry, assessments, artifacts, observations)
- Inter-rater reliability established (Cohen's κ ≥ 0.70 on 20% double-coded)
- Protocol refinements documented for Year 2

### Dependencies
- D1 (telemetry operational)
- D2 (modules deployed in classrooms)
- D3 (teachers trained)
- IRB approval

---

## D5 — Full Student Math Modeling Learning Dataset

**Due:** End of Year 3 (December 2029)  
**Owner:** Becca + James Yao  
**Type:** Dataset (major deliverable)

### Description
Multi-layered, AI-ready dataset from ~4,500 students across all partner schools. Five linked components: (1) process-level notebook telemetry (tens of millions of events; several tens of GB JSONL), (2) pre/post assessments, (3) student work artifacts, (4) classroom and implementation metadata, (5) structured expert annotations. FAIR-compliant, published on ICPSR and OSF with CC-BY license, tutorial notebooks, and analysis scripts.

### Success criteria
- ~4,500 students represented
- Tens of millions of annotated events
- All five data layers present with codebooks
- Cross-site validation complete; bias audit documented
- Published on ICPSR with DOI, OSF, GitHub (sample scripts)
- Tutorial notebooks allow new researcher to run analysis within hours of access

### Dependencies
- D4 (pilot established protocols)
- D6 (annotation protocols complete)
- D7 (Data Translation Framework published)
- IRB coverage for all sites

---

## D6 — Annotation Protocols + Codebook

**Due:** Year 2 (initial); Year 3 (final validated version)  
**Owner:** James Yao + Becca  
**Type:** Methodology document

### Description
AI-ready annotation protocols aligned with xAPI and Caliper standards. Includes: Reasoning Pattern Codes (assumption-making, variable identification, validation); Error Taxonomy (statistics education taxonomy for data handling, modeling, interpretation errors); Productive Struggle Indicators (specific revision cycles, exploratory patterns); Model Quality Metrics (fit statistics, code quality). Organized along three complexity dimensions (statistical, structural, provenance).

### Success criteria
- Codebook enables reliable annotation by non-expert coders (κ ≥ 0.70)
- xAPI/Caliper alignment documented
- Compatible with intelligent tutoring system training requirements
- Published as open-access guide on OSF

### Dependencies
- Year 1 pilot data (needed to ground and test codes)
- Literature review on learning analytics standards

---

## D7 — Data Translation Framework

**Due:** Year 3 (documented protocol published)  
**Owner:** Becca  
**Type:** Methodology document (not software)

### Description
Replicable framework for converting high-dimensional engineering research data into K-12 pedagogical materials. Components: (1) decision rubrics for dataset selection, (2) scaffolding templates, (3) learning analytics integration specifications, (4) validation checklists. Includes three complexity dials: statistical, structural, and provenance — each with teacher-adjustable settings. Published as open-access methodological guide on OSF; also submitted to Journal of Research in Mathematics Education and Educational Researcher.

### Success criteria
- Practitioners can use framework to adapt a new engineering dataset without researcher support
- Framework validated by Practitioner Review Board (quarterly NEIC audits)
- Published on OSF with CC-BY license
- At least one peer-reviewed methodology paper submitted

### Dependencies
- D3 (teacher feedback over 2 years shapes framework)
- D4 pilot data (early validation)

---

## D8 — Proof-of-Concept Classifier

**Due:** Year 3  
**Owner:** James Yao + Becca  
**Type:** Software / research output

### Description
Simple classifier (random forest or logistic regression) trained to predict productive vs. unproductive struggle from process features in the telemetry. Demonstrates the dataset's utility for AI applications. This is a proof-of-concept, not the primary contribution — it validates the "AI-ready" claim.

### Success criteria
- Classifier trained and evaluated on the full dataset
- Performance metrics reported (precision, recall, AUC)
- Results submitted for peer review
- Training pipeline deposited on GitHub with DOI

### Dependencies
- D5 (full dataset)
- D6 (annotations must exist to define labels)

---

## D9 — Publications

**Due:** Ongoing (Years 2–3)  
**Owner:** Becca + James Yao (primary authors)  
**Type:** Publications

### Description
**Primary empirical findings (RQ1):** Journal of the Learning Sciences, Cognition and Instruction  
**Methodological contributions (RQ2):** Journal of Research in Mathematics Education, Educational Researcher  
**Dataset descriptor papers:** Journal of Educational Data Mining, NeurIPS education workshops  
**Conference presentations:** ICLS, NARST, PME (annual)

### Success criteria
- At least 1 empirical paper submitted by end Year 2
- At least 1 methods paper submitted by end Year 2
- Dataset descriptor submitted upon dataset publication
- Conference presentations at ≥1 venue per year

---

## D10 — Project Website

**Due:** Year 1 (launch); maintained throughout  
**Owner:** Becca + Jeff Remington  
**Type:** Website

### Description
Public project website with documentation, researcher forum, dataset information, and links to curriculum materials and publications. Serves as primary public-facing presence of the network.

### Success criteria
- Launched Year 1 (before pilot data collection)
- Updated with milestones as they complete
- Linked from CAMEL cross-network activity page

---

## D11 — Phase II Proposal

**Due:** Year 3  
**Owner:** Becca  
**Type:** Grant proposal

### Description
Phase II CAMEL-CN proposal building on established data infrastructure, school partnerships, and demonstrated capacity. Leverages the full dataset, framework, and network to propose expanded scope.

### Dependencies
- D5 (dataset must demonstrate proof of concept)
- D7 (framework must be validated)
- NSF CAMEL Phase II solicitation timeline
