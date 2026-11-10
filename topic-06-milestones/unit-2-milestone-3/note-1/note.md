---
icon:
  type: ic:baseline-grading
  color: "#5523a6"
---

# Milestone 3 Peer-Grading Guide

### Peer-grading instructions

Peer grading is not only about assigning a score. Please **provide constructive feedback explaining your assessment**.

In particular, evaluate whether the student writing the report has made informed decisions about model selection, hyperparameter optimization, and computational resources. Consider whether the experiments are properly tracked and whether the conclusions are supported by observed results.

Highlight potential problems, ambiguities, or overlooked issues, such as insufficient experimentation, poorly justified model choices, inappropriate hyperparameter search strategies, lack of reproducibility, or failure to analyse model weaknesses.

Your feedback should help to improve the project, rather than simply justify the grade. Be specific and, where possible, suggest what the reviewee could clarify or change.

## Milestone 2 Peer-Grading Rubric

**Maximum: 10 points**

| Criterion | Points | Full-credit expectations |
|---|---:|---|
| **1. AI model selection** | **1.0** | Selects an appropriate AI/ML model type for the problem and data. The choice is justified based on task characteristics, data properties, expected performance, and computational constraints. Considers relevant alternative model types or architectures where appropriate. |
| **2. Hyperparameter optimization** | **1.5** | Performs systematic hyperparameter optimization. Identifies the hyperparameters explored, their search ranges or candidate values, and the optimization strategy (e.g., grid search, random search, Bayesian optimization). Uses an appropriate validation strategy and avoids test-set leakage. |
| **3. MLOps and experiment tracking** | **1.5** | Uses an MLOps solution or experiment-tracking tool (e.g., MLflow, Weights & Biases, or an equivalent solution) to record experiments. Tracks relevant information such as model types, architectures, hyperparameters, metrics, artifacts, and computational resources. Experiments are organized and sufficiently documented to support comparison and analysis. |
| **4. Analysis and conclusions from experiments** | **1.5** | Draws clear, evidence-based conclusions from observed results. Identifies the best-performing hyperparameters, model type, and/or architecture and explains why they were selected. Discusses relevant trade-offs, including performance, training time, inference cost, and computational resource requirements. Conclusions are supported by experimental evidence. |
| **5. Compute architecture selection** | **1.0** | Selects and justifies an appropriate computational architecture for training and experimentation (e.g., CPU, single GPU, or distributed/multiple GPUs). The decision considers model complexity, dataset size, computational requirements, training time, scalability, and resource costs where relevant. Ideally, provides evidence that the selected architecture is appropriate for the workload. |
| **6. Reproducibility** | **1.0** | Provides sufficient information to reproduce the experiments, including code, data references or versions, configurations, random seeds where appropriate, environment/dependency information, and instructions for running the experiments. Another student should be able to reproduce the main experimental results. |
| **7. Model card / model documentation** | **1.0** | Provides a model card or equivalent documentation describing the selected model, including its intended purpose, architecture, training data, evaluation methodology, performance metrics, limitations, and appropriate use considerations. |
| **8. Error analysis and model weaknesses** | **1.5** | Analyses mistakes made by the selected model (or multiple candidate models). Identifies representative failure cases, patterns in incorrect predictions, or problematic data subsets. Discusses potential reasons for these errors and identifies model limitations or weaknesses. Ideally, suggests possible improvements. |

**Total: 10 points**

## Peer-grading guidance

When assigning points, consider the following:

- **Full points:** The criterion is clearly addressed, sufficiently detailed, appropriately implemented, and supported by evidence.
- **Partial points:** The criterion is addressed but is vague, incomplete, insufficiently justified, or missing important implementation details.
- **0 points:** The criterion is not addressed, or the proposed approach is fundamentally inappropriate.

### Important distinctions

**1. Trying multiple hyperparameters is not the same as performing hyperparameter optimization.**

- *Weak:* "We tried different learning rates and selected the best one."
- *Stronger:* "We performed a random search over learning rates, batch sizes, and regularization parameters. We evaluated 30 configurations using validation F1-score and recorded the results in MLflow. The best configuration was selected based on validation performance."

**2. Using an experiment-tracking tool is not the same as drawing conclusions from experiments.**

- *Weak:* "We used MLflow to track our experiments."
- *Stronger:* "We used MLflow to track model configurations, hyperparameters, validation metrics, training duration, and resource consumption. The results indicate that the SVM model achieved the best validation performance, while the neural network required substantially more computational resources without providing a meaningful improvement."

**3. Reporting the best metric is not the same as analysing the results.**

- *Weak:* "Our best model achieved 92% accuracy."
- *Stronger:* "Our best model achieved 92% accuracy, but its recall for the minority class was only 65%. The error analysis revealed that most false negatives came from a particular subset of examples, suggesting that the model struggles with these cases."

**4. Reproducibility requires more than sharing the source code.**

- *Weak:* "All our code is available in GitHub."
- *Stronger:* "We provide the experiment configuration, dependency versions, dataset version, random seeds, and instructions to reproduce the best-performing experiment."

### Overall peer-grading question

**Could another student, using the submitted work, understand why a particular model and architecture were selected, how the hyperparameters were optimized, how the experiments were tracked, and what conclusions can be drawn from the results? Could they reproduce the main experiments and understand the weaknesses of the selected model?**

If not, deduct points from the relevant criteria for missing specificity, insufficient evidence, or lack of analysis.
