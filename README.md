End to End Sentiment Analysis System Using Natural Language Processing (NLP) and Machine Learning (ML) ReadME

This project builds a complete end‑to‑end sentiment analysis pipeline for customer product reviews from a Flipkart dataset obtained from the Kaggle website.  It covers data loading, Natural Language Processing (NLP), feature engineering (Bag-of-Words and Term Frequency – Inverse Document Frequency), model training and evaluation, model persistence and two machine learning (ML) models – Naïve Bayes and Logistic Regression - to classify text (such as product reviews) into three categories: positive, negative, or neutral.  The project also builds a graphical user interface (GUI) using Tkinter to display side-by-side sentiment predictions from the two ML models.  It is designed as a clean, reproducible template for sentiment analysis projects in Python.
Code repository: https://github.com/henrykwong-ai-ds-ml/FlipKartSentimentAnalysis 
1.	Project Overview
The goal of this project is to build an end-to-end sentiment analysis system that predicts whether a customer review is Positive, Negative, or Neutral. The system is trained on real product review data and reveals its predictions through a simple GUI where users can select reviews by clicking navigation buttons back and forth to see its sentiment along with an emoji.
Key components:
•	Data: Flipkart Product Reviews with Sentiment dataset from Kaggle (Reviews + Sentiment labels).
•	NLP preprocessing: tokenization, lowercasing, stopword removal, basic text cleaning and lemmatization.
•	Feature engineering: Bag-of-Words using CountVectorizer, TF IDF using TfidfVectorizer.
•	Models: Multinomial Naive Bayes (MultinomialNB) from scikit learn, suitable for text data represented as word-count features and Logistic Regression also from sklearn, suitable for scaling word weights by their unique importance.
•	Evaluation: train/test split, confusion matrix, classification report, and accuracy/F1 score.
•	Deployment: Tkinter GUI application that loads the saved vectorizers and models via pickle, then performs predictions on selected reviews.

2. Dataset
•	Dataset: Flipkart Product Customer Reviews with Sentiment.
•	Provider: Kaggle, created for sentiment analysis tasks.
•	Format: CSV file with product and review information.
This dataset is a good fit because it already includes labeled customer reviews and 3 sentiment classes, making it practical for demonstration and GUI usage.
3.	Project Structure
•	data/: Raw and processed CSV file.
•	src/: Core Python modules for data, modeling, and evaluation.
•	models/: Saved fitted vectorizer and classifier, serialized with pickle.
•	app/: Tkinter GUI application script.
•	reports/: Confusion matrix plot, classification report, and final PDF report.
4.	Methods and Pipeline
a.	NLP preprocessing
•	Tokenization
•	Stopword removal
•	Lemmatization
b.	Feature Engineering
•	Bag-of-Words with Countvectorizer
•	TF-IDF with TfidfVectorizer
c.	Model Training
•	MultinomialNB from sklearn.naive_bayes, which is designed for text classification problems with discrete word count features.
•	Logistic Regression from sklearn.linear_model, which is designed for taking numeric text features from Bag-of-Words or TF-IDF and learns weights that map them to class probabilities for each sentiment label. It can be extended from binary to multiclass classification, so it can directly model reviews in a single, interpretable linear classifier.
d.	Evaluation
•	Accuracy: Overall proportion of correctly predicted reviews
•	Precision, recall, and F1-score per class: Summarized in a classification report
•	Confusion matrix: Visualizes how many examples of each true class were predicted as each other class.
•	These metrics help quantify how well the model distinguishes between positive, neutral and negative sentiments and identify where it tends to make mistakes.
e.	Model Persistence
•	The trained vectorizers and models are saved using pickle:
•	Vectorizer.pkl stores the fitted CountVectorizer or TF-IDF vectorizer including learned vocabulary and parameters.
•	Sentiment_model.pkl stores the trained MultinomialNB classifier with learned parameters.
•	Logistic_Regression_model.pkl is the saved version of our trained Logistic Regression classifier, storing a file so that it can be loaded later without retraining. The GUI will load this file into memory and used it to predict the sentiment of reviews based on their vectorized text features.
5.	Tkinter GUI Application – the GUI is built using Tkinter, Python’s standard library for desktop interfaces. Two navigation buttons, “Previous Review” and “Next Review’ are displayed at the bottom of a dashboard window.  Actual Review and Summary comments are displayed. At the top of the window we have the predicted sentiment label and corresponding emoji – “Happy”, “Neutral”, and “Angry.” The GUI is a thin front-end layer, while the ML pipeline handles the actual sentiment analysis logic. 

6.	Installation and Setup
a.	Prerequisites: Python 3.x installed and a virtual environment to isolate dependencies is strongly recommended.
b.	Dependencies: 
•	Python as the programming language for writing project code.
•	Tkinter for the GUI framework for Python to create a user interface.
•	Scikit-learn (sklearn) for the machine learning library used to train the sentiment classifier.
•	NLTK as the Natural Language Toolkit for text preprocessing: stopwords, tokenization and lemmatization.
•	Pandas for data manipulation and loading the dataset.
•	Matplotlib and Seaborn for displaying emojis in a Tkinter window and for generating a confusion matrix.
•	Pillow to manage image loading and manipulation.
•	Pickle as model persistence for saving and loading the trained machine learning model and vectorizer.
7.	Usage through loading the dataset, training the model, launching the GUI and using the simple navigation buttons in the display window to view reviews, comments and predicted sentiments and emojis.
8.	Limitations
a.	The models may struggle with conditional statements, sarcasm, mixed or neutral reviews, slang and other language cues, or non-English words.
b.	Misclassifications and model bias may arise from class imbalances such as being trained and overfitted with positive reviews leading to lower precision and recall when trying to identify genuinely neutral or negative reviews.
c.	Naïve Bayes operates on the strict unrealistic assumption of feature independence (words have no relationship to each other).
d.	Logistic Regression assumes a linear boundary between sentiment classes leading to struggles with non-linear text patterns where meaning shifts dynamically based on context.
e.	Vector vulnerability as our vectorizers are capped at max_features=5000. Any new words, jargon or typos that do not appear in the top 5000 training terms are completely ignored by the dashboard.
9.	Future Work
a.	Use stronger models such as Linear Support Vector Machines (SVM) or transformer based models such as DistilBERT for improved accuracy.
b.	Add more nuanced sentiment classes such as “very positive” or “very negative” to possibly improve accuracy. 
c.	Make architectural changes to scale the project for thousands of users. Deploy a web service such as Flask/FastAPI.
10.	Citation/Acknowledgement
a.	Dataset: “Flipkart Product Customer Reviews with Sentiment dataset provided via Kaggle.”
b.	Libraries: Python, pandas, scikit-learn, NTLK, Matplotlib, Seaborn, Pillow, Pickle, Tkinter.



