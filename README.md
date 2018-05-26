# Spam_Classification
A project on using different word embedding with CNN to classify spam (Python)

## Project Introduction
It is often that we need to incorporate information in text into our model in machine learning tasks. However, machine can't read words like we do, therefore we would have to perform word embedding in order to transfer the words into numerical vectors. In this project, we aim to do serveral embedding, including tradional bag-of-words models such as word count, tf-idf score and more recent vector-space models such as Word2vec and NN embedding. We will then model the extracted features to classify our data in to spam/ham with a special structured CNN (Convolutional Neural Network). 

## Model Structure
The CNN architecture is inspired by Zhang, Y., & Wallace, B. (2015) ["A Sensitivity Analysis of (and Practitioners’ Guide to) Convolutional Neural Networks for Sentence Classification"](https://arxiv.org/pdf/1510.03820.pdf) and [this article](https://towardsdatascience.com/another-twitter-sentiment-analysis-with-python-part-11-cnn-word2vec-41f5e28eda74)

[Model Structure](Model Structure.jpg)

The above structure is specificly designed for word vectors input. First we can see that the width of each filter is exactly the same as the input width, reason for it is that a word vector contains information of the word as a whole. The other interesting part is the different size of filters, looking it closely we can see that they are actually filters that try to capture bigram, trigram, and fourgram information. After convolutional layer and max pooling layer, it simply concatenated max pooled result from each of bigram, trigram, and fourgram, then build one output layer on top of them. The actual model we will be using is similiar to the defined structure, but we added one fully connected hidden layer with dropout before the output layer since we will be using larger number of filters comparing to the example. 

## Data Description
The project take use of The [SMS Spam Collection Dataset on Kaggle](https://www.kaggle.com/uciml/sms-spam-collection-dataset), the data description on the webpage is as followed :

Context
The SMS Spam Collection is a set of SMS tagged messages that have been collected for SMS Spam research. It contains one set of SMS messages in English of 5,574 messages, tagged acording being ham (legitimate) or spam.

Content
The files contain one message per line. Each line is composed by two columns: v1 contains the label (ham or spam) and v2 contains the raw text.

This corpus has been collected from free or free for research sources at the Internet:

-> A collection of 425 SMS spam messages was manually extracted from the Grumbletext Web site. This is a UK forum in which cell phone users make public claims about SMS spam messages, most of them without reporting the very spam message received. The identification of the text of spam messages in the claims is a very hard and time-consuming task, and it involved carefully scanning hundreds of web pages. The Grumbletext Web site is: [Web Link]. -> A subset of 3,375 SMS randomly chosen ham messages of the NUS SMS Corpus (NSC), which is a dataset of about 10,000 legitimate messages collected for research at the Department of Computer Science at the National University of Singapore. The messages largely originate from Singaporeans and mostly from students attending the University. These messages were collected from volunteers who were made aware that their contributions were going to be made publicly available. The NUS SMS Corpus is avalaible at: [Web Link]. -> A list of 450 SMS ham messages collected from Caroline Tag's PhD Thesis available at [Web Link]. -> Finally, we have incorporated the SMS Spam Corpus v.0.1 Big. It has 1,002 SMS ham messages and 322 spam messages and it is public available at: [Web Link]. This corpus has been used in the following academic researches:

Acknowledgements
The original dataset can be found here. The creators would like to note that in case you find the dataset useful, please make a reference to previous paper and the web page: http://www.dt.fee.unicamp.br/~tiago/smsspamcollection/ in your papers, research, etc.

We offer a comprehensive study of this corpus in the following paper. This work presents a number of statistics, studies and baseline results for several machine learning methods.

Almeida, T.A., GÃ³mez Hidalgo, J.M., Yamakami, A. Contributions to the Study of SMS Spam Filtering: New Collection and Results. Proceedings of the 2011 ACM Symposium on Document Engineering (DOCENG'11), Mountain View, CA, USA, 2011.
