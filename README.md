# Twitter Database Schema Design:🪢
# Assignment_01: 📜
<img src = "https://github.com/Ritikkumar992/twitterSchemaDesign/assets/75531808/ac28003f-cb47-4664-93f2-9625085020bf" width = "900px">

## Requirements:🕶️
1. Users can register with their name, email and phone number.
2. Users can tweet any textual content
3. Users can like another user’s tweet
4. Users can retweet another user’s tweet
5. Users can comment on another user’s Tweet(Comments are not separate entities in Twitter, when you click comment button on any tweet it will be posted as tweet only, check this once on Twitter platform).
6. Users can follow other users.

 <br/>
 
## 2. Tables and Attributes:🔆

### Users Table:
- **Columns**:
  - `id`: Primary key, auto-incrementing integer
  - `fullName`: User's full name.
  - `email`: Unique email address of the user
  - `phoneNumber`: Unique phone number of the user
  - `createdAt`: Timestamp indicating user registration date

### Tweets Table:
- **Columns**:
  - `tweetID`: Primary key, auto-incrementing integer
  - `userID`: Foreign key referencing the `id` column in the `Users` table
  - `parentTweetID`: References the `tweetID` of the parent tweet (if any)
  - `commentID`: Identifier for tweet comments
  - `content`: Text content of the tweet
  - `commentedContent`: Text content of the commented tweet (if applicable)
  - `tweetAt`: Timestamp indicating tweet creation date

### Follows Table:
- **Columns**:
  - `followID`: Primary key, auto-incrementing integer
  - `followerUserID`: Foreign key referencing the `id` column in the `Users` table for the follower
  - `followedUserID`: Foreign key referencing the `id` column in the `Users` table for the followed user
  - `followedAt`: Timestamp indicating when the follow relationship was established

### Retweets Table:
- **Columns**:
  - `retweetID`: Primary key, auto-incrementing integer
  - `userID`: Foreign key referencing the `id` column in the `Users` table for the user who retweeted
  - `parentTweetID`: Foreign key referencing the `tweetID` column in the `Tweets` table for the original tweet
  - `retweetedAt`: Timestamp indicating when the retweet occurred

<br/>

### Likes Table:
- **Columns**:
  - `likeID`: Primary key, auto-incrementing integer
  - `userID`: Foreign key referencing the `id` column in the `Users` table for the user who liked
  - `tweetID`: Foreign key referencing the `tweetID` column in the `Tweets` table for the liked tweet
  - `retweetID`: Foreign key referencing the `retweetID` column in the `Retweets` table for the liked retweet
  - `likedAt`: Timestamp indicating when the like was registered
