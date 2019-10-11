
# Lambda Functions - Lab

## Introduction

In this lab, you'll get some hands-on practice creating and using lambda functions.

## Objectives
You will be able to:
* Understand what lambda functions are and why they are useful
* Use lambda functions to transform data within lists and DataFrames

## Lambda Functions


```python
import pandas as pd
df = pd.read_csv('Yelp_Reviews.csv')
df.head(2)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>business_id</th>
      <th>cool</th>
      <th>date</th>
      <th>funny</th>
      <th>review_id</th>
      <th>stars</th>
      <th>text</th>
      <th>useful</th>
      <th>user_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>pomGBqfbxcqPv14c3XH-ZQ</td>
      <td>0</td>
      <td>2012-11-13</td>
      <td>0</td>
      <td>dDl8zu1vWPdKGihJrwQbpw</td>
      <td>5</td>
      <td>I love this place! My fiance And I go here atl...</td>
      <td>0</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>jtQARsP6P-LbkyjbO1qNGg</td>
      <td>1</td>
      <td>2014-10-23</td>
      <td>1</td>
      <td>LZp4UX5zK3e-c5ZGSeo3kA</td>
      <td>1</td>
      <td>Terrible. Dry corn bread. Rib tips were all fa...</td>
      <td>3</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
    </tr>
  </tbody>
</table>
</div>



## Simple Arithmetic

Use a lambda function to create a new column called 'stars_squared' by squaring the stars column.


```python
df['stars_squared'] = df.stars.map(lambda x: x**2)
```


```python
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>business_id</th>
      <th>cool</th>
      <th>date</th>
      <th>funny</th>
      <th>review_id</th>
      <th>stars</th>
      <th>text</th>
      <th>useful</th>
      <th>user_id</th>
      <th>stars_squared</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>pomGBqfbxcqPv14c3XH-ZQ</td>
      <td>0</td>
      <td>2012-11-13</td>
      <td>0</td>
      <td>dDl8zu1vWPdKGihJrwQbpw</td>
      <td>5</td>
      <td>I love this place! My fiance And I go here atl...</td>
      <td>0</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>25</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>jtQARsP6P-LbkyjbO1qNGg</td>
      <td>1</td>
      <td>2014-10-23</td>
      <td>1</td>
      <td>LZp4UX5zK3e-c5ZGSeo3kA</td>
      <td>1</td>
      <td>Terrible. Dry corn bread. Rib tips were all fa...</td>
      <td>3</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>Ums3gaP2qM3W1XcA5r6SsQ</td>
      <td>0</td>
      <td>2014-09-05</td>
      <td>0</td>
      <td>jsDu6QEJHbwP2Blom1PLCA</td>
      <td>5</td>
      <td>Delicious healthy food. The steak is amazing. ...</td>
      <td>0</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5</td>
      <td>vgfcTvK81oD4r50NMjU2Ag</td>
      <td>0</td>
      <td>2011-02-25</td>
      <td>0</td>
      <td>pfavA0hr3nyqO61oupj-lA</td>
      <td>1</td>
      <td>This place sucks. The customer service is horr...</td>
      <td>2</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>10</td>
      <td>yFumR3CWzpfvTH2FCthvVw</td>
      <td>0</td>
      <td>2016-06-15</td>
      <td>0</td>
      <td>STiFMww2z31siPY7BWNC2g</td>
      <td>5</td>
      <td>I have been an Emerald Club member for a numbe...</td>
      <td>0</td>
      <td>TlvV-xJhmh7LCwJYXkV-cg</td>
      <td>25</td>
    </tr>
  </tbody>
</table>
</div>



## Dates
Select the month from the date string using a lambda function.


