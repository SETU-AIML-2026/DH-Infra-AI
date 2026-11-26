---
icon:
  type: ic:baseline-grading
  color: "#5523a6"
---

# Final Project Report

**Maximum grade: 60 points**

## 1. Project overview

The final project report documents the design, implementation, and evaluation of an end-to-end machine learning (ML) system developed throughout the four project sprints.

**This is an individual project.** Each student is expected to independently implement, document, and critically evaluate their own ML engineering solution. The project must represent the student's individual work, including their technical decisions, implementation, experiments, and conclusions.

The report should demonstrate not only that the different components have been implemented, but also that the student understands the reasoning behind their design choices and can critically evaluate the resulting system.

The project covers four main areas:

1. Data storage solution and data splitting.
2. Exploratory Data Analysis (EDA) and ELT/ETL pipelines.
3. AI model training, MLOps, hyperparameter optimization, and infrastructure selection.
4. Scalable inference service and continuous model training.

The assessment places particular emphasis on **informed technical decisions, observations supported by evidence, reproducibility, and critical analysis**.

Simply describing what was implemented is not sufficient. Students are expected to explain why particular technologies, architectures, models, configurations, and methodologies were selected, what alternatives were considered, and what conclusions can be drawn from the observed results.

## 2. Submission requirements

The final report must follow these submission requirements:

| Requirement | Description |
|---|---|
| **Submission format** | A single PDF document uploaded to Moodle. |
| **Maximum length** | 6,000 words, plus supporting screenshots, figures and tables. |
| **GitHub repository** | A link to the associated GitHub repository is mandatory and must be included in the PDF report. |
| **Repository access** | Students must ensure that the teachers have access to the GitHub repository and its contents for assessment. |
| **Documentation** | The report must cover all four project sprints and provide evidence of the implemented solution. |
| **AI usage disclosure** | A dedicated section disclosing the use of generative AI tools is mandatory. |

### 2.1 GitHub repository requirements

The GitHub repository should contain the relevant source code, configurations, scripts, and documentation required to understand and reproduce the project.

The repository should be organized so that the different project components can be identified easily.

At a minimum, it should provide access to:

- Data storage and data processing code.
- EDA notebooks or scripts.
- ETL/ELT pipeline implementation.
- Model training and hyperparameter optimization code.
- Experiment-tracking configurations or references.
- Inference service implementation.
- Continuous training and model evaluation code.
- Relevant configuration files and execution instructions (e.g. README files).

The repository link must be included in the PDF report.

**Important:** It is the student's responsibility to verify that the teachers can access the repository. A private repository without access granted to the teachers may prevent the assessment of the implementation.

### 2.2 Use of screenshots and supporting evidence

Screenshots can be included to demonstrate important implementation details and project results.

Examples include:

- Data storage organization.
- EDA visualizations.
- ETL/ELT pipeline execution.
- MLOps experiment-tracking dashboards.
- Hyperparameter optimization results.
- Infrastructure and deployment configurations.
- Inference API responses.
- Load testing and performance measurements.
- Continuous training execution.
- Comparison between the original and retrained models.

Screenshots should support the explanations in the report rather than replace them. Important observations and conclusions must be explained in the report text.

## 3. Expected report structure

The report should follow the four project sprints, followed by an overall evaluation and the mandatory AI usage disclosure.

### 3.1 Sprint 1: Data storage solution and data splits

Describe the data storage architecture and explain how the data is organized, accessed, and versioned.

Discuss:

- Where raw and processed data are stored.
- Storage technologies and file formats selected.
- How the application accesses the data.
- How data versions are identified and managed.
- The selected train/validation/test split or cross-validation strategy.
- How data leakage is prevented.

Explain and justify the important architectural decisions. Discuss any limitations or challenges associated with the selected approach.

### 3.2 Sprint 2: EDA and data pipelines

Describe the exploratory data analysis and the implemented data processing pipelines.

Discuss:

- The characteristics and properties of the dataset.
- Relevant EDA results, statistics, and visualizations.
- Missing values, outliers, class imbalance, correlations, and other relevant observations.
- Data cleaning and preprocessing.
- Feature engineering and transformations.
- The implemented ETL/ELT pipeline architecture.
- Data quality checks and validation.

