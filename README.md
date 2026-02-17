# Awesome Health AI Evaluation [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of frameworks, standards, and methods for evaluating health AI systems — from study design to post-deployment monitoring.

Despite 1,000+ FDA-authorized AI/ML medical devices, the evidence base for health AI remains thin. 24.1% of authorized devices have zero published clinical studies. Reporting transparency scores average 3.3/17. This list curates the evaluation frameworks, reporting standards, study designs, and evidence chain methods needed to build rigorous health AI evidence.

**RAIGH Academy Module:** This list serves as a reference resource for the Clinical AI Evaluation module within the [RAIGH Academy](https://raigh.org) workforce development program.

## Contents

- [The Evidence Problem in Health AI](#the-evidence-problem-in-health-ai)
- [Reporting Standards — The Big 10](#reporting-standards--the-big-10)
- [Study Design Decision Tree](#study-design-decision-tree)
- [Evidence Chain Framework](#evidence-chain-framework)
- [AI + Clinician: Proper Study Design](#ai--clinician-proper-study-design)
- [When Is Imperfect AI Good Enough?](#when-is-imperfect-ai-good-enough)
- [Model Card Framework](#model-card-framework)
- [Curated Model Registry](#curated-model-registry)
- [Structured Data](#structured-data)
- [Training & Certification](#training--certification)
- [Methodology](#methodology)
- [Contribute & Publish](#contribute--publish)
- [Sister Repositories](#sister-repositories)

---

## The Evidence Problem in Health AI

Seven landmark studies reveal critical gaps in health AI device evaluation:

| Study | Finding | Implication |
|---|---|---|
| Wu et al. (2021) | **24.1% of FDA-authorized AI/ML devices had zero published clinical studies** | Devices in clinical use without evidence |
| Muehlematter et al. (2021) | **Average transparency score: 3.3/17** for AI device regulatory submissions | Minimal information available to clinicians |
| Siontis et al. (2021) | **96.4% missing demographics data** in AI-ECG validation studies | Unknown performance across populations |
| Nagendran et al. (2020) | **Only 25%** of diagnostic AI studies compared AI with clinicians using same data | Most comparisons are unfair |
| Liu et al. (2019) | **94% of studies at high risk of bias** (PROBAST assessment) | Methodological quality crisis |
| Kelly et al. (2019) | **Lack of prospective validation** across nearly all health AI systems | Lab performance ≠ clinical performance |
| Topol (2019) | **Fundamental mismatch** between benchmark performance and clinical outcomes | Need outcome-focused evaluation |

**Key resources:**
- [Topol Review (2019)](https://doi.org/10.1038/s41591-018-0300-7) — "High-performance medicine: the convergence of human and artificial intelligence"
- [Liu et al. (2019)](https://doi.org/10.1016/S2589-7500(19)30123-2) — "A comparison of deep learning performance against health-care professionals"
- [Nagendran et al. (2020)](https://doi.org/10.1136/bmj.m689) — "Artificial intelligence versus clinicians: systematic review"
- [Wu et al. (2021)](https://doi.org/10.1038/s41591-021-01312-x) — "How medical AI devices are evaluated: limitations and recommendations"
- [FDA AI/ML Action Plan](https://www.fda.gov/medical-devices/software-medical-device-samd/artificial-intelligence-and-machine-learning-aiml-software-medical-device)

---

## Reporting Standards — The Big 10

Ten reporting standards form the foundation of health AI evidence quality:

| Standard | Full Name | Purpose | Year | Checklist |
|---|---|---|---|---|
| **TRIPOD+AI** | Transparent Reporting of a multivariable prediction model for Individual Prognosis Or Diagnosis + AI | Prediction model development and validation | 2024 | [Checklist](https://www.tripod-statement.org/) |
| **CONSORT-AI** | Consolidated Standards of Reporting Trials + AI | Randomized trials of AI interventions | 2020 | [Checklist](https://www.consort-statement.org/) |
| **SPIRIT-AI** | Standard Protocol Items: Recommendations for Interventional Trials + AI | Protocols for AI clinical trials | 2020 | [Checklist](https://www.spirit-statement.org/) |
| **STARD-AI** | Standards for Reporting of Diagnostic Accuracy Studies + AI | Diagnostic accuracy studies | 2021 | [Checklist](https://www.equator-network.org/reporting-guidelines/stard/) |
| **DECIDE-AI** | Developing and Evaluating Communication strategies to support Informed DEcisions + AI | Early-stage clinical evaluation | 2022 | [Checklist](https://doi.org/10.1038/s41591-022-01772-8) |
| **PROBAST+AI** | Prediction model Risk Of Bias Assessment Tool + AI | Risk of bias assessment | 2019+ | [Tool](https://www.probast.org/) |
| **CLAIM** | Checklist for Artificial Intelligence in Medical Imaging | AI in medical imaging | 2020 | [Checklist](https://doi.org/10.1148/ryai.2020200029) |
| **PRISMA 2020** | Preferred Reporting Items for Systematic Reviews and Meta-Analyses | Systematic reviews of AI studies | 2021 | [Checklist](http://www.prisma-statement.org/) |
| **CHEERS 2022** | Consolidated Health Economic Evaluation Reporting Standards | Health economic evaluation of AI | 2022 | [Checklist](https://doi.org/10.1016/j.jval.2021.11.1351) |
| **TRIPOD-Cluster** | TRIPOD for clustered data and models | Multi-site prediction models | 2023 | [Statement](https://www.tripod-statement.org/) |

**Key resources:**
- [EQUATOR Network](https://www.equator-network.org/) — Central hub for all health research reporting guidelines
- [CONSORT-AI Extension](https://doi.org/10.1038/s41591-020-1034-x) — Liu et al. (2020), Nature Medicine
- [SPIRIT-AI Extension](https://doi.org/10.1038/s41591-020-1037-7) — Rivera et al. (2020), Nature Medicine
- [TRIPOD+AI Statement](https://doi.org/10.1136/bmj-2023-078378) — Collins et al. (2024), BMJ
- [DECIDE-AI Framework](https://doi.org/10.1038/s41591-022-01772-8) — Vasey et al. (2022), Nature Medicine
- [CLAIM Checklist](https://doi.org/10.1148/ryai.2020200029) — Mongan et al. (2020), Radiology: AI

---

## Study Design Decision Tree

Choosing the right study design for health AI evaluation:

```
Is this a PREDICTION MODEL?
├── Yes → DEVELOPMENT study?
│   ├── Yes → Use TRIPOD+AI (Type 1a/1b)
│   └── No → EXTERNAL VALIDATION?
│       ├── Yes → Use TRIPOD+AI (Type 2a/2b/3/4)
│       └── No → CLINICAL IMPACT study?
│           ├── Yes → Proceed to intervention design ↓
│           └── No → Consider SYSTEMATIC REVIEW → Use PRISMA 2020
│
Is this an INTERVENTION STUDY (AI changes clinical decisions)?
├── RCT feasible?
│   ├── Yes → Standard parallel RCT?
│   │   ├── Yes → Use CONSORT-AI
│   │   └── No → Cluster-randomized?
│   │       ├── Yes → Use CONSORT-AI + cluster extension
│   │       └── No → Stepped-wedge?
│   │           ├── Yes → Use CONSORT-AI + stepped-wedge extension
│   │           └── No → Consider pragmatic design → Use PRECIS-2 tool
│   └── No → DECIDE-AI (early-stage clinical evaluation)
│
Is this a DIAGNOSTIC ACCURACY study?
├── Yes → Use STARD-AI
│
Is this a RISK OF BIAS assessment?
├── Yes → Use PROBAST+AI
│
Is this a MEDICAL IMAGING AI study?
├── Yes → Use CLAIM
│
Is this a COST-EFFECTIVENESS study?
├── Yes → Use CHEERS 2022
```

**Key resources:**
- [PRECIS-2](https://www.precis-2.org/) — Pragmatic-Explanatory Continuum Indicator Summary for pragmatic trial design
- [NIH Study Design Guide](https://www.nhlbi.nih.gov/health-topics/study-quality-assessment-tools) — Study quality assessment tools
- [Cochrane Handbook](https://training.cochrane.org/handbook) — Gold standard for systematic review methodology

---

## Evidence Chain Framework

A 5-phase framework for building complete health AI evidence:

```
Phase 1: DEVELOPMENT
├── Training/validation split (temporal, geographic, demographic)
├── Report: TRIPOD+AI Type 1a/1b
├── Metrics: AUROC, calibration, subgroup performance
├── Output: Internal validation paper
│
Phase 2: EXTERNAL EVALUATION
├── Independent dataset(s) — different site, time, population
├── Report: TRIPOD+AI Type 2a/2b/3
├── Metrics: Same as Phase 1 + distribution shift analysis
├── Output: External validation paper
│
Phase 3: EARLY CLINICAL EVALUATION
├── Real clinical environment, prospective
├── Report: DECIDE-AI
├── Focus: Usability, workflow integration, failure modes, clinician interaction
├── Metrics: Alert fatigue, override rate, time-to-decision
├── Output: DECIDE-AI study
│
Phase 4: RANDOMIZED CONTROLLED TRIAL
├── AI-assisted vs standard care
├── Report: CONSORT-AI (protocol: SPIRIT-AI)
├── Designs: Parallel RCT, cluster-randomized, stepped-wedge, non-inferiority
├── Metrics: Patient outcomes, resource utilization, cost-effectiveness
├── Output: RCT publication + CHEERS 2022 if economic evaluation
│
Phase 5: POST-DEPLOYMENT MONITORING
├── Continuous performance monitoring in production
├── Framework: RE-AIM (Reach, Effectiveness, Adoption, Implementation, Maintenance)
├── Metrics: Model drift, subgroup performance, adverse events, override telemetry
├── Output: Post-market surveillance report
```

**Key resources:**
- [RE-AIM Framework](https://re-aim.org/) — Framework for evaluating real-world impact of health interventions
- [Park et al. (2020)](https://doi.org/10.1148/radiol.2020192224) — "Methodologic Guide for Evaluating Clinical Performance and Effect of AI Technology for Medical Diagnosis and Prediction"
- [Vasey et al. (2022)](https://doi.org/10.1038/s41591-022-01772-8) — DECIDE-AI guideline for early clinical evaluation

---

## AI + Clinician: Proper Study Design

Five study designs for evaluating AI in clinical workflows:

### 1. Human-AI Collaboration Study

How does clinician performance change WITH vs WITHOUT AI assistance?

| Design Element | Detail |
|---|---|
| Arms | Clinician alone vs Clinician + AI |
| Randomization | By case (crossover) or by clinician (parallel) |
| Primary outcome | Diagnostic accuracy, time-to-decision |
| Key metric | Net reclassification index (how many cases correctly changed?) |
| Reporting | CONSORT-AI |

### 2. Override Analysis (Clinician Autonomy Taxonomy)

How do clinicians interact with AI recommendations?

| Override Type | Description | What It Measures |
|---|---|---|
| Type 0 | AI output not shown | Baseline human performance |
| Type 1 | AI output shown, no action required | Anchoring effect |
| Type 2 | AI output shown, clinician must acknowledge | Attention to AI output |
| Type 3 | AI output shown, clinician must give reason to disagree | Deliberate override |
| Type 4 | AI output with mandatory follow protocol unless override documented | High-autonomy AI |
| Type 5 | AI acts autonomously with human notification | Full autonomy |

### 3. Counterfactual / Causal Study

What would have happened if the AI recommendation had been followed?

- Retrospective analysis of cases where AI was available but overridden
- Compare outcomes: AI-concordant decisions vs AI-discordant decisions
- Must control for severity bias (sicker patients more likely to override)
- Use propensity score matching or instrumental variable approaches

### 4. Stepped-Wedge Cluster RCT

Sequential rollout of AI across clinical sites:

- All sites start without AI (control period)
- Sites sequentially cross over to AI at random time points
- Each site serves as its own control
- Ideal for health AI where simultaneous rollout is impractical

### 5. Decision Curve Analysis (DCA)

When is using the AI model better than treating-all or treating-none?

- Plots net benefit across threshold probabilities
- Shows the range where the AI model adds clinical value
- Does not require choosing a single classification threshold
- Standard for clinical prediction model utility assessment

**Key resources:**
- [Vickers & Elkin (2006)](https://doi.org/10.1177/0272989X06295361) — Original DCA paper
- [Gaube et al. (2021)](https://doi.org/10.1038/s41746-021-00385-9) — AI advice and clinician decision-making
- [Tschandl et al. (2020)](https://doi.org/10.1038/s41591-020-0942-0) — Human-computer collaboration for skin cancer diagnosis

---

## When Is Imperfect AI Good Enough?

In resource-limited settings, perfect evidence may be an impossible standard. When should imperfect AI be deployed?

### The Ethical Framework

| Principle | Source | Application |
|---|---|---|
| **WHO 6 Principles** | WHO (2021) | Autonomy, well-being, transparency, responsibility, inclusiveness, sustainability |
| **Rescue Ethics** | Clinical ethics | When the alternative is NO diagnostic capability, lower evidence thresholds may be justified |
| **Outcome Definition** | Methodological | GCS at discharge is a poor outcome measure — need long-term outcomes (CBI-M, GOSE at 6 months) |
| **AI + Human vs Human Alone** | Reframe | The right comparison is NOT "AI vs specialist" but "AI-augmented generalist vs generalist alone" |

### Decision Factors

1. **What is the alternative?** If no radiologist is available (e.g., rural Africa), even 70% accurate AI may save lives
2. **What is the failure mode?** False negatives (missed findings) vs false positives (unnecessary referrals) have different consequences
3. **Can the AI abstain?** An AI that says "I'm not sure, refer this case" is safer than one that always outputs a prediction
4. **Is there human oversight?** AI as decision support (with override) vs AI as autonomous agent require different evidence
5. **What is the patient population?** Performance in training population may not transfer to deployment population

### The Abstention Principle

AI systems that can abstain (say "I don't know") are fundamentally safer:

- **Conformal prediction** provides guaranteed coverage at specified confidence levels
- **Selective prediction** reduces errors by abstaining on uncertain cases
- **Calibration** ensures predicted probabilities match observed frequencies

**Key resources:**
- [WHO Ethics & Governance of AI for Health (2021)](https://www.who.int/publications/i/item/9789240029200)
- [Babic et al. (2021)](https://doi.org/10.1038/s41591-021-01316-7) — "Algorithms on regulatory lockdown in medicine"
- [Vayena et al. (2018)](https://doi.org/10.1038/s41591-018-0246-6) — "Machine learning in medicine: addressing ethical challenges"
- [Char et al. (2018)](https://doi.org/10.1056/NEJMp1714229) — "Implementing Machine Learning in Health Care — Addressing Ethical Challenges"

---

## Model Card Framework

Standardized documentation for health AI models:

### Template Fields

| Field | Description | Source |
|---|---|---|
| Model Details | Name, version, type, developers, date, license | Google Model Cards |
| Intended Use | Primary use cases, out-of-scope uses | Google Model Cards |
| Training Data | Sources, size, demographics, temporal range, geographic scope | Google + FDA |
| Evaluation Data | Validation datasets, external datasets, subgroup coverage | TRIPOD+AI |
| Performance Metrics | Discrimination, calibration, clinical utility, fairness | This repo |
| Ethical Considerations | Bias analysis, demographic parity, equalized odds | IEEE 2894 |
| Caveats & Recommendations | Known limitations, deployment conditions, monitoring | FDA Transparency |
| Evidence Chain Status | Phase (1-5), reporting standards used, gaps | This repo |
| Regulatory Status | FDA/CE/other authorization, PCCP applicability | Regulatory data |

### Existing Frameworks

- [Google Model Cards](https://modelcards.withgoogle.com/about) — Mitchell et al. (2019). Original model card framework
- [Hugging Face Model Cards](https://huggingface.co/docs/hub/model-cards) — Standardized model documentation for ML community
- [FDA Transparency Requirements](https://www.fda.gov/medical-devices/digital-health-center-excellence/transparency-machine-learning-enabled-medical-devices) — US FDA labeling for AI medical devices
- [EU AI Act Article 11](https://artificialintelligenceact.eu/) — Technical documentation requirements for high-risk AI
- [HL7 EHI Framework](https://www.hl7.org/) — Health-specific model documentation standards

### Templates

See [`data/templates/model-card-template.yaml`](data/templates/model-card-template.yaml) for a health AI model card template.

---

## Curated Model Registry

Notable health AI models with evidence chain status:

| Model | Developer | Domain | FDA | Phase | Key Gap |
|---|---|---|---|---|---|
| Viz.ai LVO | Viz.ai | Stroke detection | Yes (2018) | 4 | Limited LMIC validation |
| IDx-DR | Digital Diagnostics | Diabetic retinopathy | Yes (2018) | 4 | First autonomous AI, single-disease |
| Qure.ai qXR | Qure.ai | Chest X-ray | Yes (2020) | 3 | Strong LMIC data, limited RCTs |
| Caption Health | Caption Health | Echocardiography | Yes (2020) | 3 | Novel AI-guided acquisition |
| Paige.AI Prostate | Paige.AI | Pathology | Yes (2021) | 3 | First AI in pathology |
| Eko AI | Eko Health | Cardiac murmur | Yes (2020) | 3 | Point-of-care stethoscope |
| BRIDGE-TBI | EvidenceOS | TBI triage | No | 2 | External validation ongoing |
| Brainomix e-Stroke | Brainomix | Stroke imaging | CE (2019) | 3 | European-focused |
| Annalise.ai CXR | Annalise.ai | Chest X-ray (124 findings) | CE (2022) | 3 | Broadest CXR coverage |

*Note: Evidence chain phases are assessments based on publicly available literature, not endorsements.*

---

## Structured Data

This repository includes machine-readable evaluation data in the [`data/`](data/) directory:

```
data/
├── standards/
│   ├── tripod-ai-checklist.json     # TRIPOD+AI reporting checklist
│   ├── consort-ai-extensions.json   # CONSORT-AI extension items
│   └── claim-checklist.json         # CLAIM imaging AI checklist
├── templates/
│   ├── model-card-template.yaml     # Health AI model card template
│   └── evidence-chain-template.yaml # Evidence chain tracking template
├── models/
│   └── model-registry.json          # Curated model registry with evidence status
├── evidence-gaps/
│   ├── fda-device-limitations.json  # Key studies on FDA device evidence gaps
│   └── evidence-chain-scorecard.json # Evidence chain phase by device category
├── study-designs/
│   ├── decision-tree.json           # Study design decision tree
│   └── override-taxonomy.json       # Clinician override type taxonomy
└── badges/
    └── badge-definitions.json       # Evidence and evaluation badges
```

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidance on adding structured data.

---

## Training & Certification

- [EQUATOR Network Toolkits](https://www.equator-network.org/) — Comprehensive resources for health research reporting. Free courses on CONSORT, PRISMA, TRIPOD
- [Cochrane Training](https://training.cochrane.org/) — Gold standard systematic review methodology. Free online learning modules
- [Good Clinical Practice (GCP)](https://www.ema.europa.eu/en/human-regulatory/research-development/compliance/good-clinical-practice) — ICH E6(R2) training for clinical trial conduct
- [Coursera: AI in Healthcare](https://www.coursera.org/specializations/ai-healthcare) — Stanford. Includes evaluation and evidence quality modules
- [edX: Statistics and Data Science](https://www.edx.org/micromasters/mitx-statistics-and-data-science) — MIT MicroMasters. Statistical methods for clinical AI evaluation
- [NIH Clinical Research Training](https://clinicalcenter.nih.gov/training/) — Principles and Practice of Clinical Research
- [WHO OpenWHO](https://openwho.org/) — Free courses on health research methods, clinical trials, and evaluation
- [OHDSI Resources](https://www.ohdsi.org/past-events/) — Training on OMOP CDM, observational study methods
- [fast.ai Practical Deep Learning](https://course.fast.ai/) — Practical ML course with model evaluation emphasis
- [RAIGH Academy](https://raigh.org) — PAATHI workforce development program. Clinical AI Evaluation module covers evidence chain framework, reporting standards, study design for health AI

---

## Methodology

This list is curated using a combination of **agentic extraction** and **human validation**:

1. **Agentic Extraction** — Automated search across PubMed, Cochrane Library, EQUATOR Network, and grey literature using the EvidenceOS systematic review pipeline
2. **Knowledge Graph Integration** — Resources are linked to entities (reporting standards, study designs, evidence phases, diseases) to identify coverage gaps
3. **Human Validation** — Every resource is reviewed by at least one clinical research methodologist before inclusion
4. **Continuous Update** — GitHub Actions scan for new reporting guidelines and evaluation studies weekly; community PRs reviewed by AI + human

We are conducting a **Human vs AI Curation Study** comparing manual evidence mapping against agentic extraction. Results will be published as a companion paper.

---

## Contribute & Publish

We invite clinical researchers, methodologists, and students to participate in our **Human vs AI Curation Study**:

- **What:** Compare your manual curation of health AI evaluation resources against our agentic extraction pipeline
- **How:** Fork this repo, add evaluation frameworks or model evidence assessments, submit a PR
- **Outcome:** Co-authorship eligibility on "A Systematic Analysis of the Health AI Evidence Landscape" paper
- **Measurement:** Inter-rater reliability (Krippendorff's alpha) between AI and human curators

Top contributors (5+ validated resources) are eligible for RAIGH Academy Campus Lead status. See [CONTRIBUTING.md](CONTRIBUTING.md) for details.

---

## Sister Repositories

| Repository | Focus | RAIGH Module |
|---|---|---|
| [awesome-african-digital-health](https://github.com/EvidenceOS/awesome-african-digital-health) | African digital health landscape | Digital Health Foundations |
| [awesome-dpi-infrastructure](https://github.com/EvidenceOS/awesome-dpi-infrastructure) | DPI platforms & protocols | DPI Architecture |
| [awesome-health-ai-regulations](https://github.com/EvidenceOS/awesome-health-ai-regulations) | Health AI regulatory frameworks | Regulatory Navigator |
| **awesome-health-ai-evaluation** (this repo) | Health AI evaluation methods | Clinical AI Evaluation |
| [awesome-ai-evaluation-metrics](https://github.com/EvidenceOS/awesome-ai-evaluation-metrics) | AI evaluation metrics taxonomy | AI Fundamentals & Metrics |

---

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the authors have waived all copyright and related rights to this work. See [LICENSE](LICENSE).
