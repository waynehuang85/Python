## Get the unique size of a dataframe column 

df.userID.unique().size

## Get the sum of a dataframe column

df.orderAmount.sum()

## Get average order amount per user

df.orderAmount.sum() / df.userID.unique().size