Explain how the observations from EDA influenced preprocessing and pipeline design. Justify the selected transformations and discuss any relevant limitations.

### 3.3 Sprint 3: AI training, MLOps, hyperparameter optimization and infrastructure

Describe the model development and experimentation process.

Discuss:

- The selected model type and architecture, including alternative approaches considered.
- Why the selected model is appropriate for the problem.
- The hyperparameter optimization strategy and parameters explored.
- The MLOps solution used to track experiments.
- The computational infrastructure selected (CPU, GPU, distributed GPU, or other).
- Comparison of experimental results and identification of the best-performing model.
- Training performance, computational costs, and relevant trade-offs.
- Model weaknesses and error analysis.

Provide evidence from the experiment-tracking solution to support the conclusions.

Explain why the selected model, hyperparameters, and computational resources were appropriate. Report what was learned from the experiments and identify potential improvements.

Include a model card or equivalent documentation for the selected model.

### 3.4 Sprint 4: Scalable inference and continuous training

Describe the inference architecture and how the model can be served and maintained over time.

**A. Scalable inference**

Discuss:

- The inference service architecture and implementation.
- How the trained model is exposed through an API or equivalent interface.
- How incoming requests are handled.
- How the service can accommodate increasing workloads.
- The selected scaling strategy, such as horizontal scaling, vertical scaling, containerization, load balancing, or autoscaling. **Note**: we only expect some practical load testing, performance measurements, and justified architectural decisions, deployment with an expensive infrastructure (i.e. Kubernetes) is not expected.
- Relevant performance measurements, such as latency, throughput, and resource utilization.
- Limitations and potential scalability improvements.

Explain and justify the selected serving and scaling architecture.

**B. Continuous training and model lifecycle management**

Discuss:

- How new or extended training data is incorporated.
- How the retraining process is triggered or executed.
- How the newly trained model is evaluated.
- How model versions are tracked and managed.
- How a new model is made available to the inference service. **Note**: Full automation is not expected, but considered a good achievement.
- How a previous model can be restored if the new model performs poorly.

Students should demonstrate **at least one successfully retrained model using extended training data**.

**The final test set must remain the same as in the previous milestones to ensure fair comparison of the results**. Compare the original and retrained models using appropriate evaluation metrics. Discuss the observed differences and explain whether the additional training data improved, deteriorated, or had no significant impact on model performance.

**An improvement in performance is not mandatory.** A valid experiment, appropriate evaluation, and well-reasoned conclusions are what matter.

### 3.5 Overall evaluation and critical reflection

Provide an overall assessment of the completed ML system.

Discuss:

- What worked well and what did not.
- The most important technical challenges encountered.
- The effectiveness of the selected technologies and architectures.
- The main limitations of the current implementation.
- Potential improvements and future development.
- Whether the resulting system satisfies the original project objectives (shared in Slack).

### 3.6 AI usage disclosure

Include a dedicated section titled **AI Usage Disclosure**.

Students must disclose if generative AI was used.

If AI tools were used, specify:

- Which tools were used (e.g., ChatGPT, GitHub Copilot, Claude, or other tools).
- For what purposes they were used (e.g., code assistance, debugging, explanation of concepts, documentation, report writing, or data analysis).
- Which parts of the project were assisted by AI.
- How AI-generated suggestions or outputs were reviewed, tested, and validated.

If no generative AI tools were used, explicitly state this.

Students remain responsible for the correctness, quality, and understanding of all submitted work, including any content or code produced with AI assistance.

---

# 4. Final Project Grading Rubric

**Maximum: 60 points**


## 4.1 Sprint 1 (10 points)

