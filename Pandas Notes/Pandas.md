```python
import pandas as pd
```

# Creating, Reading and Writing

A dataframe is like a table made of vertical columns which are lists (or series in pandas)	
```python
a = pd.Dataframe({'number1':[1,2,3],'number2':[4,5,6]},index=[a,b]) #options in Dataframe

```
A series is a vertial list
```python
b = pd.Series([1,2,3,4,5,6],index=[a,b,c,d,e,f],name="numbers") #options in Series
```

### Reading & writing
```python

# Reading
a = pd.read_csv("hyperlink",index_col=0) #by default this gives 0,1,2... but with index_col we can specify which column from our data we want to choose

# Writing
a.to_csv("Name.csv")
```

# Indexing, Selecting and Assigning

Say we have a dataframe "reviews", which has various columns like country, description,points,price etc. for a collection of wine reviews

```python
# Native accessing
reviews.country
reviews['country'] #better in case series name is "country name"

reviews['country'][0] # or reviews.country[0]
```

### Indexing in Pandas
Pandas has its own native accessor operations. loc and iloc. They are row based ie. selecting rows first. Hence both are row first, column second, opposite of how you would do selection if using native accessing

```python
# iloc
# index based acessising of rows first
reviews.iloc[0] #gives the first row of the table
reviews.iloc[:,0] #gives the first column or also reviews.iloc[:][0]

reviews.iloc[1:3,0] #from [1,3) 
```

```python
# loc
# label based selection
reviews[0,'country'] #from row 0, column entry from the one with name country

#loc is more powerful since column entry names are significant in dataframes, Eg.
reviews.loc[:, ['taster_name', 'taster_twitter_handle', 'points']]
```
NOTE:	
iloc and loc use different indexing schemes.	
iloc uses the Python stdlib indexing scheme, where the first element of the range is included and the last one excluded. So 0:10 will select entries 0,...,9. loc, meanwhile, indexes inclusively. So 0:10 will select entries 0,...,10

### Conditional Selecting
The power of DFs comes in the ability to use conditions
```python
reviews.country == 'Italy' #returns a list of countries if Italy or not according to index.

#this can be used with loc to select relevant data
reviews.loc[reviews.country == 'Italy']

# Eg.
reviews.loc[(reviews.country == 'Italy') & (reviews.points >= 90)]

reviews.loc[reviews.country.isin(['Italy', 'France'])]

reviews.loc[reviews.price.isnull()]
reviews.loc[reviews.price.notnull()]

top_oceania_wines = reviews.loc[:][(reviews.points>=95) & (reviews.country.isin(['Australia','New Zealand']))] #this gave the wrong answer when the conditions weren't in brackets
```

### Assigning Data
Pretty straightforward
```python
reviews['critic'] = 'everyone' #constant assignment

reviews['index_backwards'] = range(len(reviews), 0, -1) #assigning numbers
#can assign a list as well. series too im sure tho haven't tested yet
```
# Summary Functions and Maps
Inbuilt functions in pandas that give us information of dataframe
```python
reviews.points.describe() #gives summary of values of reviews.points depending on what datatype that series is
reviews.points.mean()
reviews.taster_name.unique() #gives all unique entries
reviews.taster_name.value_counts() #gives all unique entries with their number
```

### Maps
For mapping values of a series or dataframe to desired outputs		
does not modify main object, returns modified new object	
```python
review_points_mean = reviews.points.mean()
reviews.points.map(lambda p: p - review_points_mean) #for series

def remean_points(row):
    row.points = row.points - review_points_mean
    return row
reviews.apply(remean_points, axis='columns') #for dataframe

#faster way of remeaning points column using inbuilt maths abilities of series
review_points_mean = reviews.points.mean()
reviews.points - review_points_mean

reviews.country + " - " + reviews.region_1
```
Some nice questions:		
Q. I'm an economical wine buyer. Which wine is the "best bargain"? Create a variable bargain_wine with the title of the wine with the highest points-to-price ratio in the dataset.
```python
bargain_idx = (reviews.points / reviews.price).idxmax() #idxmax() gives the first occuring entry with max value of what idxmax() is applied on
bargain_wine = reviews.loc[bargain_idx, 'title']
```

# Grouping and sorting
Maps allow us to transform data in a DataFrame or Series one value at a time for an entire column. 	
However, often we want to group our data, and then do something specific to the group the data is in.		

### Groupwise analysis
```python
reviews.groupby('points').points.count() #replicating what .value_counts() does

reviews.groupby('points').price.min()

reviews.groupby(['country']).price.agg([len, min, max]) #agg lets us run different functions simultaneously
```
You can think of each group we generate as being a slice of our DataFrame containing only data with values that match. This DataFrame is accessible to us directly using the apply() method, and we can then manipulate the data in any way we see fit. For example, here's one way of selecting the name of the first wine reviewed from each winery in the dataset:
```python
reviews.groupby('winery').apply(lambda df: df.title.iloc[0])
```


For even more fine-grained control, you can also group by more than one column. For an example, here's how we would pick out the best wine by country and province:
```python
reviews.groupby(['country', 'province']).apply(lambda df: df.loc[df.points.idxmax()])

countries_reviewed = reviews.groupby(['country', 'province']).description.agg([len])
```
Note that this creates a multiindex data-structure
To reset it to normal dataframe 
```python
countries_reviewed.reset_index()
```

### Sorting
```python
countries_reviewed = countries_reviewed.reset_index()
countries_reviewed.sort_values(by='len') #ascending by default

countries_reviewed.sort_values(by='len', ascending=False)

#to sort index values, again with same arguments
countries_reviewed.sort_index()

#sorting multiple values at one time
countries_reviewed.sort_values(by=['country', 'len'])
```

# Data Types and Missing Values
```python
reviews.points.astype('float64') #changing dtype
```
### Missing data
```python
reviews[pd.isnull(reviews.country)] # to select NaN entries, or its companion pd.notnull()

reviews.region_2.fillna("Unknown") # to fill missing values

reviews.taster_twitter_handle.replace("@kerinokeefe", "@kerino") #replacing values
```
The replace() method is worth mentioning here because it's handy for replacing missing data which is given some kind of sentinel value in the dataset: things like "Unknown", "Undisclosed", "Invalid", and so on.








	





















