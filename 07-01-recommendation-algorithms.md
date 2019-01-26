# Recommendation Algorithms

## Products come in a variety of forms

- Music
- ...
- ...
- ...

## People come in a variety of forms

- Preferences ....  
- Requirements ....

You observe the preferences and requirements.

### User-Product Relationship

- Affinity 

### Product-Product Relationship

- What kind of affinities do you find in products?

### User-User Relationship

- What kind of affinities do you find in user - user relationships?

## Business Insights

- what the user would like?
- if the user buys something, what else they problaby like to buy?
- social networks may find possible friends of you?

All these insights could be monetized.

## How could you monetize it?


... 


Data -> //// ->  Relationships



This system is a "Recommendation Algorithms"

## What Data should I send to the "Recommendation Algorithms"?


















Behaviour / Demographic / Product Attribute


## Products a user already like
- ...
- ...
- ...

What the user probably likes?

- Option 1 -> Products with similar attributes (Content Based Filtering)
- Option 2 -> Products liked by similar users (Collaborative Filtering)
- Option 3 -> Complementary products (Association Rules Learning)

## Example

Lord of the Rings

Rating

Direction 10
Cast 8
Cinematography 10
Story 9

Hobbit

Rating

Direction 9.5
Cast 8
Cinematography 9
Story 10

## Users

User A Rating LOTR 5
User B Rating LOTR 5

User A Rating Hobbit 4.5
User B Rating Hobbit 4.5


User B Rating Casablanca 4.5
??????

## Complementary Products

By genre
By use (phones and headphones)

## Similar Attributes

- Which or What attributes? -> Influence user preferences
- Which are relevant, and which are not.

## Similar Users


Lord of the Rings

Rating

Direction 10
Cast 8
Cinematography 10
Story 9

Hobbit

Rating

Direction 9.5
Cast 8
Cinematography 9
Story 10

Ratings could be points in an N-Dimensional Space

Proximity between points is a measure of similarity.

How to measure distance:
- Euclidean Distance
- Hamming Distance
- Correlation Distance

# How it works

Data -> Algorithm

Average Ratings User per product
Same dimensional Space
Calculate the Distance


# Caso de studio

-  Book crossing
-  What book the user may like.
-  Find the top N book to recommend to the user.
-  We are going to use collaborative filtering.

Thera are 2 possible solutions.

-  Nearest neighbor model
-  Latent factor analysis

## Nearest neighbor model

-  // P P P P P
-  U1 3 4 - - 4
-  U2 3 5 3 4 5
-  U3 4 2 - 5 5
-  U4 4 - 4 5 2
-  U5 1 - 4 1 2 
-  U6 3 4 - 2 5

Options to recomment P3

-  Average of ratings by "similar users"
-  Ex: U2 and U1 have similar ratings (higher weight)
-  U5 and U1 are less similar users  (lower weight)

## Distance Metrics

-  **Euclidean distance** (ruler)
-  **Correlation distance**
-  U1 1 4 3 4 2
-  U2 3 4 2 4 4
-  (grafico de puntos y promedio) (correlation x and y)
-  result [-1, 1] -> Correlation distance = 1 - Correlation
-  If correlation distance is high correlation is low and vice versa
-  **Hamming Distance** % Disagreement of 2 series of numbers (used in binary numbers)
-  U1 3 3 5 2 1
-  U2 4 5 2 2 1
-  Agree 40% Disagree 60% -> Hamming Distance is 0.6

## Finding top N Recommendations

1.  Set up the data -> function to access the relevant information
    -  ISBN -> Rating Author
    -  User -> Favorite Books
2.  Construct a rating matrix  -> Representation for collaborative filtering
    -  User ISBN RATING -> Matrix User x Products
3.  Find the K nearest neighbors
    -  U1 U2 -> Distance -> Distance between users
    -  User , K -> K nearest neighbors
4.  Find the top N recommendations -> Average ratings of K nearest neigbors
    -  Sort and pink N


## Set up the data

-  http://www2.informatik.uni-freiburg.de/~cziegler/BX/ (csv dump 3 files)
-  pandas / numpy / scipy