| Criterion | Points | Full-credit expectations |
|---|---:|---|
| **1.1 Raw and processed data storage** | 2.0 | Clearly describes and implements where raw and processed data are stored. Specifies storage technologies, file formats, and data organization. Justifies the choice of storage solutions based on project requirements. |
| **1.2 Data access and versioning** | 2.0 | Explains how the pipeline accesses the data and how different dataset versions are identified and tracked. Demonstrates an appropriate approach to managing changes to datasets. |
| **1.3 Data splitting strategy** | 3.0 | Implements an appropriate train/validation/test split or cross-validation strategy. Explains the rationale behind the selected strategy, including how data leakage is prevented. The test set is appropriately isolated from model development and hyperparameter optimization. |
| **1.4 Technical decisions and observations** | 2.0 | Provides detailed reasoning for the storage architecture, formats, and splitting strategy. Discusses relevant observations about the data organization, storage requirements, and potential limitations of the chosen solution. |
| **1.5 Reproducibility** | 1.0 | Provides sufficient information to locate, access, and reconstruct the datasets and splits. Includes relevant configurations, scripts, references, or version identifiers. |
| **Subtotal** | **10.0** | |

## 4.2 Sprint 2 (12 points)

| Criterion | Points | Full-credit expectations |
|---|---:|---|
| **2.1 Exploratory Data Analysis (EDA)** | 4.0 | Provides thorough EDA appropriate to the dataset and problem. Includes relevant descriptive statistics and visualizations, investigates feature distributions, missing values, outliers, class imbalance, correlations, or other relevant characteristics. Identifies meaningful patterns and observations that inform subsequent project decisions. |
| **2.2 ETL/ELT pipeline implementation** | 3.0 | Implements a clear and functional data processing pipeline. Describes the extraction, transformation, and loading steps (or corresponding ELT process). Processing includes relevant cleaning, filtering, transformations, and feature engineering. The pipeline is appropriately structured and integrated with the data storage solution. |
| **2.3 Data quality and validation** | 2.0 | Demonstrates appropriate data quality checks and validation. Addresses issues such as missing values, invalid records, inconsistent formats, duplicates, and potential data leakage. Explains how data quality is maintained throughout the pipeline. |
| **2.4 Decisions and observations** | 2.0 | Explains how EDA findings influenced preprocessing, feature selection, and pipeline design. Justifies important transformation choices and discusses relevant findings. |
| **2.5 Reproducibility** | 1.0 | Provides code, configurations, and instructions sufficient to reproduce the EDA and data processing pipeline and obtain the processed dataset. |
| **Subtotal** | **12.0** | |

## 4.3 Sprint 3 (18 points)

| Criterion | Points | Full-credit expectations |
|---|---:|---|
| **3.1 Model and architecture selection** | 2.0 | Selects an appropriate AI/ML model type and architecture for the problem. Justifies the selection based on the data, task characteristics, expected performance, and relevant alternatives. |
| **3.2 Hyperparameter optimization** | 3.0 | Performs systematic hyperparameter optimization. Clearly identifies the hyperparameters explored, search ranges, optimization strategy, and evaluation methodology. Compares configurations and identifies the best-performing configuration based on appropriate validation metrics. |
| **3.3 MLOps and experiment tracking** | 3.0 | Uses an MLOps solution (e.g., MLflow, Weights & Biases, or an equivalent tool) to track experiments. Records relevant information, including model configurations, hyperparameters, metrics, artifacts, and experiment results. The tracked experiments support meaningful comparisons. |
| **3.4 Infrastructure and compute architecture selection** | 2.0 | Selects and justifies appropriate computational resources (e.g., CPU, single GPU, or distributed/multiple GPUs). Considers model complexity, dataset size, training requirements, execution time, scalability, and resource costs. Explains why the selected infrastructure is appropriate for the workload. |
| **3.5 Evaluation and experimental analysis** | 3.0 | Evaluates the trained models using appropriate metrics. Analyses and compares experimental results, identifies the best model and hyperparameters, and discusses relevant performance trade-offs. Provides evidence supporting conclusions rather than simply reporting the best metric. |
| **3.6 Model weaknesses and error analysis** | 2.0 | Analyses mistakes made by the selected model. Identifies representative failure cases, problematic data subsets, or patterns in incorrect predictions. Discusses potential causes, limitations, and possible improvements. |
| **3.7 Reproducibility and model documentation** | 1.0 | Provides sufficient information to reproduce the training experiments, including code, configurations, dependency information, and relevant data references. Provides a model card or equivalent documentation describing the selected model, its intended purpose, evaluation, and limitations. |
| **3.8 Technical decisions and observations** | 2.0 | Provides detailed reasoning for model selection, optimization strategy, experiment-tracking approach, and infrastructure decisions. Discusses important observations from the experiments and explains how these influenced subsequent decisions. |
| **Subtotal** | **18.0** | |

