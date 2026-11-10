# GM Pre-Joining AI/ML Preparation Plan

**Preparation period:** November 10–December 6, 2026  
**GM start date:** December 7, 2026  
**Target role:** Senior AI/ML Data Scientist, Global Product Safety, Systems, and Certification (GPSSC)  
**Longer-term goal:** Build credibility at GM and prepare for a Fall 2028 University of Michigan–Dearborn ECE D.Eng. application.

> **Core objective:** Arrive ready to understand product-safety workflows, evaluate GenAI systems rigorously, and contribute to trustworthy AI solutions. Prioritize one well-evaluated project over collecting certificates.

## 1. What success looks like on December 7

By joining day, aim to be able to:

- Explain a retrieval-augmented generation (RAG) pipeline and the trade-offs among lexical search, embedding search, reranking, and grounding.
- Evaluate retrieval quality, classification errors, false negatives, unsupported conclusions, and uncertainty.
- Describe a human-review workflow appropriate for safety-related decisions.
- Reproduce an ML experiment with clear data splits, tests, tracked metrics, and limitations.
- Explain why public vehicle complaints are **not** verified defect findings.
- Demonstrate a lightweight public-data prototype called **SafetyLens**.

**Time budget:** About **10–12 hours/week**, approximately 40–45 hours total. Suggested split: **60% project**, **25% courses**, **15% automotive-domain reading**. Adjust downward if needed; consistency is more important than completion of every optional item.

## 2. Four-week timeline

| Dates | Focus | Learning | Project deliverable | Definition of done |
|---|---|---|---|---|
| **Nov 10–15** | RAG and retrieval fundamentals | DeepLearning.AI *Building and Evaluating Advanced RAG*; Lewis et al. RAG paper | Download and inspect public NHTSA data; implement TF-IDF search | Search returns traceable complaint record IDs |
| **Nov 16–22** | LLM evaluation and testing | DeepLearning.AI *Automated Testing for LLMOps* and *Evaluating and Debugging Generative AI*; RAGAS paper | Create evaluation set, retrieval metrics, and initial text classifier | Baseline metrics and known failure cases documented |
| **Nov 23–29** | Automotive safety, agents, and safeguards | NHTSA datasets; NIST AI RMF; optionally *AI Agents in LangGraph* and *Safe and Reliable AI via Guardrails* | Add semantic search, evidence display, and low-confidence/human-review rules | Retrieval comparison and conservative error handling work |
| **Nov 30–Dec 6** | Reproducibility and demo | Selected Udemy LangChain/LangGraph modules; MLflow and pytest docs | Clean README, tests, experiment log, 5-minute demo | Project runs locally from setup instructions; limitations stated |

**Practical scheduling:** Reserve two 90-minute project blocks and two shorter study blocks each week, plus a weekend review. Do not sacrifice rest immediately before your GM start date.

## 3. Expert-led DeepLearning.AI course shortlist

Take only the modules that help with the project. Video durations are approximate and may change.

| Priority | Course | Why it matters | Link |
|---|---|---|---|
| **1 — Essential** | **Building and Evaluating Advanced RAG** | Retrieval strategies, grounding, evaluation; useful for technical evidence search | https://www.deeplearning.ai/short-courses/building-evaluating-advanced-rag/ |
| **2 — Essential** | **Automated Testing for LLMOps** | Repeatable evaluation, model-based checks, and CI concepts | https://www.deeplearning.ai/short-courses/automated-testing-llmops |
| **3 — Essential** | **Evaluating and Debugging Generative AI** | Experiment tracking, tracing, and error analysis | https://www.deeplearning.ai/courses/evaluating-debugging-generative-ai |
| **4 — Recommended** | **AI Agents in LangGraph** | State, control flow, tool calling, and human-in-the-loop patterns | https://www.deeplearning.ai/courses/ai-agents-in-langgraph |
| **5 — Recommended** | **Safe and Reliable AI via Guardrails** | Output validation, risk controls, and reliability checks | https://www.deeplearning.ai/courses/safe-and-reliable-ai-via-guardrails |

**How to study:** For each course, capture (1) one concept, (2) one trade-off, (3) one evaluation idea, and (4) one change to SafetyLens. Implement the change before moving on.

## 4. Udemy shortlist — practical supplements

These are supplementary, not prerequisites. Udemy catalog availability, course titles, reviews, and access through any employer subscription may change. **Do not assume GM provides these courses.**

1. **LangChain & LangGraph AI Engineer: Agents, Agentic RAG & MCP — Eden Marco**  
   https://www.udemy.com/course/langchain/  
   Use selected sections on RAG, LangGraph state, tool use, tracing, and evaluation. Skip basic Python and elaborate agent demonstrations for now.
2. **AI Engineer Production Track: Deploy LLMs & Agents at Scale — Ed Donner / Ligency**  
   https://www.udemy.com/course/generative-and-agentic-ai-in-production/  
   Save most of this for after onboarding, when you know which deployment tools and cloud platforms GM approves. Focus on production architecture and observability if you have extra time.

**Course selection rule:** Prefer technically credible instructors, practical exercises, evaluation rigor, current material, and clear explanations of failure modes. A high star rating alone does not prove expertise.

