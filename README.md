# Sentiment-Analysis
Dataset Information
We use and compare various different methods for sentiment analysis on tweets (a binary classification problem). The training dataset is expected to be a csv file of type tweet_id,sentiment,tweet where the tweet_id is a unique integer identifying the tweet, sentiment is either 1 (positive) or 0 (negative), and tweet is the tweet enclosed in "". Similarly, the test dataset is a csv file of type tweet_id,tweet. Please note that csv headers are not expected and should be removed from the training and test datasets.

Requirements
There are some general library requirements for the project and some which are specific to individual methods. The general requirements are as follows.

numpy
scikit-learn
scipy
nltk
The library requirements specific to some methods are:

keras with TensorFlow backend for Logistic Regression, MLP, RNN (LSTM), and CNN.
xgboost for XGBoost.
Note: It is recommended to use Anaconda distribution of Python.

Usage
Preprocessing
Run preprocess.py <raw-csv-path> on both train and test data. This will generate a preprocessed version of the dataset.
Run stats.py <preprocessed-csv-path> where <preprocessed-csv-path> is the path of csv generated from preprocess.py. This gives general statistical information about the dataset and will two pickle files which are the frequency distribution of unigrams and bigrams in the training dataset.
After the above steps, you should have four files in total: <preprocessed-train-csv>, <preprocessed-test-csv>, <freqdist>, and <freqdist-bi> which are preprocessed train dataset, preprocessed test dataset, frequency distribution of unigrams and frequency distribution of bigrams respectively.

For all the methods that follow, change the values of TRAIN_PROCESSED_FILE, TEST_PROCESSED_FILE, FREQ_DIST_FILE, and BI_FREQ_DIST_FILE to your own paths in the respective files. Wherever applicable, values of USE_BIGRAMS and FEAT_TYPE can be changed to obtain results using different types of features as described in report.

Baseline
Run baseline.py. With TRAIN = True it will show the accuracy results on training dataset.
Naive Bayes
Run naivebayes.py. With TRAIN = True it will show the accuracy results on 10% validation dataset.
Maximum Entropy
Run logistic.py to run logistic regression model OR run maxent-nltk.py <> to run MaxEnt model of NLTK. With TRAIN = True it will show the accuracy results on 10% validation dataset.
Decision Tree
Run decisiontree.py. With TRAIN = True it will show the accuracy results on 10% validation dataset.
Random Forest
Run randomforest.py. With TRAIN = True it will show the accuracy results on 10% validation dataset.
XGBoost
Run xgboost.py. With TRAIN = True it will show the accuracy results on 10% validation dataset.
SVM
Run svm.py. With TRAIN = True it will show the accuracy results on 10% validation dataset.
Multi-Layer Perceptron
Run neuralnet.py. Will validate using 10% data and save the best model to best_mlp_model.h5.
Reccurent Neural Networks
Run lstm.py. Will validate using 10% data and save models for each epock in ./models/. (Please make sure this directory exists before running lstm.py).
Convolutional Neural Networks
Run cnn.py. This will run the 4-Conv-NN (4 conv layers neural network) model as described in the report. To run other versions of CNN, just comment or remove the lines where Conv layers are added. Will validate using 10% data and save models for each epoch in ./models/. (Please make sure this directory exists before running cnn.py).
Majority Vote Ensemble
To extract penultimate layer features for the training dataset, run extract-cnn-feats.py <saved-model>. This will generate 3 files, train-feats.npy, train-labels.txt and test-feats.npy.
Run cnn-feats-svm.py which uses files from the previous step to perform SVM classification on features extracted from CNN model.
Place all prediction CSV files for which you want to take majority vote in ./results/ and run majority-voting.py. This will generate majority-voting.csv.
Information about other files
dataset/positive-words.txt: List of positive words.
dataset/negative-words.txt: List of negative words.
dataset/glove-seeds.txt: GloVe words vectors from StanfordNLP which match our dataset for seeding word embeddings.
Plots.ipynb: IPython notebook used to generate plots present in report.
