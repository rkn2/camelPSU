# CAMEL-CN Project Showcase — July 28, 2026
**Modeling the Messy: Capturing Student Reasoning within High-Dimensional Industrial AI Datasets**
NSF Award #2621173 | Phase I | Penn State University | 12-minute presentation

---

## Slide 1 — Title
**Modeling the Messy**
Capturing Student Reasoning within High-Dimensional Industrial AI Datasets

NSF CAMEL Phase I | Penn State University
Napolitano · Yao · Reinhart · Zuo · Hill

---

## Slide 2 — Team Members

| Name | Institution | Expertise |
|------|-------------|-----------|
| Rebecca (Becca) Napolitano | Penn State — AE | Data translation; Python/notebook education; learning analytics |
| Xiangquan (James) Yao | Penn State | Science of learning; cognitive science; educational measurement |
| Wesley F. Reinhart | Penn State — MSE | FAIR data; scientific AI; Composable Courseware architecture |
| Wangda Zuo | Penn State — AE | Energy systems; cyber-physical datasets; industrial AI |
| Kathleen (Kathy) Hill | Penn State CSATS | K-12 teacher PD; rural school partnerships; practitioner implementation |
| Amber Cesare | CSATS | Curriculum integration; complexity dial tuning; field liaison |
| Jeff Remington | CSATS | School outreach; district relationships; NEIC facilitation |

---

## Slide 3 — Network Partners

**School Partners (7 rural PA districts):**
- Keystone Central: Bucktail MS/HS (100% econ. disadvantaged) + Central Mountain HS
- Juniata Valley / Juniata County / Hollidaysburg / Lewisburg Area / Philipsburg-Osceola / Jersey Shore Area

**Data & Infrastructure Partners:**
- 2DCC-MIP (Penn State) — materials science AFM datasets
- Penn State ICDS — compute and storage infrastructure

---

## Slide 4 — The K-12 Math Problem

Real-world data is messy. Textbook data isn't.

Students learn math with sanitized, curated datasets — but the data that matters in science, engineering, and industry is high-dimensional, noisy, and complex. This gap means students don't develop authentic mathematical modeling competency — the ability to reason with real-world complexity.

**Our focus:** Algebra and Statistics students in rural, high-poverty PA schools
(Math proficiency rates: 12–47% across partner districts)

**Research Questions:**
1. How do students develop mathematical modeling competencies with complex industrial datasets?
2. What infrastructure (data translation frameworks, annotation protocols) is required to study this at scale?

---

## Slide 5 — What Data We're Building

**A 5-layer, AI-ready dataset of student mathematical modeling**

Two industrial contexts:
- **Materials science:** AFM data from Penn State's 2D Crystal Consortium (Reinhart)
- **Energy systems:** Campus cooling + data center time-series (Zuo)

**Five linked data layers:**
1. Process-level notebook telemetry — cell executions, code diffs, errors, idle time (tens of millions of events)
2. Pre/post mathematical modeling assessments
3. Student work artifacts (completed Jupyter notebooks)
4. Classroom/implementation metadata (teacher fidelity)
5. Expert annotations — Reasoning Patterns, Error Taxonomy, Productive Struggle Indicators

**Scale:** ~4,500 students | 7 districts | FAIR, CC-BY | Published ICPSR + OSF with DOI

---

## Slide 6 — Current State

We received our award June 22, 2026. We're in the pre-work setup period (July–December 2026).

| Component | Status |
|-----------|--------|
| Composable Courseware L01–L02 | Built (from prior NSF IIS-2123343) |
| School district partnerships | Outreach underway — 7 districts identified |
| Python telemetry framework | Designed — implementation begins Jan 2027 |
| Annotation codebook | Drafted — to be validated in pilot |
| Pilot dataset (~100 students, 2 sites) | Target: Fall 2027 |
| Full dataset (~4,500 students) | Target: End of 2029 |

[PLACEHOLDER: Add any preliminary data/visuals from prior grant IIS-2123343 here]

---

## Slide 7 — How We Draw on Expertise

**Researchers:**
- Yao — cognitive science, science of learning → annotation protocols, RQ1 analysis
- Reinhart — materials science, FAIR data → dataset originator + Composable Courseware architecture
- Zuo — energy systems engineering → second industrial context

**Practitioners:**
- Hill + Cesare + Remington (CSATS) — teacher PD design, school partnerships, fidelity monitoring
- 4–12 math teachers/year as co-researchers — annotating, documenting, shaping the tools
- NEIC — monthly virtual sessions, PDSA cycles, practitioner feedback loop

**Data Scientists:**
- Napolitano — data translation framework (complexity dials, scaffolding templates)
- 2 PhD students — telemetry system + ML classifier
- D8 classifier: proof-of-concept AI trained on our dataset (productive vs. unproductive struggle)

---

## Slide 8 — What We Expect to Work Well

- **We're not starting from zero.** L01–L02 Composable Courseware modules built and tested in college classrooms (IIS-2123343). Phase I adapts them for K-12.
- **Strong school trust already in place.** Kathy Hill's team has existing relationships with all 7 rural districts — this isn't cold outreach.
- **Interdisciplinary team with shared track record.** Napolitano, Reinhart, and Hill have worked together on a completed NSF grant.
- **Mature telemetry design.** IPython kernel hooks for process-level data capture are well-understood from prior work.

---

## Slide 9 — Biggest Challenges

**1. Data translation is genuinely hard.**
Making industrial datasets pedagogically accessible requires expertise that rarely sits in one person. Our "complexity dials" (statistical, structural, provenance) are the mechanism — calibrating them across 7 districts, multiple teachers, and diverse students is an open research problem.

**2. Annotation at scale requires reproducible standards.**
Labeling student reasoning at scale (Cohen's κ ≥ 0.70 across thousands of sessions) is a substantial infrastructure problem. What counts as "productive struggle" must be precise enough that non-expert coders can apply it reliably.

**3. The logistics chain is tight.**
Every milestone — teacher PD, pilot data collection, full dataset — depends on a chain of IRB approvals, partnership agreements, and hiring that takes months. The critical path is unforgiving.

**Where a collaboratory helps most:**
- Shared annotation standards → pool coding labor across teams
- Cross-team data translation templates → faster complexity dial development
- Shared IRB/data governance models → reduce every team's setup burden

---

## Slide 10 — Magic Wand

[PLACEHOLDER — Becca to write in her own voice]

Draft framing:
*"If we could wave a magic wand: every CAMEL team would adopt the same process-level telemetry schema from day one — a shared event log standard — so that student reasoning data across materials science, climate, and energy contexts could be directly compared. Right now we're each building data infrastructure in parallel. A collaboratory that converges on a common telemetry and annotation layer in Phase I would let Phase II ask questions none of us can ask alone."*

---

*Open items: (1) preliminary data visuals from IIS-2123343; (2) additional challenges from Becca; (3) magic wand in Becca's voice*
