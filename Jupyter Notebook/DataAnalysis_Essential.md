## Get the unique size of a dataframe column 

df.userID.unique().size

## Get the sum of a dataframe column

df.orderAmount.sum()

## Get average order amount per user

df.orderAmount.sum() / df.userID.unique().size


## userID in format of String+Number , ie "user-234188", "user-256234", "vstr-234188"
df['userid'] = df['userID'].str[0:4]
df['userid'].unique()
=> ['user', 'vstr']

df['userID' = df['userID'.str[5:0]
df['userID'].unique()
=> ['234188', '256234']

//use hash to covert the userID into unique numbers if there are non-unique values

## repeated buyer percentage
### get pivot-table or order count by userID over months
pivoted_counts = df.pivot_table(index='userID', columns='months', values='orderTime', aggfunc='count').fillna(0)
pivoted_counts.head()

### any user who placed more than one order in a month, is deemed as repeated buyer
#### if > 1, then mark 0, if = 1, then mark 0, if = 0, then mark NaN for repeatedBuy
import numpy as np
pcRepeatBuy = pivoted_counts.applymap(lambda x: 1 if x>1 else np.NaN if x==0 else 0)
pcRepeatedBuy.head()
(pcRepeatBuy.sum()/pcRepeatBuy.count()).plot(figsize=(20,9))
