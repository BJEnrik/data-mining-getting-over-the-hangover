<h1 style="color:#000000">I. Executive Summary</h1>

<span style="font-size: 20px">
    A <b>'book hangover'</b> is typically a common phenomenon that book lovers feel especially when they have read an especially good and relatable book (mostly fiction). It is a phenomenon that conjures the sadness and melancholy feelings of a reader, which if not treated immediately, may at worst affect an individual's way of life for a short period of time. A solution to mitigate this feeling is to veer the reader away from the previously read book that triggered the hangover -- by recommending the next book based on it.

<b> The goal of this system is to recommend the next top 5 books based from the previously read book in order to help the affected reader to relieve him or herself from going deep into the book hangover.</b>

The team had developed this <b>Book Recommender System</b> based on the database taken from the `New York Times - Books API`. There are three(3) ways for a reader to search for the top 5 recommended books:
<ol>
    <li>Content-Based Recommender System;</li>
    <li>Description-Based Recommender System; and</li>
    <li>Author-Based Recommender System.</li>
</ol>

In each way, the <b>COUNT VECTORIZER</b> and <b>TF-IDF VECTORIZER</b> were used to extract the <b>Top 5 Recommended Books</b>.

After developing this system, the team found that the TF-IDF is in general better than Count Vectorizers because it not only focuses on the frequency of words present in the corpus but also provides the importance of the words. We can then remove the words that are less important for analysis, hence making the model building less complex by reducing the input dimensions.
</span>

<h1 style="color:#000000">II. Problem Statement</h1>

<center><img src="How_to_.png"/></center>

<span style="font-size: 20px">How to get over a book hangover? Don't know what to read next? To relieve a reader from the empty void feeling after finishing a book - <b>this <u>Book Recommender System</u> aims to present the next top 5 books to read based on a previously read book.</b></span>

<h1 style="color:#000000">III. Motivation</h1>

<span style="font-size: 20px">According to an author from bookriot.com: <blockquote><span style="font-size: 18px"><i>"A <b>'book hangover'</b> is the slangy shortcut for the feeling when a reader finishes a book—usually fiction—and they can’t stop thinking about the fictional world that has run out of pages. The story is over, but the reader misses the characters or the atmosphere of the novel."<sup>1</sup></i></span></blockquote></span>

<span style="font-size: 20px">It is a common phenomenon that the feeling of emptiness consumes bookworms after reading an especially good book. The feeling of sadness or separation anxiety could get worse to the point that it affects the reader's way of living for a short period. Of course, this is not something that anyone would want to happen. One way to get over a book hangover is to search for books similar to one that is previously read. It veers the reader slightly away from the world of the previous book, but not separated from it that the reader would deem it as something not worth reading. It must be similar to the previous one and at the same time fills in the void of that empty feeling.</span>

<span style="font-size: 20px">A reader does not have to feel so empty after finishing a good book after all. Hence, this Book Recommender system aims to present the next top 5 books based on a previously read book - to ultimately fill the void of a book hangover.</span>

<h1 style="color:#000000">VII. Results and Discussion</h1>

<span style="font-size: 20px"><b>Why should we use cosine similarity instead of $L_p$-norm?</b>

<span style="font-size: 16px">
**$L_p$-norm** is basically the distance between two vectors or points. The $L_p$-norm between two vectors $\vec v_1$ and $\vec v_2$ is
$$L_p(\vec v_1, \vec v_2) = \left(\sum_i \left| \vec v_{1_i} - \vec v_{2_i} \right|^p \right)^{1/p}$$

If $p=2$, it is the usual Euclidean distance. If $p=1$, it is known as the city block or Manhattan distance.

On the other hand, the **cosine similarity** between two vectors is related to the angle between them. The cosine similarity between two vectors $\vec v_1$ and $\vec v_2$ is
$$S_\text{cos}(\vec v_1, \vec v_2) = \frac{\vec v_1 \cdot \vec v_2}{\left|\left|\vec v_1\right|\right| \left|\left| \vec v_2 \right|\right|}.$$


If the vectors are nonnegative, which is the case for BoW vectors, its range is $[0,1]$ with 1 implying the two vectors are aligned (most similar) and 0 implying they are perpendicular (least similar).

The cosine similarity is beneficial because even if the two similar data objects are far apart by the Euclidean distance because of the size, they could still have a smaller angle between them. Smaller the angle, higher the similarity.

For recommender systems, one of the most commonly used similarity measures is cosine similarity.
</span>

<span style="font-size: 20px"><b>Which is better? Count Vectorizer or TF-IDF Vectorizer?</b>

<span style="font-size: 16px">

TF-IDF is in general better than Count Vectorizers because it not only focuses on the frequency of words present in the corpus but also provides the importance of the words. We can then remove the words that are less important for analysis, hence making the model building less complex by reducing the input dimensions.
    
</span>

<span style="font-size: 20px"><b>Can we adjust the sensitivity of information retrieval?</b>

<span style="font-size: 16px">
    
Yes. We can also adjust the sensitivity of information retrieval by tuning the min_df and max_df parameter of both the Count Vectorizer and Tf-Idf Vectorizer.

</span>

<h1 style="color:#000000">VIII. Conclusion</h1>

<span style="font-size: 16px">

Recommending books can be based on several things ranging from the book title, and description, to the author. It does not have to be constrained this way as you can always do some recommendations based on a publisher or a set of tags. An even more robust methodology would be to simply combine the context of all previously mentioned basis for recommendation and look for the k nearest similarities.
    
If you're a reader looking to read a book that probably stands in the same parallel setting as the book you have previously read, then a title-based and author-based recommender is the way to go as it simply recommends books based on a similar style of work. Just like the examples, using the title-based recommender off a previously read Starwars book will also give you the next best Starwars book to complement what you have just read.
    
The description-based recommender system on the other hand is unique as it recommends books of similar description. Sometimes, the context of the description is not taken into consideration as the vectorizer only takes words at face value. However, it is not to say that the recommendations are not similar. It should still be similar under a singular theme.
    
</span>

<h1 style="color:#000000">IX. Recommendation</h1>

<span style="font-size: 16px">
    
To take things a step further, the proponents of this project recommend building a more robust recommender by doing a custom recommender. One way to do it would be to combine all of the features like author, description, and title into a single vector and look for similar results. Another way, which the authors strongly recommend is by changing how the recommender system works by dynamically changing the search filtering technique depending on the factors that drive a user. 
    
Another option that one can explore is using other types of distance measurements. Although it might be argued that cosine similarity is the best distance measure for a book recommender system, other distances could also work in this context. The most common similarity measures among book recommender systems are cosine, Euclidian, and Pearson.

Some however use the Adjusted Cosine Vector Similarity function to compute similarity among book ratings to recommend books, to take into account that users have different rating schemes.
</span>

<h1 style="color:#000000">X. References</h1>

<sup>1</sup> The Phenomenon and Psychology of a Book Hangover.Barnett.https://bookriot.com/psychology-of-a-book-hangover/#:~:text=A%20%E2%80%9Cbook%20hangover%E2%80%9D%20is%20the,the%20atmosphere%20of%20the%20novel.

- FAQ – New York Times developer.nytimes.com https://developer.nytimes.com/faq#a1

- Overview - New York Times. developer.nytimes.com 
