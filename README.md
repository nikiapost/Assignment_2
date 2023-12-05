# BASIC INFO:
#### The name of the dataset
Edina Self-dialogue. (as noted in the Assignment)
The Self-dialogue Corpus. (as noted in their GitHub)

#### What kind of data it is (domain, modality)
The Self-dialogue Corpus is a collection of open-domain self-dialogues in text modality, which covers various domains such as entertainment (movies, music), sports and general topics (opinions, favorite things etc.). Specifically, a collection of raw CSVs from Amazon Mechanical Turk, sorted by individual tasks/topics. These topics are about music, movies and sports and subtopics within these.

#### Where you downloaded it from (include the original URL)
From their GitHub Account, as noted in the Assignment. Original URL: https://github.com/jfainberg/self_dialogue_corpus.git 

#### How it was collected
This paper proposes a novel way to gather domain specific, conversational data in an efficient, cost-saving way: self-dialogues through crowdsourcing. Instead of a standard, two party conversation, self-dialogues are fictitious conversations orchestrated by one person who plays both parts in a dialogue. Using this technique they collected a corpus of approximately 3 million words across 23 topics via Amazon Mechanical Turk, that they make available alongside their paper.
Specifically, this corpus was collected using Amazon Mechanical Turk (AMT). To harvest self-dialogues, they asked Workers to create a fictitious two-party conversation around a topic. For the majority of the tasks, the Workers were requested to fill 20 text boxes with a conversation on a particular topic. The setup required all 20 text boxes to be completed in order to submit.
In order to obtain conversations that were as natural as possible, they limited the number of constraints set in the task descriptions. They aimed to present tasks that were simple to execute. The only rejection criteria related to abusing the system, such as submitting (near) duplicate entries or content with exaggerated bad language. To deal with the large amount of submissions, they automated the rejection procedure by 1. comparing the cosine similarity between bags of words of two dialogues and 2. flagging conversations which contained a large number of words from a bad-words list.
In total only eight out of 2,717 Workers were banned, and 145 conversations (~0,6%) were rejected.

#### What kind of dialogue system or dialogue system component it's designed for
By design, open-domain conversational agents require the ability to converse about a broad set of topics in a fluid and unconstrained manner while keeping dialogue with the end-user coherent, clear and engaging.
The intended purpose of the dataset is to train conversational agents. Suitable for open-domain human-bot conversational settings.

#### What kind of annotation is present (if any at all), how was it obtained (human/automatic)
Their paper does not refer explicitly to annotation, but through their own words, we can conclude that there is some kind of annotation obtained by humans. Firstly, the dataset is shorted in 23 different topics, so there should be topic labels for them. Also, in their paper, when they discuss the comparison with Open Subtitles they conclude that their corpus is promising for comparisons when name-entities are involved. So, there should also be name-entities annotations.
They, also, refer to labelling some conversations, such as as “partially” complete. This takes place when prompting two Workers to hold a conversation with one another in order to investigate the differences between their corpus and standard two-party conversations. So, in cases where one Worker is disconnected mid-task, they instruct the remaining Worker to imagine how the conversation would continue and finish their 15 messages accordingly in order for him to receive the payment.
Throughout the paper there is no reference to sentiment labels or dialogue acts.

#### What format is it stored in
The format of the dataset is stored in raw CSVs from Amazon Mechanical Turk, sorted by individual tasks/topics.

#### What is the license
Self_dialogue_corpus is licensed under the BSD 3-Clause "New" or "Revised" License. This is a permissive license similar to the BSD 2-Clause License, but with a 3rd clause that prohibits others from using the name of the copyright holder or its contributors to promote derived products without written consent.

Description/paper that came out with the data, used to extract the above info: https://arxiv.org/pdf/1809.06641.pdf  

# MEASUREMENTS
Firstly, by checking the dataset:
a.	there was no clear separation between a user and a system, as it is one human making the dialogues for both user and system, and
b. there was no train/dev/test split.
So, I will provide the overall numbers.

In general, from their README file on their GitHub page, the info says that it is a corpus of 3.6 million words across 23 topics. 

To begin with the measurements asked, firstly I converted all .csv files into .txt files, using the get_data.py that can be found on their README file. It is a preprocessing script that changes format from .csv to .txt and by default saves the created .txt files in a folder called dialogues. But it doesn’t keep the structure of the .csv files (which were all stored in a file named corpus and then in subfiles of different topics). The .txt files are stored all together in a file names dialogues. So, each file is a different dialogue, but we don’t know the category it belongs to.
Because of that, I later decided to work on the .csv files directly, so as to get more accurate measurements regarding the topics as well, and not just the dataset as a whole. The .csv measurements are presented below:

.CSV FILES

#### Total data length (in terms of dialogues, turns, sentences, words)