## 5. Essential papers and articles

### Read before joining

| Resource | Link | What to learn |
|---|---|---|
| **Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks** (Lewis et al.) | https://arxiv.org/abs/2005.11401 | Why retrieval can improve knowledge-intensive tasks; limitations of evidence retrieval |
| **RAGAS: Automated Evaluation of Retrieval Augmented Generation** | https://arxiv.org/abs/2309.15217 | Faithfulness and relevance evaluation; where automated metrics can fail |
| **A Survey on RAG Evaluation** | https://arxiv.org/abs/2405.07437 | Evaluation dimensions and benchmark design |
| **NIST AI Risk Management Framework** | https://www.nist.gov/itl/ai-risk-management-framework | Trustworthiness, governance, risk identification, and monitoring |
| **NIST Generative AI Profile** | https://www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence | Generative-AI-specific risks and controls |
| **NHTSA datasets and APIs** | https://www.nhtsa.gov/nhtsa-datasets-and-apis | Public complaint data, its context, and its limitations |
| **Scikit-learn probability calibration** | https://scikit-learn.org/stable/modules/calibration.html | Calibration and interpretation of model confidence |
| **MLflow documentation** | https://mlflow.org/docs/latest/ | Experiment tracking and reproducibility |
| **Pytest documentation** | https://docs.pytest.org/en/stable/ | Automated tests for data and model pipelines |

### Optional, for your longer-term D.Eng. direction

- **CLIP: Learning Transferable Visual Models From Natural Language Supervision** — https://arxiv.org/abs/2103.00020  
  Read for multimodal alignment and image–text representation learning.
- **Attention Is All You Need** — https://arxiv.org/abs/1706.03762  
  Selective transformer refresher.
- **LLaMA: Open and Efficient Foundation Language Models** — https://arxiv.org/abs/2302.13971  
  Optional foundation-model architecture background.

**Paper-reading template:** Problem → Method → Data → Evaluation → Limitations → One practical application to safety intelligence.

## 6. Hands-on project: SafetyLens

### Concept

**SafetyLens: Public Automotive Complaint Retrieval and Analysis**

A small, local Python prototype that helps a user search public vehicle complaint narratives, find similar records, explore provisional complaint categories, and see evidence and uncertainty. **It does not diagnose vehicles, verify defects, or make safety determinations.**

### Workflow

```text
Public NHTSA complaint records (500–1,000)
                  |
                  v
       Clean, normalize, inspect
                  |
        +---------+----------+
        |                    |
        v                    v
  TF-IDF baseline     Sentence embeddings
        |                    |
        +---------+----------+
                  |
                  v
       Retrieve relevant records
                  |
                  v
   Show complaint IDs + excerpts
                  |
                  v
 Evaluation / uncertainty / review flag
                  |
                  v
  Optional local Streamlit interface
```

### Suggested technology stack

- **Python + pandas:** data cleaning and exploration
- **Scikit-learn:** TF-IDF, logistic regression, train/test splits, metrics, calibration
- **Sentence Transformers:** semantic embeddings
- **FAISS or scikit-learn nearest neighbors:** optional vector search
- **MLflow:** optional experiment tracking
- **Pytest:** data and retrieval tests
- **Streamlit:** optional lightweight UI
- **No paid LLM API required** for the core project

### Project scope and milestones

#### Milestone A — Data and baseline (Nov 10–15)

- [ ] Find the NHTSA public complaint dataset and review its documentation.
- [ ] Select a small sample (500–1,000 narratives) with useful record IDs and fields.
- [ ] Inspect missing values, duplicates, text length, and class distributions.
- [ ] Build TF-IDF keyword search.
- [ ] Return top results with record identifiers and source fields.

**Deliverable:** `01_data_exploration.ipynb` and `retrieval_baseline.py`.

#### Milestone B — Classification and evaluation (Nov 16–22)

- [ ] Choose a modest, defensible prediction task (e.g., component category) based on available labels.
- [ ] Split data carefully; avoid duplicate/near-duplicate leakage across train and test.
- [ ] Train a TF-IDF + logistic regression baseline.
- [ ] Report per-class precision, recall, F1, confusion matrix, and class imbalance.
- [ ] Manually inspect at least 20–30 representative errors.
- [ ] Build a small manually reviewed set of search queries and relevant results.

**Deliverable:** `02_baseline_evaluation.ipynb` and `evaluation_notes.md`.

**Important:** Complaint categories and narratives are not independently validated defect labels. Explain that limitation explicitly.

#### Milestone C — Semantic retrieval and safety checks (Nov 23–29)

- [ ] Embed complaint narratives with a small Sentence Transformers model.
- [ ] Implement top-k semantic search.
- [ ] Compare semantic and TF-IDF retrieval using a manually reviewed query set.
- [ ] Show exact retrieved record IDs and excerpts, not unsupported generated claims.
- [ ] Add conservative handling for missing evidence and ambiguous results.
- [ ] Add a **human review recommended** indicator for uncertain or safety-sensitive interpretations.

**Deliverable:** `semantic_search.py` and `03_retrieval_comparison.ipynb`.

