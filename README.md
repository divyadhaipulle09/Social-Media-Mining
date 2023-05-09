# Social-Media-Mining 

The Fallout of a Wrong Answer: Analyzing Public Sentiment on Bard's Accuracy Reputation. (1398 words) 
Divya Dhaipullay, MS in Data Science, 2nd Semester, Indiana University
 


 
1.	    Introduction
The importance of a company's reputation in its success cannot be overstated. It can impact public trust, consumer behavior, and even financial performance [1,3]. Inaccuracies in a company's products or services can have a detrimental effect on its reputation, as seen in the case of Google, which lost $1 billion due to an inaccurate answer [6]. This study aims to analyze the public sentiment towards Bard's accuracy reputation following an inaccurate answer to a factual question.
2. 	Background & Literature
Dowling's [2] study showed that reputation can significantly affect consumer behavior and brand choice. Similarly, Fombrun and Shanley's [3] study found that a company's reputation can impact its financial performance. In terms of sentiment analysis, Liu [4] conducted a survey of sentiment analysis and opinion-mining techniques in social media, while Zhang et al. [5] proposed a deep-learning approach for sentiment analysis of online reviews. 
This study focuses on addressing the following questions.
How does an inaccurate answer to a factual question from Bard impact the perception of its reputation among the public?

3. Methods
This section specifically discusses the data collection and the analysis method to answer the research questions outlined above.

3.1	Data
The data was collected from two social media platforms, Twitter and Reddit, using two different tools, Optimized-Modified-GetOldTweets3-OMGOT and PRAW-Python Reddit API Wrapper, respectively.
For Twitter, the keywords "bard" and "accuracy" were used, and data in the form of comments were collected using pagination. The collected data included the tweet ID, the date of the tweet, the text of the tweet, and the username of the user who posted it. The data collection period was from February 3rd, 2022, to February 25th, 2023.
For Reddit, data in the form of comments was collected from various subreddits like r/technology, r/stocks, r/bardai, r/wallstreetbets, r/ProgrammerHumor, r/ChatGPT,  r/AskReddit,  r/programming, r/iiiiiiitttttttttttt, r/artificial, r/singularity, r/CryptoCurrency were selected for Reddit as most AI-related discussions happen. using specific keywords like 'chatgpt', 'google', 'bard', 'bard.ai', 'accuracy', 'ai', 'openAi', 'bing', 'people', and 'think' to filter the data. The collected data included the Reddit ID, title, author, timestamp, number of comments, and score (number of upvotes) for each comment. Finally, approximately 600 data points from both platforms were combined and stored in a CSV file format 

3.2 	Analysis

The methods used include NRC Emotion Lexicon and Vader sentiment analyzer, and creating a correlation matrix and heatmap, text processing using stop word removal, punctuation removal, and lowercasing, word frequency analysis using Counter, and topic modeling using Gensim.

For sentiment analysis, the NRC Emotion Lexicon and Vader sentiment analyzer are loaded, and we get the emotion counts and sentiment scores. Using Vader sentiment scores we get the sentiment of each comment returning 'Very positive', if the sentiment score is greater than 0.5, 'Positive', if it's greater than 0.05 but less than or equal to 0.5, 'Very negative’, if it's less than -0.5, 'Negative', if it's less than or equal to -0.05 but greater than -0.5, and, if it's between -0.05 and 0.05 inclusive else it is Neutral. We then calculate the average emotion scores for each column and get the sentiment based on the sentiment score.

For text processing and analysis, clean the text by removing stop words and punctuation and lowercasing the text. For topic modeling, preprocessing of data is done using spaCy for lemmatization and stop word removal, converted into a bag of words representation, and a dictionary of words and their frequency is created. The dictionary is filtered to remove words that occur in less than 5 documents or more than 50% of the documents. The number of topics is evaluated using coherence scores, and the LDA model is trained on the corpus with the optimal number of topics. The topics and their corresponding words are printed and visualized. 


4	Results

Each post could be coded majorly in only one category. Definitions for each category and examples of each are enumerated in Table 1 (below).

Category	Definition	Example

Positive	
Comments with sentiment scores greater than 0.05	
" When errors in Google's chatbot Bard were detected in their demo video Google's market cap dropped by $100B. Bard was released on Feb 7th- interested to see how it will improve its accuracy over time. #MIST5720”



Very Negative	

Comments with sentiment scores lesser than -0.5	

"Interesting! So how can AI-based recruitment systems judge whether the interviewee is looking at the camera? AI challenges AIAI Wars: Google stock tumbles -5% premarket as Bard AI gives wrong answer at launch event Microsoft to incorporate ChatGPT into Bing"


Negative	Comments with sentiment scores lesser than -0.05	"Google Losing Accuracy and Market Value: Its AI named ""Bard"" is being taken by the market as aÂ lousy product basically. It isn't very accurate. A Google is now 13% off the Feb highs. A Close to 200m shares traded in 2 days.  Google gets most of its revenue frâ€¦https://t.co/7qwNM7crO7"


Slightly positive	Comments with sentiment scores in the range of 0 to 0.05, inclusive
	" 2. Google has announced their own AI chatbot Bard which rivals the Microsoft-backed ChatGPT but experts are urging caution due to accuracy concerns.”
Slightly Negative	Comments with sentiment scores in the range -0.05 to 0, inclusive	"I built a chrome extension to turn ChatGPT into "Grammarly" letting me see what changes it made to my content and allowing me to accept and reject the revisions
		