```python
df['month'] = df.date.map(lambda x: x[5:7])
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>business_id</th>
      <th>cool</th>
      <th>date</th>
      <th>funny</th>
      <th>review_id</th>
      <th>stars</th>
      <th>text</th>
      <th>useful</th>
      <th>user_id</th>
      <th>stars_squared</th>
      <th>month</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>pomGBqfbxcqPv14c3XH-ZQ</td>
      <td>0</td>
      <td>2012-11-13</td>
      <td>0</td>
      <td>dDl8zu1vWPdKGihJrwQbpw</td>
      <td>5</td>
      <td>I love this place! My fiance And I go here atl...</td>
      <td>0</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>25</td>
      <td>11</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>jtQARsP6P-LbkyjbO1qNGg</td>
      <td>1</td>
      <td>2014-10-23</td>
      <td>1</td>
      <td>LZp4UX5zK3e-c5ZGSeo3kA</td>
      <td>1</td>
      <td>Terrible. Dry corn bread. Rib tips were all fa...</td>
      <td>3</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>1</td>
      <td>10</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>Ums3gaP2qM3W1XcA5r6SsQ</td>
      <td>0</td>
      <td>2014-09-05</td>
      <td>0</td>
      <td>jsDu6QEJHbwP2Blom1PLCA</td>
      <td>5</td>
      <td>Delicious healthy food. The steak is amazing. ...</td>
      <td>0</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>25</td>
      <td>09</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5</td>
      <td>vgfcTvK81oD4r50NMjU2Ag</td>
      <td>0</td>
      <td>2011-02-25</td>
      <td>0</td>
      <td>pfavA0hr3nyqO61oupj-lA</td>
      <td>1</td>
      <td>This place sucks. The customer service is horr...</td>
      <td>2</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>1</td>
      <td>02</td>
    </tr>
    <tr>
      <th>4</th>
      <td>10</td>
      <td>yFumR3CWzpfvTH2FCthvVw</td>
      <td>0</td>
      <td>2016-06-15</td>
      <td>0</td>
      <td>STiFMww2z31siPY7BWNC2g</td>
      <td>5</td>
      <td>I have been an Emerald Club member for a numbe...</td>
      <td>0</td>
      <td>TlvV-xJhmh7LCwJYXkV-cg</td>
      <td>25</td>
      <td>06</td>
    </tr>
  </tbody>
</table>
</div>



## What is the average number of words for a yelp review?
Do this with a single line of code!


```python
average = df.text.map(lambda x: len(x.split())).mean()
average
```




    77.06551724137931



## Create a new column for the number of words in the review.


```python
df['number_words'] = df.text.map(lambda x: len(x.split()))
```


```python
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>business_id</th>
      <th>cool</th>
      <th>date</th>
      <th>funny</th>
      <th>review_id</th>
      <th>stars</th>
      <th>text</th>
      <th>useful</th>
      <th>user_id</th>
      <th>stars_squared</th>
      <th>month</th>
      <th>number_words</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>pomGBqfbxcqPv14c3XH-ZQ</td>
      <td>0</td>
      <td>2012-11-13</td>
      <td>0</td>
      <td>dDl8zu1vWPdKGihJrwQbpw</td>
      <td>5</td>
      <td>I love this place! My fiance And I go here atl...</td>
      <td>0</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>25</td>
      <td>11</td>
      <td>58</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>jtQARsP6P-LbkyjbO1qNGg</td>
      <td>1</td>
      <td>2014-10-23</td>
      <td>1</td>
      <td>LZp4UX5zK3e-c5ZGSeo3kA</td>
      <td>1</td>
      <td>Terrible. Dry corn bread. Rib tips were all fa...</td>
      <td>3</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>1</td>
      <td>10</td>
      <td>30</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>Ums3gaP2qM3W1XcA5r6SsQ</td>
      <td>0</td>
      <td>2014-09-05</td>
      <td>0</td>
      <td>jsDu6QEJHbwP2Blom1PLCA</td>
      <td>5</td>
      <td>Delicious healthy food. The steak is amazing. ...</td>
      <td>0</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>25</td>
      <td>09</td>
      <td>30</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5</td>
      <td>vgfcTvK81oD4r50NMjU2Ag</td>
      <td>0</td>
      <td>2011-02-25</td>
      <td>0</td>
      <td>pfavA0hr3nyqO61oupj-lA</td>
      <td>1</td>
      <td>This place sucks. The customer service is horr...</td>
      <td>2</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>1</td>
      <td>02</td>
      <td>82</td>
    </tr>
    <tr>
      <th>4</th>
      <td>10</td>
      <td>yFumR3CWzpfvTH2FCthvVw</td>
      <td>0</td>
      <td>2016-06-15</td>
      <td>0</td>
      <td>STiFMww2z31siPY7BWNC2g</td>
      <td>5</td>
      <td>I have been an Emerald Club member for a numbe...</td>
      <td>0</td>
      <td>TlvV-xJhmh7LCwJYXkV-cg</td>
      <td>25</td>
      <td>06</td>
      <td>32</td>
    </tr>
  </tbody>
