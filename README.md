# Review of models for Rotten Tomatoes review dataset
>Currently a rough draft.  To see a finished analysis, view my other projects [Spark Logistic Regression](https://github.com/metriczulu/pyspark_log_reg_model) or [Personality Test Analysis](https://github.com/metriczulu/open_source_personality_analysis)

The Rotten Tomatoes review dataset was originally posted on Reddit by */u/nicolas-gervais*, who had scraped it from the RT website.  The scraped used can be found on his github at:

*https://github.com/nicolas-gervais/6-607-Algorithms-for-Big-Data-Analysis/blob/master/scraping%20all%20critic%20reviews%20from%20rotten%20tomatoes*

This is a large-ish dataset with 440k reviews.  Each review is labeled either 1 for ‘Fresh’ or 0 for ‘Not Fresh.’  The dataset is completely balanced with respect to the labels, there is no missing data, and it consists of a single independent variable.  Due to all these factors, EDA is not done in these scripts and I skip straight to the model building process.

In the different scripts uploaded here, I build multiple models for the data using traditional bag-of-words NLP techniques and more advanced RNN/CNNs.  The RNN/CNN models are split into two Jupyter notebook scripts, one in which the word embeddings are learned as the model is trained and one which uses pretrained GLoVe vectors from twitter data.

The bag-of-words notebook was run on my local PC and the two CNN/RNN scripts were run on Google Colab for that free GPU.  This has the effect that the loading of the dataset is done slightly differently for each notebook.

All models built use my wordvecpy package for text processing and for generating the embedding matrix for the pretrained GLoVe vectors.

Surprisingly, of all the models trained I found simple logistic regression on a count matrix to be the most accurate and—by far—faster to train than more advanced methods using ensemble decision trees or neural networks.  Multinomial Naïve-Bayes trained faster that logistic regression and came close in accuracy.

## Future Plans

Currently working on expanding my wordvecpy package to grant support for generating ELMO embeddings for large datasets.  Words are represented differently in ELMO based on the context of the doc they are in and should give a significant accuracy boost over the pretrained GLoVe vectors.  

Additionally, working on a standalone class to use BERT as a simple classifier and see how accurately in classifies this data.

## License
None