## 4.4 Sprint 4 (14 points)

| Criterion | Points | Full-credit expectations |
|---|---:|---|
| **4.1 Inference service architecture and implementation** | 3.0 | Implements a functional inference service that exposes the trained model through an appropriate interface (e.g., REST API). Describes and justifies the serving architecture, including model loading, request handling, preprocessing, and prediction responses. |
| **4.2 Scalability and performance of inference** | 3.0 | Addresses how the inference service can handle increasing workloads. Considers relevant strategies such as horizontal/vertical scaling, containerization, load balancing, concurrent request handling, or autoscaling. Provides performance measurements or tests where appropriate (e.g., latency, throughput, resource utilization, or behavior under load). Justifies the selected scaling approach. |
| **4.3 Continuous training pipeline** | 3.0 | Implements a continuous training or retraining process that incorporates extended or newly available training data. Explains how new data is collected or introduced, how retraining is triggered or executed, and how the resulting model is evaluated, registered, and managed. |
| **4.4 Demonstration and evaluation of a retrained model** | 3.0 | Demonstrates at least one successfully retrained model using extended training data. Documents the additional data and retraining process. Compares the new model against the previous model using appropriate evaluation metrics. Discusses whether performance improved, deteriorated, or remained similar and provides evidence supporting the conclusions. |
| **4.5 Model deployment, lifecycle management and technical decisions** | 2.0 | Explains how newly trained models are made available to the inference service. Addresses model versioning, model promotion, deployment, and rollback where appropriate. Justifies the selected deployment and retraining architecture and discusses relevant operational trade-offs, limitations, and observations. |
| **Subtotal** | **14.0** | |

## 4.5 Overall reproducibility, documentation and engineering quality (6 points)

This section evaluates the quality and completeness of the project as a whole, across all four sprints.

| Criterion | Points | Full-credit expectations |
|---|---:|---|
| **5.1 End-to-end reproducibility** | 2.0 | Provides a clear and sufficiently complete set of instructions to reproduce the main project workflow, from data access and processing through model training, deployment, and retraining. Includes relevant code repositories, configurations, dependencies, and execution instructions. |
| **5.2 Technical documentation and report quality** | 2.0 | Provides clear, well-organized, and technically accurate documentation. Includes relevant architecture diagrams, pipeline descriptions, configuration details, experiment results, and references to implementation artifacts. The report makes it possible to understand how the different components fit together. |
| **5.3 Critical reflection and overall engineering quality** | 2.0 | Demonstrates a critical understanding of the project. Identifies important limitations, challenges, trade-offs, and potential improvements. Reflects on the effectiveness of the selected technologies and approaches, and discusses what could be improved in a future iteration. |
| **Subtotal** | **6.0** | |

## 5. Total score

| Assessment area | Points |
|---|---:|
| Sprint 1 – Data storage solution and data splits | 10 |
| Sprint 2 – EDA and ELT/ETL pipelines | 12 |
| Sprint 3 – AI training, MLOps, hyperparameter optimization and infrastructure | 18 |
| Sprint 4 – Scalable inference and continuous training | 14 |
| Overall reproducibility, documentation and engineering quality | 6 |
| **TOTAL** | **60** |

---


## 8. AI Usage Disclosure

Generative AI (ChatGPT by OpenAI) was used as an assistance tool in the preparation of this assignment specification and grading rubric. It was used to help structure the assessment criteria, draft rubric descriptions, suggest point allocations, and improve the clarity and consistency of the assessment guidelines.

The generated content was subsequently reviewed, edited, and adapted by the lecturer. The final wording, assessment criteria, weighting, and allocation of marks reflect the lecturer's own decisions and professional judgement.

The lecturer takes full responsibility for the final assignment specification and grading rubric.