```python
import pandas as pd
dataFile='/Users/swethakolalapudi/Downloads/BX-CSV-Dump/BX-Book-Ratings.csv'
data=pd.read_csv(dataFile,sep=";",header=0,names=["user","isbn","rating"])

## Set up the data

data.head()


bookFile='/Users/swethakolalapudi/Downloads/BX-CSV-Dump/BX-Books.csv'
books=pd.read_csv(bookFile,sep=";",header=0,error_bad_lines=False, usecols=[0,1,2],index_col=0,names=['isbn',"title","author"])


books.head()


def bookMeta(isbn):
    title = books.at[isbn,"title"]
    author = books.at[isbn,"author"]
    return title, author
    
    
bookMeta("0671027360")

def faveBooks(user,N):
    userRatings = data[data["user"]==user]  # Filtering by user  (relevant data)
    sortedRatings = pd.DataFrame.sort_values(userRatings,['rating'],ascending=[0])[:N]  # Sort by rating in desc order pick N
    sortedRatings["title"] = sortedRatings["isbn"].apply(bookMeta)  # Apply bookMeta to ISBN column
    return sortedRatings

data = data[data["isbn"].isin(books.index)]  # Inconsistencies


faveBooks(204622,5)  # Top 5 books of that user

## Construc Rating Matrix
## User vs ISBN -> Rating per book


data.shape  # more than 1 million


usersPerISBN = data.isbn.value_counts()
usersPerISBN.head(10)

usersPerISBN.shape  # 340.000 ISBN Columns


ISBNsPerUser = data.user.value_counts()

ISBNsPerUser.shape  # 150.000 Users Rows




data = data[data["isbn"].isin(usersPerISBN[usersPerISBN>10].index)]  # ISBN read for more than 10 users

data = data[data["user"].isin(ISBNsPerUser[ISBNsPerUser>10].index)]  # ISBN users read more than 10 books




userItemRatingMatrix=pd.pivot_table(data, values='rating',
                                    index=['user'], columns=['isbn'])  # Rating Matrix (pivot)

userItemRatingMatrix.head()

userItemRatingMatrix.shape

user1 = 204622
user2 = 255489


user1Ratings = userItemRatingMatrix.transpose()[user1]  # User 1 
user1Ratings.head()


user2Ratings = userItemRatingMatrix.transpose()[user2]  # User 1 


## Compute de hamming distance

from scipy.spatial.distance import hamming 
hamming(user1Ratings,user2Ratings)  # Hamming distance


import numpy as np
# Distance by any pair of users
def distance(user1,user2):
        try:
            user1Ratings = userItemRatingMatrix.transpose()[user1]
            user2Ratings = userItemRatingMatrix.transpose()[user2]
            distance = hamming(user1Ratings,user2Ratings)
        except: 
            distance = np.NaN
        return distance 


distance(204622,10118)



user = 204622
allUsers = pd.DataFrame(userItemRatingMatrix.index)
allUsers = allUsers[allUsers.user!=user]  # Remove the actual user to recommend
allUsers.head()

allUsers["distance"] = allUsers["user"].apply(lambda x: distance(user,x))  # Apply the distance function to this new column


K = 10
KnearestUsers = allUsers.sort_values(["distance"],ascending=True)["user"][:K]  # Find the K nearest neighbors

# Make the function, sending user and number of K users
def nearestNeighbors(user,K=10):
    allUsers = pd.DataFrame(userItemRatingMatrix.index)
    allUsers = allUsers[allUsers.user!=user]
    allUsers["distance"] = allUsers["user"].apply(lambda x: distance(user,x))
    KnearestUsers = allUsers.sort_values(["distance"],ascending=True)["user"][:K]
    return KnearestUsers
    

KnearestUsers = nearestNeighbors(user)
KnearestUsers


NNRatings = userItemRatingMatrix[userItemRatingMatrix.index.isin(KnearestUsers)]  # Ratings of the Nearest Neighbors for all books
NNRatings

avgRating = NNRatings.apply(np.nanmean).dropna()  # Average rating per isbn, nanmean is applied for each column (isbn) dropna() drop books which do not have rating
avgRating.head()


booksAlreadyRead = userItemRatingMatrix.transpose()[user].dropna().index  # Get ratings of the active user, drop books without rating
booksAlreadyRead


avgRating = avgRating[~avgRating.index.isin(booksAlreadyRead)]  # Remove average of already read books

N=3
topNISBNs = avgRating.sort_values(ascending=False).index[:N]  # Sort values and pick N


pd.Series(topNISBNs).apply(bookMeta)  # Tell us title and author


# function for any user

def topN(user,N=3):
    KnearestUsers = nearestNeighbors(user)
    NNRatings = userItemRatingMatrix[userItemRatingMatrix.index.isin(KnearestUsers)]
    avgRating = NNRatings.apply(np.nanmean).dropna()
    booksAlreadyRead = userItemRatingMatrix.transpose()[user].dropna().index
    avgRating = avgRating[~avgRating.index.isin(booksAlreadyRead)]
    topNISBNs = avgRating.sort_values(ascending=False).index[:N]
    return pd.Series(topNISBNs).apply(bookMeta)
    
    
faveBooks(204813,10)

topN(204813,10)

```
