</table>
</div>



## Rewrite the following as a lambda function. Create a new column 'Review_Length'


```python
def rewrite_as_lambda(value):
    if len(value) < 50:
        return 'Short'
    elif len(value) < 80:
        return 'Medium'
    else:
        return 'Long'
#Hint: nest your if, else conditionals

rewrite_as_lambda('help')
```




    'Short'




```python
test = lambda value: "Short" if len(value) < 50 else ("Medium" if len(value) < 80 else "Long")
test('help')
```




    'Short'



## Level Up: Dates Advanced!
<img src="images/world_map.png" width="600">  

Overwrite the date column by reordering the month and day from YYYY-MM-DD to DD-MM-YYYY. Try to do this using a lambda function.


```python
df['date2'] = df.date.map(lambda x: f'{x[8:]}-{x[5:7]}-{x[0:4]}')
```


```python
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>business_id</th>
      <th>cool</th>
      <th>date</th>
      <th>funny</th>
      <th>review_id</th>
      <th>stars</th>
      <th>text</th>
      <th>useful</th>
      <th>user_id</th>
      <th>stars_squared</th>
      <th>month</th>
      <th>number_words</th>
      <th>date2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>pomGBqfbxcqPv14c3XH-ZQ</td>
      <td>0</td>
      <td>2012-11-13</td>
      <td>0</td>
      <td>dDl8zu1vWPdKGihJrwQbpw</td>
      <td>5</td>
      <td>I love this place! My fiance And I go here atl...</td>
      <td>0</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>25</td>
      <td>11</td>
      <td>58</td>
      <td>13-11-2012</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>jtQARsP6P-LbkyjbO1qNGg</td>
      <td>1</td>
      <td>2014-10-23</td>
      <td>1</td>
      <td>LZp4UX5zK3e-c5ZGSeo3kA</td>
      <td>1</td>
      <td>Terrible. Dry corn bread. Rib tips were all fa...</td>
      <td>3</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>1</td>
      <td>10</td>
      <td>30</td>
      <td>23-10-2014</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>Ums3gaP2qM3W1XcA5r6SsQ</td>
      <td>0</td>
      <td>2014-09-05</td>
      <td>0</td>
      <td>jsDu6QEJHbwP2Blom1PLCA</td>
      <td>5</td>
      <td>Delicious healthy food. The steak is amazing. ...</td>
      <td>0</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>25</td>
      <td>09</td>
      <td>30</td>
      <td>05-09-2014</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5</td>
      <td>vgfcTvK81oD4r50NMjU2Ag</td>
      <td>0</td>
      <td>2011-02-25</td>
      <td>0</td>
      <td>pfavA0hr3nyqO61oupj-lA</td>
      <td>1</td>
      <td>This place sucks. The customer service is horr...</td>
      <td>2</td>
      <td>msQe1u7Z_XuqjGoqhB0J5g</td>
      <td>1</td>
      <td>02</td>
      <td>82</td>
      <td>25-02-2011</td>
    </tr>
    <tr>
      <th>4</th>
      <td>10</td>
      <td>yFumR3CWzpfvTH2FCthvVw</td>
      <td>0</td>
      <td>2016-06-15</td>
      <td>0</td>
      <td>STiFMww2z31siPY7BWNC2g</td>
      <td>5</td>
      <td>I have been an Emerald Club member for a numbe...</td>
      <td>0</td>
      <td>TlvV-xJhmh7LCwJYXkV-cg</td>
      <td>25</td>
      <td>06</td>
      <td>32</td>
      <td>15-06-2016</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Your code here
```

## Summary

Great! Hopefully, you're getting the hang of lambda functions now! It's important not to overuse them - it will often make more sense to define a function so that it's reusable elsewhere. But whenever you need to quickly apply some simple processing to a collection of data you have a new technique that will help you to do just that. It'll also be useful if you're reading someone else's code that happens to use lambdas.
