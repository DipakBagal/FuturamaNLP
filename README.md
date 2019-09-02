# FuturamaNLP

I scraped the data and grouped or cleaned the data in the Scrape Script Data notebook. I initially worked on the NLP Analysis notebook (like LSA/NMF and some basic classification), but the the primary notebooks to look at are LDA, Classification, and Text Generation, as those were the three tasks I sought to perform. 

I chose LDA for topic modeling because it seemed to produce topics that made the most sense, and also because I had a relatively easy way to tune it to my liking. However, none of the dimensionality reduction helped me in my primary goal, which was to perform character identification.

For the classification, a simple tfidfvectorizer with a gricsearched SGDClassifier seemed to work best (support vectors in general seem to work better than decisiontrees, even boosted ones). It wasn't very good though, about 55% accuracy, which I attribute to dialogue being so full of action words or common words, while there are also a lot of nonsensical words in the script that make it hard to tell who is speaking for many of the lines.

Finally, the icing on the cake was my bender bot. I trained it using LSTM on my home computer using tensorflow-gpu (on my 2080ti, muhaha) for about 2 full days (it is nice that the modeling can be paused and resumed). I tried several different optimizers and ultimately chose to use Adam with an extra dropout layer (I would not recommend this typically, as this dramatically increased my train time, from 150s epochs to 700s). I took my model and created a flask app that generates text whenever the user wants. The text is generated from a randomly selected sequence of 100 letters, and produces 100 more.