**Evaluation:** Precision@k, Recall@k (where judgments are available), qualitative error categories, and latency. Do not claim calibrated confidence without validating calibration.

#### Milestone D — Engineering quality and demo (Nov 30–Dec 6)

- [ ] Refactor code into small modules with clear function names.
- [ ] Add tests for data loading, missing fields, and deterministic retrieval behavior.
- [ ] Record package versions and random seeds.
- [ ] Write a README with setup, sample commands, architecture, and limitations.
- [ ] Create a short demo or screenshots using only public data.
- [ ] Write a one-page technical report: problem, baseline, results, failures, next steps.

**Deliverable:** reproducible repository and a five-minute walkthrough.

### Minimum viable project (if time gets tight)

Complete just these five items:

1. Public complaint data loader.
2. TF-IDF search with source IDs.
3. Sentence-embedding search.
4. Small manually reviewed retrieval evaluation.
5. README explaining limitations and human-review requirements.

**Stretch goals only:** Streamlit UI, MLflow, RAG-generated summaries, reranking, a full agent workflow, or a multimodal extension. Do not let stretch goals prevent finishing the baseline.

### Suggested repository structure

```text
safetylens/
├── README.md
├── requirements.txt
├── data/                  # Public sample or download instructions
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_baseline_evaluation.ipynb
│   └── 03_retrieval_comparison.ipynb
├── src/
│   ├── data_loader.py
│   ├── retrieval_baseline.py
│   ├── semantic_search.py
│   └── evaluation.py
├── tests/
│   ├── test_data_loader.py
│   └── test_retrieval.py
└── reports/
    └── evaluation_notes.md
```

### Example demonstration query

> “Vehicle loses power while driving.”

Expected output format: relevant public complaint records, their IDs, concise excerpts, provisional similarity rankings, and a clear note that results are **not verified defect findings**. Any displayed confidence must be appropriately defined and evaluated.

## 7. GM onboarding readiness

### Questions to bring to your manager and team

- What are the most important outcomes for my first 30, 60, and 90 days?
- Which GenAI/NLP/AI projects are highest priority?
- How do analysts and engineers use model outputs in existing workflows?
- What errors are most consequential, and how are they measured?
- Which data sources, development tools, models, and cloud platforms are approved?
- What are the AI governance, privacy, security, and documentation requirements?
- Who are the key domain experts and cross-functional partners?

### Behaviors to emphasize

- Understand the safety workflow before recommending a new model.
- Establish baseline metrics before claiming improvement.
- Treat false negatives, evidence provenance, and human oversight seriously.
- Document failure modes and reproducibility.
- Collaborate with safety engineers and domain specialists.

**Boundary:** SafetyLens is an independent public-data learning project. Do not upload GM data or internal code to personal tools, and do not assume permission to use internal material for academic work.

## 8. Connection to your Fall 2028 D.Eng. plan

This preparation is **not** a doctoral application project yet. It is a technical foundation for later work on **Trustworthy Multimodal AI for Automotive Safety and Intelligent Systems**.

| Period | Career priority | Research/academic priority |
|---|---|---|
| **Dec 2026–Mar 2027** | Learn GPSSC, deliver an initial measurable contribution | Confirm UM-Dearborn GPA eligibility; read selectively |
| **Apr–Jun 2027** | Own a useful project and strengthen evaluation practice | Expand a public-data research baseline |
| **Jul–Sep 2027** | Identify genuine unresolved technical problems | Draft research questions and contact faculty |
| **Oct–Dec 2027** | Build management trust; discuss feasibility and support | Refine proposal, identify recommenders |
| **Early 2028** | Maintain strong job performance | Submit Fall 2028 D.Eng. application by the **verified** deadline |

**Important eligibility issue:** Your reported M.S. GPA is **3.11**, below the previously identified **3.20** regular-admission benchmark. Obtain written guidance from UM-Dearborn about whether exceptions, conditional pathways, or other remedies exist. Neither professional experience nor faculty interest guarantees an exception.

**Deadline note:** Earlier program and central admissions pages appeared to provide different fall deadlines. **February 2028 is a conservative planning target, not a confirmed Fall 2028 deadline.** Verify the applicable deadline directly with the university when available.

## 9. Weekly reflection template

Copy this into a journal every Sunday:

```markdown
### Week of YYYY-MM-DD

**Time spent:** __ hours
**Courses/reading completed:**
-

**Project progress:**
-

**Metrics or experiments:**
-

**What failed / what surprised me:**
-

**One insight relevant to trustworthy automotive AI:**
-

**Next week's top 3 tasks:**
1.
2.
3.
```

## 10. Final priorities

1. **Finish SafetyLens's retrieval baseline and evaluation** before adding agents or an elaborate interface.
2. **Take the three essential DeepLearning.AI courses**, applying each lesson immediately.
3. **Understand NHTSA data limitations and NIST AI risk concepts.**
4. **Write a clear README and technical report.**
5. **Arrive rested and ready to learn GM's actual workflows.**

---

*Prepared November 10, 2026. Course catalogs, URLs, availability, and institutional admission requirements can change; verify before purchasing or applying.*
