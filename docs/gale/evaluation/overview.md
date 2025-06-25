# Overview

Evaluation Studio is a comprehensive tool in GALE for assessing LLM performance. It offers users the flexibility to select from a variety of pre-existing evaluators to measure model effectiveness. Users can upload and organize datasets (including inputs and outputs) into designated projects for evaluation, with adjustable thresholds and scoring metrics for customization based on specific needs. With Evaluation Studio, users can assess datasets against models, analyze results, and gain insights through a streamlined, user-friendly interface tailored to their selected criteria.


## Key Features

1. **Project-based Organization:** Projects serve as folders for evaluations. Users can create multiple evaluations under a project, and each evaluation contains a dataset. Users can create, rename, and delete projects.
2. **Flexible Dataset Handling and Import:** Evaluation Studio supports importing data through CSV files (with input-output pairs or input data) and production data from deployed model traces.
3. **Streamlined Evaluation Process**: Evaluate model performance based on out-of-the-box evaluators such as groundness, coherence, toxicity, etc. Users can run evaluations on datasets, with results helping identify areas for model improvement.
4. **Flexibility for Different Data Scenarios**: Evaluation Studio supports various evaluation scenarios:
    1. **One Input, One Output**: Simple, straightforward evaluations.
    2. **One Input, Multiple Outputs**: Assess multiple outputs from a single input.
    3. **Input Only**: Generate outputs  with your production model when only input data is available.


## Why Use Evaluation Studio?

Evaluation Studio is an essential tool for managing, evaluating, and optimizing Large Language Models. It simplifies the process of model evaluation and provides flexible options for data import and analysis. This makes it an invaluable resource for data scientists, machine learning engineers, and teams working on model development and optimization.

1. **Streamlined Workflow:** Evaluation Studio captures the model evaluation through datasets with various pre-built evaluators. Users can manage projects, upload data, perform evaluations, and track results, all in one place.
2. **Customizability:** Users can define evaluation criteria that suit their specific needs. The platform adapts to different evaluation scenarios, from simple to complex use cases.
3. **Continuous Improvement:** Regular evaluations allow users to track model performance over time, ensuring that models are updated or fine-tuned as needed for ongoing optimization.
4. **Seamless Integration**: Evaluation Studio is designed to integrate with production models seamlessly. It supports importing data from deployed models and exporting custom trace data in the studio to be further analyzed.


## User Experience Overview

The following outlines the key actions at each stage of the Evaluation Studio user journey:

1. [**Create a project**](./create-project.md): Log in to GALE, go to Evaluation Studio, and create a project.

2. [**Create an evaluation**](./create-evaluation.md): Create an evaluation for your project.

3. [**Import a dataset**](./import-dataset.md): Upload your dataset (e.g., CSV) for evaluation.

4. [**Configure evaluators**](./configure-evaluator.md): Choose Quality or Safety evaluators such as Coherence, Toxicity, or Bias Detection. Then, link the evaluator’s prompt variables (e.g., {{input}}, {{output}}) to the dataset columns.

5. [**Run an evaluation**](./run-evaluation.md): Trigger the evaluation based on your dataset and selected evaluators.

6. [**View evaluation results**](./view-evaluation-insight.md): Review the evaluator tiles in the Evaluation Insights section, where results are shown visually with color-coded indicators (e.g., green/red). Assess model performance by examining visual cues and scores.
