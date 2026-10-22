# NameThatLLM

CS-6600 Project Part 1: Exploratory Data Analysis

Team: Jeffery Hatch, Fred Walter, Issac Christensen, Zachary Saylors

## About the project

We want to see whether we can identify which LLM wrote a paragraph based on its writing style. We are looking at things like paragraph length, sentence length, and punctuation.

The dataset has 2,699 paragraphs from 18 LLMs responding to 150 prompts. The columns are id, prompt_id, text, and model. The model column tells us which LLM wrote each paragraph.

## Data source

We are using data from the Name That LLM competition on Kaggle. The task is to identify which of 18 LLMs wrote a passage. Our notebook reads the team's CSV copy from GitHub.

Original source: [Name That LLM on Kaggle](https://www.kaggle.com/competitions/name-that-llm)

Data page: https://www.kaggle.com/competitions/name-that-llm/data

CSV used by the notebook: https://raw.githubusercontent.com/FredWltr/NameThatLLM/refs/heads/main/dataset/data.csv

Citation: Yao Yan, Martyna Plomecka, and Ashley Oldacre. Name That LLM. Kaggle, 2026. https://www.kaggle.com/competitions/name-that-llm

## Questions we are exploring

1. Can we identify which LLM wrote a paragraph when the prompt was not included in training?
2. How do paragraph length and punctuation use differ between LLMs?
3. Are longer paragraphs easier to classify correctly than shorter paragraphs?

## What we have done

- [x] Added three research questions.
- [x] Looked at the dataset, its columns, and example paragraphs.
- [x] Checked for missing values and duplicate paragraphs. Neither showed up in the current results.
- [x] Checked how many paragraphs belong to each model.
- [x] Calculated features such as word count, average word length, sentence length, and punctuation use.
- [x] Added a boxplot comparing paragraph lengths across models.
- [x] Added a heatmap showing correlations between numerical features.
- [x] Flagged possible outliers and displayed examples to review.

## What we need to finish this week

- [ ] Clean up the introduction and confirm everyone's name is listed correctly.
- [ ] Add the Kaggle source and collection details to the notebook, and explain how the data fits the assignment.
- [ ] Fill in the Observations section with what we learned from the graphs and summary statistics.
- [ ] Compare punctuation use across models to help answer our second question.
- [ ] Review the flagged outliers and explain whether we will keep them, fix them, or remove them.
- [ ] Decide which features to use and document any cleaning changes, including how to handle empty text and punctuation our current code does not count.
- [ ] Explain how we will handle categorical variables. The model name is our target label. The paragraph ID should not be used to predict it, and the prompt ID should be used to group responses when splitting the data.
- [ ] Put the preparation steps into a reusable function or pipeline that takes the raw data and returns the features and labels needed for modeling. Keep the feature columns consistent and fit any learned preprocessing using training data only.
- [ ] Choose our main question and explain how we will measure success.
- [ ] Restart the notebook and run all cells in order to make sure everything works.
- [ ] Review the final notebook together and have everyone submit the same version on Canvas.

## Plan for evaluating the model

We could focus on identifying LLMs from unfamiliar prompts. We would keep responses to the same prompt together when splitting the data so that a prompt cannot appear in both training and testing.

We could also use accuracy and macro F1 to evaluate the results and compare them against a simple model that always guesses the most common training label. A confusion matrix would show which LLMs get confused with each other.