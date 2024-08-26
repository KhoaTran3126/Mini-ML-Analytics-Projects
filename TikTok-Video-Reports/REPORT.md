# Introduction
The dataset used consist of information on various reported TikTok videos by users, with each video makes a claim or opinion, and various statistics related to each video. The primary analysis focuses on understanding:
1. What characteristics are better for separating claim-related videos from opinion-related videos?
2. Compared to each other, what kind of videos receive more scrutinies from TikTok's moderation?

## Data Cleaning
1. Removed 298 rows (1.5% of data) with missing values in all columns related to video statistics
2. Converted string-casted numerical columns to numerical type
3. Inspected for duplicates

## Result
### Betwen claim-related and opinion-related videos, very clear separations exist in numerical distributions: 
1. Claim-related videos tend to have larger values for **comments, downloads, likes, shares**, and **views**
2. Of all **banned accounts and accounts under review**, there are more users which make claims than opinions

#### Videos making claims are more popular amongst viewers AND in respect of circulation, but face GREATER scrutinies than videos expressing opinions by about 4.5X
