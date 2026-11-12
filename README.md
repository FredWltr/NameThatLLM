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
- [x] Compare punctuation use across models to help answer our second question. - Zak Saylors
- [x] Clean up the introduction and confirm everyone's name is listed correctly. - Isaac
- [x] Add the Kaggle source and collection details to the notebook, and explain how the data fits the assignment. - Isaac
- [x] Fill in the Observations section with what we learned from the graphs and summary statistics. - Isaac
- [x] Review the flagged outliers and explain whether we will keep them, fix them, or remove them. - Isaac
- [x] Decide which features to use and document any cleaning changes, including how to handle empty text and punctuation our current code does not count. -Isaac
- [x] Explain how we will handle categorical variables. The model name is our target label. The paragraph ID should not be used to predict it, and the prompt ID should be used to group responses when splitting the data. -Zak
- [x] Put the preparation steps into a reusable function or pipeline that takes the raw data and returns the features and labels needed for modeling. Keep the feature columns consistent and fit any learned preprocessing using training data only. -Zak
- [x] Choose our main question and explain how we will measure success. - Jeffery
- [x] Restart the notebook and run all cells in order to make sure everything works. - Jeffery

## Plan for evaluating the model

We could focus on identifying LLMs from unfamiliar prompts. We would keep responses to the same prompt together when splitting the data so that a prompt cannot appear in both training and testing.

We could also use accuracy and macro F1 to evaluate the results and compare them against a simple model that always guesses the most common training label. A confusion matrix would show which LLMs get confused with each other.

## Part 2: Model and presentation

Open the [Part 2 notebook](NameThatLLM_Part2_Baseline.ipynb) with the same Python kernel as Part 1 and run all cells. If you're setting up a fresh environment, install the packages with `python -m pip install -r requirements-part2-baseline.txt`.

Use the [shared split CSV](dataset/part2_split.csv) for each model. Join it to the data by `id` and use `validation_fold` on the training rows. Compare models using balanced accuracy and macro F1.

### What we have done

- [x] Set up the shared prompt split and three validation folds. - Jeffery Hatch
- [x] Added the Part 2 notebook and ran the dummy and logistic regression baselines on the same folds. - Jeffery Hatch
- [x] Added regular and company-guided MLP models. - Fred Walter
- [x] Added balanced accuracy and macro F1 to both MLP evaluations. - Jeffery Hatch
- [x] Added random seeds, kept each model's fold results separately, and combined the results into one comparison table. - Jeffery Hatch
- [x] Corrected the explanation of how the company-guided model learns. - Jeffery Hatch
- [x] Added 54 features covering punctuation, sentence variation, vocabulary diversity, capitalization, symbols, and common function words. - Jeffery Hatch
- [x] Compared six feature sets using logistic regression on the shared validation folds and added a graph of the results. - Jeffery Hatch

### Feature comparison results

Logistic regression with the expanded 63 features averaged 31.0% balanced accuracy and 30.2% macro F1, compared with 25.9% and 23.8% using the original nine features.
Balanced accuracy improved in all three validation folds. These are validation results, haven't evaluated on final test set.

### Current validation results

These are mean scores across the three validation folds. The final test set has not been evaluated.

| Model | Balanced accuracy | Macro F1 |
| --- | ---: | ---: |
| Most frequent guess | 5.6% | 0.6% |
| Logistic regression | 25.9% | 23.8% |
| Regular MLP | 24.9% | 22.6% |
| Company-guided MLP | 23.9% | 21.1% |

### What we need to finish

- [ ] Compare additional writing-style features and text-based features against the original nine-feature baseline.
- [ ] Compare remaining models on the shared folds and choose the final approach using validation scores.
- [ ] Analyze classification errors and whether longer paragraphs are easier to classify.
- [ ] Fit the chosen model on all training rows. Finish the notebook with the data, preprocessing, test results, and limitations.
- [ ] Prepare a 15 to 20 minute presentation with a section for each team member.
- [ ] Upload the final notebook, slides, and recording to the team Drive folder before midnight on December 4.