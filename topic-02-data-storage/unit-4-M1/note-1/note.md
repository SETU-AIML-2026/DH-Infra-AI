---
icon:
  type: ic:baseline-grading
  color: "#5523a6"
---

# Grading Rubrics

### Peer-grading instructions

Peer grading is not only about assigning a score. Please **provide constructive feedback explaining your assessment**.

In particular, highlight any **potential problems, ambiguities, or overlooked issues** that you identified in the project. Think about what could cause difficulties later in the project, for example, problems with data leakage, unclear data versions, insufficient reproducibility, inappropriate storage choices, or an underspecified preprocessing or data-splitting strategy.

Your feedback should help to **improve their project**, rather than simply justify the grade. Be specific and, where possible, suggest what they could clarify or change.


## Milestone 1 Peer-Grading Rubric

**Maximum: 10 points**

Assess each criterion based on the quality and completeness of the team's description. Give **partial credit** when a criterion is addressed but lacks important detail.

| Criterion                                    |   Points | Full-credit expectations                                                                                                                                                                                                                   |
| -------------------------------------------- | -------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **1. Raw data storage**                      |  **1.0** | Clearly states **where the raw data will live**, including the storage system/location and why it is appropriate.                                                                                                                          |
| **2. Processed data storage & file formats** |  **1.0** | Clearly describes **where processed data will be stored** and specifies appropriate **file formats** for raw and/or processed data, with enough detail to understand the intended representation.                                          |
| **3. Database / object storage decision**    | **0.5** | Explicitly considers whether a **database, object storage, file system, or other solution** is needed. The choice is justified in relation to the project's data and access requirements.                                                  |
| **4. Data versioning**                       | **0.5** | Explains **how different versions of the data will be identified and tracked**, including changes to datasets where relevant.                                                                                                              |
| **5. Data access**                           | **1.0** | Clearly explains **how the system/code will access the data**, including relevant paths, APIs, credentials/access mechanisms, or other interfaces as appropriate.                                                                          |
| **6. Data split / validation strategy**      |  **2.0** | Provides a **clear and appropriate data-splitting strategy**: either cross-validation or a train/dev/test split. The description specifies how the split/validation will be performed and avoids inappropriate data leakage.               |
| **7. Feature description**                   |  **1.0** | Features used by the AI system are **clearly identified and described**. It is possible to understand what each feature represents and how it is obtained or constructed.                                                                  |
| **8. Data types and formats**                | **0.5** | Specifies relevant **data types and formats** (e.g., numerical, categorical, text, image; integer, float, string; CSV, JSON, Parquet, etc.) sufficiently to understand how the data will be handled.                                       |
| **9. Reproducibility of data collection**    |  **1.0** | Describes how the **data collection process can be reproduced**, including data sources, collection procedures, relevant parameters/settings, and/or code where appropriate.                                                               |
| **10. Reproducibility of preprocessing**     |  **1.5** | Describes preprocessing steps clearly enough that another person could **reproduce the processed dataset from the raw data**. Important transformations, filtering, cleaning, feature construction, and relevant parameters are specified. |

**Total: 10 points**

## Peer-grading guidance

When assigning points, consider the following:

* **Full points:** The criterion is clearly addressed, sufficiently detailed, and appropriate for the project.
* **Partial points:** The criterion is addressed but is vague, incomplete, insufficiently justified, or missing important implementation details.
* **0 points:** The criterion is not addressed, or the proposed approach is fundamentally inappropriate.

### Important distinction

**Mentioning something is not the same as specifying it.**

For example:

* *Weak:* “We will store the data in the cloud.”
* *Stronger:* “Raw data will be stored in a GCS bucckets as JSON files. Processed feature tables will be stored as Parquet files. Each dataset release will have a version identifier and timestamp.”

Similarly:

* *Weak:* “We will split the data into training and testing data.”
* *Stronger:* “We will use a 70/15/15 train/dev/test split, stratified by the target class. The test set will be held out until final evaluation, and preprocessing parameters will be fitted using only the training data.”

### Overall peer-grading question

**Could another student, using this milestone description, understand how the project's data will be stored, accessed, transformed, split, and reproduced?**

If not, deduct points from the relevant criteria for missing specificity.
