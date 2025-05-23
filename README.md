Topic Modeling Technical Report

Course: Mathematics and Statistics for Data Science.
Submitted by: Harpreet Kaur
Date:05/03/2025

1. Introduction
This report presents the end-to-end application of topic modeling algorithms on the 20 Newsgroups dataset (20news-19997). The objectives include:
•	Implementing topic modeling techniques (NMF and LSA)
•	Visualizing discovered topics and clustering of documents
•	Quantitatively evaluating topic quality (coherence and distinctiveness)
•	Interpreting sample topics with top words
•	Summarizing methodology and findings
2. Data and Preprocessing
Dataset: A tar archived collection of ~20,000 newsgroup posts across 20 categories.
Steps:
1.	Extraction: Decompressed 20news-19997.tar.gz and loaded text files from each category.
2.	Cleaning: Removed non alphabetic characters; lowercased all text.
3.	Tokenization & Lemmatization: Used a regex-based tokenizer to extract lowercase word tokens of length ≥2, removed NLTK English stop-words, and applied WordNet lemmatization.
4.	Vectorization: Constructed a TF-IDF matrix X with max_df=0.95, min_df=2 to filter overly common and rare terms.
3. Topic Modeling Algorithms
We applied two matrix decomposition techniques:
1.	Non-negative Matrix Factorization (NMF): Decomposes X ≈ W H, enforcing non-negativity for interpretability.
2.	Latent Semantic Analysis (LSA): Uses truncated SVD to factorize X into orthogonal components.
For each model, we varied the number of topics kk from 5 to 15.
 
4. Evaluation Metrics
4.1 UMass Coherence:
 
4.2 Distinctiveness:
•	Measures overlap of top-10 words across topics; higher values (closer to 1) indicate more unique topic vocabularies.
For each kk, we recorded coherence and distinctiveness for both NMF and LSA, then identified the best kk by maximum coherence.
5. Results
5.1 Optimal Number of Topics
Method	Best kk	UMass Coherence	Distinctiveness
NMF	10	-0.85	0.78
LSA	8	-1.10	0.72
5.2 Coherence vs. k
Figure 1: Coherence scores for NMF and LSA across k=5–15.

 
5.3 Topic Clusters Visualization
•	Applied t-SNE to the document-topic matrix WW for both NMF (k=10) and LSA (k=8).
•	Figure 2: t-SNE plot of documents colored by dominant NMF topic.
6. Sample Topic Interpretation (NMF, k=10)
Topic	Top-10 Words	Interpretation
1	space, orbit, nasa, launch, mission, satellite, crew,...	Space & NASA
2	god, christian, bible, faith, church, jesus, worship,...	Religion: Christianity
3	file, window, drive, card, disk, pc, memory,...	Computer Hardware
...	...	...
7. Methodology & Findings
•	Preprocessing choices (e.g., min_df, lemmatization) significantly affected topic clarity.
•	NMF outperformed LSA in coherence, yielding more interpretable topics.
•	Distinctiveness scores indicated moderate overlap, suggesting potential for hierarchical topic refinement.
•	Visualization confirmed well-separated clusters under NMF.
8. Conclusions & Future Work
•	Conclusions: NMF with k=10k=10 provides the best balance of coherence and distinctiveness for this dataset.
•	Future Directions: Explore bigram/trigram inclusion, hierarchical topic models (hLDA), and dynamic topic modeling over time.
 
Report generated by topic modeling pipeline on 20 Newsgroups data.

![image](https://github.com/user-attachments/assets/c392aab5-91b5-43b5-8334-2744dbc45cbc)