Table 1. Category definitions and examples for sentiment analysis using VADER
The results of the data analysis indicate that emotions are not independent but rather co-occur with each other to varying degrees. Fear has a moderate positive correlation with Anger, Negative, and Sadness, indicating that these emotions are likely to co-occur. Similarly, Anger has a moderate positive correlation with Negative and Disgust, indicating that these emotions are also likely to co-occur (Figure 1).

Trust has a weak positive correlation with Joy, suggesting that people are slightly more likely to trust when they experience joy. The same is true for Surprise, which has a weak positive correlation with Joy, indicating that people are slightly more likely to be surprised when they experience joy.

Positive has a weak positive correlation with Trust and Joy, indicating that when people experience Trust or Joy, they are slightly more likely to feel positive. These results suggest that emotions are not isolated experiences but rather have a complex and interconnected relationship with each other.

 
  Figure 1. Correlation Matrix for NRC sentiment analysis

Positive Sentiment Word	Frequency
ai	31
chatgpt	29
accuracy	18
Bard	16
Google	14
People 	11
Search	10
Answer	7
will 	7
Bing	6
chatbot	6
made	6
Table 2. Positive Sentiment Word	Frequency


Negative Sentiment Word	Frequency
ai	16
Bard	15
Google	13
accuracy	13
bing	12
chatgpt	12
People	10
Will	9
One	7
Using	7
Googles	6
Market	5
Table 3. Negative Sentiment Word	Frequency

For the positive sentiment text, the code outputs a table of the top 12 most common words and their frequencies. The most frequent word is "ai" with a frequency of 31, followed by "chatgpt" with a frequency of 29. Other frequent words include "accuracy", "Bard", "Google", "People", "Search", "Answer", "will", "Bing", "chatbot", and "made".

For the negative sentiment text, the code outputs a table of the top 12 most common words and their frequencies. The most frequent word is "ai" with a frequency of 16, followed by "Bard" with a frequency of 15. Other frequent words include "Google", "accuracy", "bing", "chatgpt", "People", "Will", "One", "Using", "Googles", and "Market".
 
Figure 2: Most repetitive words

Some words, such as "ai", "accuracy" and "Bard", appear frequently in both the positive and negative sentiment text, which suggests that they may be more related to the topic being discussed rather than the sentiment itself. Based on the given topic-term matrix after removing stop words, we can observe that there are 4 topics in total. The matrix represents the probability of each term being present in each topic. The terms with the highest probability for each topic are:

Topic 0: "AI", "machine", "learning"
Topic 1: "Bard", "Google", "Alphabet"
Topic 2: "accuracy", "ChatGPT", "people"
Topic 3: "year"

Note that the topics seem to be more distinct and informative after removing the stop words. However, some common terms still appear in multiple topics, such as "AI" and "machine learning." Based on the topic distribution table, it appears that the text is related to various topics, including AI and machine learning (Topic 0), tech companies such as Google and Alphabet (Topic 1), and perhaps some discussion about accuracy and people (Topic 2).

 
Figure 3. Topic-wise Term Distribution of the most frequent words using Topic Modelling

The results below show that the most common emotions expressed in the dataset are "positive" and "trust". "Positive" emotion was expressed in 19.5% of the data, while "anticipation" was expressed in 0.0%. "Negative" emotion was expressed in 11.2% of the data, followed by "trust" at 10.4%. The least common emotions expressed in the data were "disgust" and "sadness", with only 1.4% and 3.6% respectively. The emotion "surprise" was expressed in 2.3% of the data.

Sentiment	Percentage
Anticipation	0.0%
Trust	10.4%
Surprise	2.3%
Positive	19.5%
Negative	11.2%
Sadness	3.6%
Disgust	1.4%
Table 4. Sentiments and their counts in Percentages

It appears that although the impact of incorrect answers from Google Bard was not perceived as entirely negative, people still hold onto the hope that Google's reputation will not be greatly affected by just one wrong answer.

5	Discussions

	The study highlights the potential usefulness of sentiment analysis in reputation management providing insights into public perception of Bard's accuracy and reputation.

5.1	Limitations & Future Directions
	The study focuses on only one inaccurate answer from Bard, which may not be representative of the company's overall accuracy reputation. Future studies could explore the impact of multiple inaccurate answers on public sentiment. Additionally, the study only collected data from Twitter and Reddit, which may not be representative of the general public's sentiment toward Bard. Future studies could collect data from other social media platforms or conduct surveys to obtain a more comprehensive understanding of public sentiment toward Bard. 

5.2	Conclusion

	Inaccuracies, even in a single product or service, can have a detrimental effect on a company's reputation, which in turn can significantly affect consumer behavior and brand choice. The case of Google losing $1 billion due to an inaccurate answer underscores the significance of accuracy in a company's products and services. Despite the negative impact, people still hold onto the hope that Google's reputation won’t be largely impacted suggesting that a company's reputation can be somewhat resilient to isolated incidents of inaccuracies, but a pattern of inaccuracy can have a lasting impact on the company's reputation.

6	References

[1] Roberts, P. W., & Dowling, G. R. (2002). Corporate reputation and sustained superior financial performance. Strategic Management Journal, 23(12), 1077-1093.

[2] Dowling, G. R. (2001). Creating corporate reputations: identity, image, and performance. Oxford University Press.

[3] Fombrun, C., & Shanley, M. (1990). What's in a name? Reputation building and corporate strategy. Academy of Management Journal, 33(2), 233-258.

[4] Liu, B. (2012). Sentiment analysis and opinion mining. Synthesis lectures on human language technologies, 5(1), 1-167.

[5] Zhang, Y., Ye, X., Gao, J., & Wang, W. Y. (2019). Deep learning for sentiment analysis: A survey. Wiley Interdisciplinary Reviews: Data Mining and Knowledge Discovery, 9(4), e1301.


