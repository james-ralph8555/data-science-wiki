- Text frequency-inverse document frequency
- Example:
	Document 1 (d1) : “A quick brown fox jumps over the lazy dog. What a fox!”<br>
	Document 2 (d2) : “A quick brown fox jumps over the lazy fox. What a fox!”<br>
	Question: which document is the word "fox" more relevant to, using tf-idf<br>
	tf(“fox”, d1) = 2/12 , as the word "fox" appears twice in the first document which has a total of 12 words<br>
	tf(“fox”, d2) = 3/12 , as the word "fox" appears thrice in the second document which has a total of 12 words<br>
	An idf is constant per corpus (in this case, the corpus consists of 2 documents), and accounts for the ratio of documents that include that specific "term". Using this definition, we can compute the following:<br>
		idf(“fox”, D) = log(2/2) = 0 , as the word "fox" appears in both the documents in the corpus<br>
		tf-idf(“fox”, d1, D) = tf(“fox”, d1) * idf(“fox”, D) = (2/12) * 0 = 0<br>
		tf-idf(“fox”, d2, D) = tf(“fox”, d2) * idf(“fox”, D) = (3/12) * 0 = 0<br>
	Using tf-idf, the word “fox” is equally relevant (or just irrelevant!) for both document d1 and document d2<br>