TOTAL DATA LENGTH Measurememnts (analysis_csv.ipynb)  Paper (GitHub) README (GitHub)
Total Dialogues		        24.249				   			24.283			24.165
Total Turns		            1.455			  				141.945				-
Total Sentences		        958.803							-				    -
Total Words		            5.694.981			   			3.653.313		3.653.313

As we can observe there are some differences:
a.	About the number of the total Dialogues, the .csv measurements shows a small differantiation in regards to their own measurements. Of course, those as we can see, are different on their paper on GitHub and on their README on GitHub!
b.	As for the number of total Turns, my calculations on the .csv file probably failed to compute appropriately.
c.	The number of total Words is much higher than their own measurements (which this time coincide).
d.	And finally, as there is no mention of the number of total sentences neither on their paper nor in their README file, we cannot conclude to a comparison.

#### Mean/std dev dialogue lengths (in terms of dialogues, turns, sentences, words)
The values below provide an insight into the average length and variability/spread of dialogues, turns, sentences, and words within each dialogue across the dataset. They give an indication of  the structure of the typical dialogue and the range of variation/spread in the length of dialogues in terms of dialogues, turns, sentences, and words:

Mean/Std Dev Dialogue Lengths:
Mean Dialogue Length (Dialogues): 384.9047619047619
StdDev Dialogue Length (Dialogues): 258.1223233020501
Mean Dialogue Length (Turns): 22.740154233164255
StdDev Dialogue Length (Turns): 2.546752108033262
Mean Dialogue Length (Sentences): 39.53989855251763
StdDev Dialogue Length (Sentences): 5.128629772166213
Mean Dialogue Length (Words): 234.85426203142399
StdDev Dialogue Length (Words): 74.36175345292521

Note that in the analysis_csv.ipynb file there are also results of the mean/std dev dialogue lengths per topic, (which is not included in the report because of their size).

#### VOCABULARY SIZE
The number of all the unique words in the vocabulary of the dataset is 117187 words. 

##### Vocabulary Size Per Topic:
Below there is the calculation of the vocabulary size per topic: 

Topic: action, Vocabulary Size: 5932
Topic: baseball, Vocabulary Size: 10761
Topic: basketball, Vocabulary Size: 9406
Topic: beatles, Vocabulary Size: 7554
Topic: comedy, Vocabulary Size: 5647
Topic: disney, Vocabulary Size: 17097
Topic: fashion, Vocabulary Size: 6761
Topic: fast_furious, Vocabulary Size: 4321
Topic: harry_potter, Vocabulary Size: 5750
Topic: horror, Vocabulary Size: 6310
Topic: icehockey, Vocabulary Size: 4882
Topic: lady_gaga, Vocabulary Size: 5773
Topic: movies, Vocabulary Size: 44744
Topic: music, Vocabulary Size: 49886
Topic: music_and_movies, Vocabulary Size: 6314
Topic: nfl_football, Vocabulary Size: 28460
Topic: pop, Vocabulary Size: 7839
Topic: rap_hiphop, Vocabulary Size: 8427
Topic: rock, Vocabulary Size: 8317
Topic: star_wars, Vocabulary Size: 14013
Topic: superhero, Vocabulary Size: 5712
Topic: thriller, Vocabulary Size: 9134
Topic: transition_music_movies, Vocabulary Size: 1270

# Impressions
After a closer look at the dataset and their paper, where at the end they present unedited self-dialogues from various topics to show the nature of the collected data, my findings agree that the data look extremely natural, and that was the goal as they mention in their paper. Specifically the data appear to be very structured and at the same time maintaining the oral speech in a more informal way. In summary the natural way people talk with each other about a variety of everyday things.

It would be easy for this dataset to learn from, because it is very well structured and cleaned, with no noise that needs removal. Also, as they present in their paper, they’ve made a comparison with other datasets and they had very good results: By comparing self-dialogues with standard two-speaker conversations, they demonstrate the advantages in terms of costs, simplicity, efficiency, and quality of their collected data. The self-dialogues tend to present better coherence and engagement. Also, by comparing their corpus to the one of Open Subtitles they’ve concluded that their corpus is more suitable for open-domain human-bot conversational settings.

In an actual system it is my understanding that it will be very useful because they have captured and integrated the naturalness of a human dialogue at a very high level. Also, as they have shown in their paper, there are many advantages in terms of cost, quality and suitability for training conversational agents.

As for any problems or limitations, both of them should be related with the actual goal of the people that made the specific dataset. They have built a very good, open-domain dataset that can be used in a variety of tasks. No problems nor limitations found on my behalf. In the case that this dataset is going to be used for domain specific tasks (e.g. Law, Health etc) there probably be a problem, because of the domain, but this is not the goal of the creators so that shouldn’t constitute a problem overall.
