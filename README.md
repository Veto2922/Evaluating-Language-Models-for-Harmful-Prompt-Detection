# Evaluation of Language Models for Harmful Prompt Detection

## Overview

This project evaluates and compares three language models—**Gemini_pro**, **AI2_j2-ultra**, and **Gemini_flash**—for their effectiveness in detecting harmful content in text prompts. The evaluation includes model predictions on a stratified sample of prompts and performance metrics, including accuracy, precision, recall, and F1 score. The project aims to determine the best model for detecting offensive content.

### Please refer to the notebook folder to view all the code.


## 1. Data Preparation

### Data Source
- ** https://www.kaggle.com/datasets/strikoder/llm-evaluationhub/data


### Data Description
The dataset consists of text prompts categorized into different ethical categories. It includes columns such as:
- `Prompt`: The text prompt to be evaluated.
- `EthicalCategory`: The ethical category of the prompt.
- `CorrectLabel`: The ground truth label indicating whether the prompt is harmful or not.

### Stratified Sampling
To manage resource constraints, a stratified sample of 350 prompts was extracted from the dataset. The sample is balanced across different ethical categories to ensure a representative evaluation.

## 2. Model Evaluation

### Models Evaluated
1. **Gemini_pro** (Google Generative AI)
2. **AI2_j2-ultra** (AI21 Language Model)
3. **Gemini_flash** (Google Generative AI)

### Evaluation Process
Each model was used to predict whether the text prompts contained offensive content. The following steps were carried out:
1. **Prediction**: Models provided predictions on the sampled prompts.
2. **Error Handling**: Included retry logic with exponential backoff to manage rate limits and errors.
3. **Results Collection**: Predictions were collected and stored in the output data file.

## 3. Performance Metrics

### Metrics Computed
- **Accuracy**: Proportion of correctly identified labels.
- **Precision**: Proportion of true positives among the predicted positives.
- **Recall**: Proportion of true positives among the actual positives.
- **F1 Score**: Harmonic mean of precision and recall.

### Results Summary
The performance metrics were calculated for each model, and the results are summarized as follows:
![image](https://github.com/user-attachments/assets/723dcee8-7275-4cfc-8c22-b19ce3dd1a9a)

- **Gemini_pro**: Best overall performance with high accuracy, precision, and recall.
- **Gemini_flash**: Strong second, with a good balance between precision and recall.
- **AI2_j2-ultra**: Lower performance in accuracy, precision, and recall compared to the other models.

### Model Comparison
Bar plots and confusion matrices were generated to compare the models' performance across different metrics. **Gemini_pro** was identified as the best-performing model, particularly in scenarios requiring high recall.

## 4. Results Visualization

### Accuracy, Precision, Recall, and F1 Score
![image](https://github.com/user-attachments/assets/a1c684c8-1f1a-4a9b-a0bc-469a33483de9)

![image](https://github.com/user-attachments/assets/9d9a0bc9-ea3b-489c-894b-bebac504dfe9)


Visualizations show the comparison of models based on accuracy, precision, recall, and F1 score. Key insights include:
- **Gemini_pro**: Consistently high across all metrics.
- **Gemini_flash**: Strong performance but slightly less consistent.
- **AI2_j2-ultra**: Generally lower performance.

### Confusion Matrices
Confusion matrices illustrate how each model performs in terms of true positives, false positives, true negatives, and false negatives.

![image](https://github.com/user-attachments/assets/4e3282ff-091d-40b5-b283-cca1cc83acfb)

![image](https://github.com/user-attachments/assets/397351f0-eb93-40f3-9822-1b4376650178)

![image](https://github.com/user-attachments/assets/75fc4587-711c-4dba-b06e-e10f2fae82f3)




## 5. Ethical Categories Performance

Performance metrics were also evaluated across different ethical categories:
![image](https://github.com/user-attachments/assets/b653760c-3098-4e7b-9c99-1ec2e113d7c8)

- **Gemini_pro_res_clean**: Best performance overall across categories.
- **Gemini_flash_res_clean**: Strong performance in some categories but slightly weaker in others.
- **AI2_j2-ultra_res_clean**: Lower performance in specific categories, particularly in **Ethics and Morality**.

  ![image](https://github.com/user-attachments/assets/68d0c9ea-e7b2-45dc-9f15-7bbd2099f230)

  ![image](https://github.com/user-attachments/assets/4764d77e-fa31-4870-ab49-3ec9cb524f38)



## Conclusion

- **Gemini_pro** is recommended for applications requiring high recall and overall strong performance.
- **Gemini_flash** offers a balanced approach and can be considered for scenarios needing a good trade-off between precision and recall.
- **AI2_j2-ultra** may need further tuning or could be less suitable based on current performance.



## Project Organization

```
├── LICENSE            <- Open-source license if one is chosen
├── Makefile           <- Makefile with convenience commands like `make data` or `make train`
├── README.md          <- The top-level README for developers using this project.
├── data
│   ├── external       <- Data from third party sources.
│   ├── interim        <- Intermediate data that has been transformed.
│   ├── processed      <- The final, canonical data sets for modeling.
│   └── raw            <- The original, immutable data dump.
│
├── docs               <- A default mkdocs project; see www.mkdocs.org for details
│
├── models             <- Trained and serialized models, model predictions, or model summaries
│
├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
│                         the creator's initials, and a short `-` delimited description, e.g.
│                         `1.0-jqp-initial-data-exploration`.
│
├── pyproject.toml     <- Project configuration file with package metadata for 
│                         llms_evaluation and configuration for tools like black
│
├── references         <- Data dictionaries, manuals, and all other explanatory materials.
│
├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
│   └── figures        <- Generated graphics and figures to be used in reporting
│
├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
│                         generated with `pip freeze > requirements.txt`
│
├── setup.cfg          <- Configuration file for flake8
│
└── llms_evaluation   <- Source code for use in this project.
    │
    ├── __init__.py             <- Makes llms_evaluation a Python module
    │
    ├── config.py               <- Store useful variables and configuration
    │
    ├── dataset.py              <- Scripts to download or generate data
    │
    ├── features.py             <- Code to create features for modeling
    │
    ├── modeling                
    │   ├── __init__.py 
    │   ├── predict.py          <- Code to run model inference with trained models          
    │   └── train.py            <- Code to train models
    │
    └── plots.py                <- Code to create visualizations
```

--------

