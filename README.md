# GitHUb_recommendation_system
the name of the project is github recommendation system
as the name suggests, here we have created a system which helps in recommending different users on github on the basis of a lot of things like mutual followings, using similar content, doing same type of works in repositories, etc

I have used python language, machine learning to run the model and I have used various algorithms to run the project

libraries used 
pandas (analyzing data)
numpy (mathematical operations)
seaborn (data visualization)
matplotlib (plot graphs)
networkx (to study large complex networks represented in form of graphs with nodes and edges)

setting up GITHUB api
access tokens (for authentication (instead of password))

using graph to store "github following" ---- first layer

adding "following of following" in same graph and connecting them with edges ----- second layer

making a directed graph too as it is imp :- "following" needs to be directed

Getting the properties of the users like : -
Degree Centrality - The number of edges it has(total connections)
In-degree Centrality - The numebr of directed edges it has(in case of directed graphs that we made earlier)
Closeness Centrality - 	reciprocal of (avg shortest dist from each vertex to each other vertex)
			lesser avg distance -> higher closeness centrality
Betweenness Centrality - the influence it has over the others edges(acting like a bridge for most edges)
Clustering co-efficient - CLUSTERS

Now we have build a dataframe using this data

replacing null values with fillNa

APPROACH 1
collaborative filtering link prediction
Using sklearn built-in modules to compute similarity metrices like cosine similarity and jaccard score

cosine similarity - measures the similarity between vector lists by calculating the cosine angle between the two vector lists
we do cosine similarity (index(basically rows) * columns)
now we take out the name of the dataframe in descencing order and print it

-----------Alternative for cosines and why we preferred cosine----------
1. euclidean distance
The cosine similarity is advantageous because even if the two similar documents are far apart by the Euclidean distance 
because of the size (like, the word 'cricket' appeared 50 times in one document and 10 times in another) they could 
still have a smaller angle between them. Smaller the angle, higher the similarity.

2. Jaccard similarity takes only unique set of words for each sentence / document while cosine 
similarity takes total length of the vectors. 

APPROACH 2
content based recommendation
get data using keywords from repositories of users
create a dataframe with these keywords
clean the data :-
1. Convert list of tags into strings for better use
2. concatenating strings separated by coma
3. converting everything to lower case
4. using stemming to reduce size of dictionary (using PorterStemmer built-in function)

APPROACHES USED FOR BUILDING FEATURES
1. Bag of words
	it just creates a set of array storing the number of times it has been used
     

2. tfidf (term frequency-inverse document frequency)
	it basically gives numerical weightage to word on the basis of its importance thus making it useful in dataframe

now we do cosine similarity between these two approaches
resulting into n*n matrix
then we sort it in descending order
we take out top 10 which will be the best recommendation
	
----------------Jaccard Similarity-----------------
Jaccard similarity takes only unique set of words for each sentence / document while cosine similarity takes total length of the vectors
