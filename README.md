# TextCoherenceOnSocialMedia
This repository contains the project done during CS535.
With social media becoming the number one platform for individuals to find a global audience, being coherent is more crucial than ever.
However, the colloquialisms of social media make assessing coherence a problematic task.
In this project, we look to automate the generation a dataset of coherent and incoherent social media posts. We also describe the preprocessing pipeline, a critical step given the varied nature of social media. Furthermore, we develop a sliding window convolutional neural network (CNN) architecture to capture the semantics of social media. Finally, we compare our results with existing architectures on both social media and non-social media-based corpora.

Refer to reports/EndTerm_Report for detailed information about the project including proposed method description and experimental analysis.

Our source code is split into three colab notebooks. They are:

1. Text_Coherence_Dataset_Generation
It contains code to synthesize the two datasets whose details are mentioned in the report:
1. Where the Reddit posts and comments are considered separately
2. Where the Reddit Posts and top 10 comments are considered.
- Note: To run this notebook successfully, make sure to have the redditDataset folder in your google drive root directory.
- Use the following link to download the zip dataset folder:
https://www.kaggle.com/ammar111/reddit-top-1000
- Then extract it, rename it to redditDataset and upload it on your drive before running the steps ahead.

	
2. Text_Coherence_Pre-Processing
It contains code for data pre-processing and vector embedding generation as described in the report.
- This notebook directly imports social media and NTSB testing and training data from Kaggle.
- Importing GloVE embeddings is done from Google Drive
- The following pre-processing steps are followed:
	- Sentence Level Cleaning: Removing non-alphanumeric characters
	- Word/Token Level Cleaning: Stem each word + remove stop words
	- Genism simple_preprocess
	- LDA based Topic Modelling
	- GloVE embeddings generation for each sentence
- Output: Word embeddings for training and testing of NTSB and social media corpus.
- A sample of generated embeddings is also included at the end of the Colab sheet.
- Note: Cells can take in excess of an hour to complete and can overload RAM so run relevant cells only.

3. TextCoherenceModel
It contains the code for training and testing the text coherence model.
- Note you must have previously run the notebook to preprocess and generate word
embeddings for each of the datasets. This notebook trains and tests models for three datasets:
	- One is the generated Social Media dataset which considers posts and comments as separate documents.
	- One is the generated Social Media dataset which considers posts and top 10 comments as single documents.
	- One is the Accidents Report dataset which is the standard dataset used for text coherence analysis.
- We train our model on all three datasets, and for each model, we test on all three sets. See the report for result analysis.
- Ensure the word embeddings for the training data and testing data are present in your google drive. For our notebook, we kept a folder named nlp in google drive which had three sub-folders: separate, combined and accident. All three folders had 2 files each: the word embeddings for training and testing dataset.
- Once the word embeddings are present in the required folder with names mentioned in the
notebook, you can easily run the notebook.
- Note: It takes a few hours for training and testing to be complete.