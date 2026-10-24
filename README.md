# NameThatLLM

CS-6600 Project Part 1: Exploratory Data Analysis

Team: Jeffery Hatch, Fred Walter, Isaac Christensen, Zachary Saylors

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

- [x] Uploaded Jeffery's initial notebook and added the dataset CSV to the repository. Fred Walter
- [x] Added the initial Kaggle login, download, and data-loading code. Jeffery Hatch
- [x] Added all three research questions. Jeffery Hatch
- [x] Added code to inspect the dataset size, columns, and example paragraphs. Jeffery Hatch
- [x] Added checks for missing values, duplicate paragraphs, prompt counts, and paragraph counts per model. Jeffery Hatch
- [x] Calculated word counts, summarized paragraph lengths by model, and added the paragraph-length boxplot. Jeffery Hatch
- [x] Changed the notebook to load the team's CSV from GitHub instead of downloading through Kaggle. Fred Walter
- [x] Added NLTK sentence tokenization and the required language-resource downloads. Fred Walter
- [x] Expanded the dataset with word count, average word length, average sentence length, sentence count, punctuation count, and symbol count. Fred Walter
- [x] Added detection of punctuation types and calculated individual punctuation ratios. Fred Walter
- [x] Added comments explaining the code, feature calculations, and their limitations. Jeffery Hatch
- [x] Updated punctuation ratios to prevent division by zero and use escaped punctuation matching. Jeffery Hatch
- [x] Added punctuation per 100 words, a numerical feature summary, and the correlation heatmap. Jeffery Hatch
- [x] Added IQR outlier checks for average sentence length and punctuation per 100 words, with examples to review. Jeffery Hatch
- [x] Updated the team names and added the README, source links, remaining-work checklist, and proposed evaluation plan. Jeffery Hatch

## What we need to finish this week

- [ ] Clean up the introduction and confirm everyone's name is listed correctly. - Isaac
- [ ] Add the Kaggle source and collection details to the notebook, and explain how the data fits the assignment. - Isaac
- [ ] Fill in the Observations section with what we learned from the graphs and summary statistics. - Isaac
- [ ] Compare punctuation use across models to help answer our second question. - Zak
- [ ] Review the flagged outliers and explain whether we will keep them, fix them, or remove them. - Isaac
- [ ] Decide which features to use and document any cleaning changes, including how to handle empty text and punctuation our current code does not count. -Isaac
- [ ] Explain how we will handle categorical variables. The model name is our target label. The paragraph ID should not be used to predict it, and the prompt ID should be used to group responses when splitting the data.
- [ ] Put the preparation steps into a reusable function or pipeline that takes the raw data and returns the features and labels needed for modeling. Keep the feature columns consistent and fit any learned preprocessing using training data only.
- [ ] Choose our main question and explain how we will measure success.
- [ ] Restart the notebook and run all cells in order to make sure everything works.
- [ ] Review the final notebook together and have everyone submit the same version on Canvas.

## Plan for evaluating the model

We could focus on identifying LLMs from unfamiliar prompts. We would keep responses to the same prompt together when splitting the data so that a prompt cannot appear in both training and testing.

We could also use accuracy and macro F1 to evaluate the results and compare them against a simple model that always guesses the most common training label. A confusion matrix would show which LLMs get confused with each other.
