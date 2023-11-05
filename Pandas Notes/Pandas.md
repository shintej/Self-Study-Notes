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
Pandas has its own native accessor operations. loc and iloc. They are row based ie. selecting rows first. Hence both are row first, column second, opposite of normal language syntax

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
```

### Assigning Data
Pretty straightforward
```python
reviews['critic'] = 'everyone' #constant assignment

reviews['index_backwards'] = range(len(reviews), 0, -1) #assigning numbers
#can assign a list as well. series too im sure tho haven't tested yet
```









