# importing all the required libraries


```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from pandas import DataFrame
```

# loading all the datasets


```python
course_info = pd.read_csv("course_information.csv") #loading the dataset
course_info.head()
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
      <th>name</th>
      <th>course_id</th>
      <th>weeks</th>
      <th>hours</th>
      <th>start_date</th>
      <th>end_date</th>
      <th>type</th>
      <th>language</th>
      <th>num_threads</th>
      <th>mandatory_posts</th>
      <th>num_users</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Analyse Numérique pour Ingénieurs</td>
      <td>analysenumerique-001</td>
      <td>9</td>
      <td>5</td>
      <td>2/18/2013</td>
      <td>NaN</td>
      <td>Q</td>
      <td>FR</td>
      <td>119</td>
      <td>NaN</td>
      <td>103</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Asset Pricing</td>
      <td>assetpricing-001</td>
      <td>9</td>
      <td>12.5</td>
      <td>9/30/2013</td>
      <td>NaN</td>
      <td>Q</td>
      <td>E</td>
      <td>673</td>
      <td>NaN</td>
      <td>392</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Automata</td>
      <td>automata-002</td>
      <td>6</td>
      <td>9</td>
      <td>11/4/2013</td>
      <td>NaN</td>
      <td>Q</td>
      <td>E</td>
      <td>429</td>
      <td>NaN</td>
      <td>493</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Big Data in Education</td>
      <td>bigdata-edu-001</td>
      <td>8</td>
      <td>7</td>
      <td>10/24/2013</td>
      <td>NaN</td>
      <td>?</td>
      <td>E</td>
      <td>585</td>
      <td>NaN</td>
      <td>710</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Bioinformatics Algorithms (Part 1)</td>
      <td>bioinformatics-001</td>
      <td>12</td>
      <td>9</td>
      <td>11/4/2013</td>
      <td>1/27/2014</td>
      <td>Q</td>
      <td>E</td>
      <td>1160</td>
      <td>NaN</td>
      <td>941</td>
    </tr>
  </tbody>
</table>
</div>




```python
course_threads = pd.read_csv("course_threads.csv") #loading the dataset
course_threads.head(2)
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
      <th>thread_id</th>
      <th>course_id</th>
      <th>og_forum</th>
      <th>og_forum_id</th>
      <th>parent_forum</th>
      <th>parent_forum_id</th>
      <th>forum_chain</th>
      <th>depth</th>
      <th>num_views</th>
      <th>num_tags</th>
      <th>forum_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2</td>
      <td>analysenumerique-001</td>
      <td>Questions d'ordre technique (coursera, octave,...</td>
      <td>13</td>
      <td>Forums</td>
      <td>0.0</td>
      <td>Forums/ Questions d'ordre technique (coursera,...</td>
      <td>2</td>
      <td>277</td>
      <td>0</td>
      <td>13</td>
    </tr>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>analysenumerique-001</td>
      <td>Questions d'ordre technique (coursera, octave,...</td>
      <td>13</td>
      <td>Forums</td>
      <td>0.0</td>
      <td>Forums/ Questions d'ordre technique (coursera,...</td>
      <td>2</td>
      <td>572</td>
      <td>0</td>
      <td>13</td>
    </tr>
  </tbody>
</table>
</div>




```python
course_posts = pd.read_csv("course_posts.csv") #loading the dataset
course_posts.head(100)
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
      <th>post_id</th>
      <th>thread_id</th>
      <th>course_id</th>
      <th>parent_id</th>
      <th>order</th>
      <th>user_id</th>
      <th>user_type</th>
      <th>post_time</th>
      <th>relative_t</th>
      <th>votes</th>
      <th>num_words</th>
      <th>forum_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>3</td>
      <td>2</td>
      <td>analysenumerique-001</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>Anonymous</td>
      <td>1358942448</td>
      <td>-0.404753</td>
      <td>2</td>
      <td>23</td>
      <td>13</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4</td>
      <td>2</td>
      <td>analysenumerique-001</td>
      <td>0</td>
      <td>2</td>
      <td>3992067770</td>
      <td>Instructor</td>
      <td>1359109877</td>
      <td>-0.373994</td>
      <td>0</td>
      <td>15</td>
      <td>13</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7</td>
      <td>2</td>
      <td>analysenumerique-001</td>
      <td>0</td>
      <td>3</td>
      <td>3992067770</td>
      <td>Instructor</td>
      <td>1359129778</td>
      <td>-0.370338</td>
      <td>1</td>
      <td>9</td>
      <td>13</td>
    </tr>
    <tr>
      <th>3</th>
      <td>8</td>
      <td>2</td>
      <td>analysenumerique-001</td>
      <td>0</td>
      <td>4</td>
      <td>0</td>
      <td>Anonymous</td>
      <td>1359130161</td>
      <td>-0.370267</td>
      <td>0</td>
      <td>2</td>
      <td>13</td>
    </tr>
    <tr>
      <th>4</th>
      <td>15</td>
      <td>2</td>
      <td>analysenumerique-001</td>
      <td>0</td>
      <td>5</td>
      <td>3992067770</td>
      <td>Instructor</td>
      <td>1359214077</td>
      <td>-0.354851</td>
      <td>0</td>
      <td>31</td>
      <td>13</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>95</th>
      <td>109</td>
      <td>17</td>
      <td>analysenumerique-001</td>
      <td>0</td>
      <td>7</td>
      <td>6686165963</td>
      <td>Student</td>
      <td>1361448017</td>
      <td>0.055559</td>
      <td>0</td>
      <td>0</td>
      <td>12</td>
    </tr>
    <tr>
      <th>96</th>
      <td>110</td>
      <td>17</td>
      <td>analysenumerique-001</td>
      <td>0</td>
      <td>8</td>
      <td>6686165963</td>
      <td>Student</td>
      <td>1361448140</td>
      <td>0.055581</td>
      <td>0</td>
      <td>52</td>
      <td>12</td>
    </tr>
    <tr>
      <th>97</th>
      <td>111</td>
      <td>17</td>
      <td>analysenumerique-001</td>
      <td>0</td>
      <td>9</td>
      <td>3992067770</td>
      <td>Instructor</td>
      <td>1361456027</td>
      <td>0.057030</td>
      <td>1</td>
      <td>25</td>
      <td>12</td>
    </tr>
    <tr>
      <th>98</th>
      <td>145</td>
      <td>17</td>
      <td>analysenumerique-001</td>
      <td>0</td>
      <td>10</td>
      <td>7363974425</td>
      <td>Student</td>
      <td>1361737478</td>
      <td>0.108737</td>
      <td>0</td>
      <td>50</td>
      <td>12</td>
    </tr>
    <tr>
      <th>99</th>
      <td>74</td>
      <td>18</td>
      <td>analysenumerique-001</td>
      <td>0</td>
      <td>1</td>
      <td>4717497213</td>
      <td>Student</td>
      <td>1361034235</td>
      <td>-0.020459</td>
      <td>0</td>
      <td>42</td>
      <td>12</td>
    </tr>
  </tbody>
</table>
<p>100 rows × 12 columns</p>
</div>



# feature extraction 2

# 1. using groupby to count post_id with repect to user_type
# 2. assigning post_id count as num_messages
# 3. using groupby to count all the messages from anonymous users


```python
course_posts_groupby = course_posts.groupby('user_type')['post_id'].count().to_frame().reset_index() #grouping post_id with respect to user_type
course_posts_groupby
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
      <th>user_type</th>
      <th>post_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Anonymous</td>
      <td>70531</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Community TA</td>
      <td>17336</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Coursera Staff</td>
      <td>162</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Coursera Tech Support</td>
      <td>228</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Instructor</td>
      <td>8118</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Staff</td>
      <td>11986</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Student</td>
      <td>630713</td>
    </tr>
  </tbody>
</table>
</div>




```python
course_posts_groupby['num_messages'] = course_posts_groupby['post_id'] #assigning num_of_messages as post_id count
course_posts_groupby.drop('post_id',axis =1, inplace= True) #dropping post_id column
course_posts_groupby.loc[0].reset_index() #grouping messages count of anonymous user
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
      <th>index</th>
      <th>0</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>user_type</td>
      <td>Anonymous</td>
    </tr>
    <tr>
      <th>1</th>
      <td>num_messages</td>
      <td>70531</td>
    </tr>
  </tbody>
</table>
</div>



# feature extraction1

# 1. dropping the rows which contains 0's in user_id column
# 2. using groupby to count user_id with repect to thread_id


```python
df = course_posts.drop(course_posts[course_posts.user_id == 0].index,axis=0) #dropping columns with 0's under user_id
df
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
      <th>post_id</th>
      <th>thread_id</th>
      <th>course_id</th>
      <th>parent_id</th>
      <th>order</th>
      <th>user_id</th>
      <th>user_type</th>
      <th>post_time</th>
      <th>relative_t</th>
      <th>votes</th>
      <th>num_words</th>
      <th>forum_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>4</td>
      <td>2</td>
      <td>analysenumerique-001</td>
      <td>0</td>
      <td>2</td>
      <td>3992067770</td>
      <td>Instructor</td>
      <td>1359109877</td>
      <td>-0.373994</td>
      <td>0</td>
      <td>15</td>
      <td>13</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7</td>
      <td>2</td>
      <td>analysenumerique-001</td>
      <td>0</td>
      <td>3</td>
      <td>3992067770</td>
      <td>Instructor</td>
      <td>1359129778</td>
      <td>-0.370338</td>
      <td>1</td>
      <td>9</td>
      <td>13</td>
    </tr>
    <tr>
      <th>4</th>
      <td>15</td>
      <td>2</td>
      <td>analysenumerique-001</td>
      <td>0</td>
      <td>5</td>
      <td>3992067770</td>
      <td>Instructor</td>
      <td>1359214077</td>
      <td>-0.354851</td>
      <td>0</td>
      <td>31</td>
      <td>13</td>
    </tr>
    <tr>
      <th>5</th>
      <td>18</td>
      <td>2</td>
      <td>analysenumerique-001</td>
      <td>0</td>
      <td>6</td>
      <td>7849522082</td>
      <td>Student</td>
      <td>1359246298</td>
      <td>-0.348931</td>
      <td>0</td>
      <td>1</td>
      <td>13</td>
    </tr>
    <tr>
      <th>6</th>
      <td>4</td>
      <td>2</td>
      <td>analysenumerique-001</td>
      <td>15</td>
      <td>0</td>
      <td>8489183117</td>
      <td>Student</td>
      <td>1359259908</td>
      <td>-0.346431</td>
      <td>-1</td>
      <td>10</td>
      <td>13</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>739068</th>
      <td>4027</td>
      <td>913</td>
      <td>virology-001</td>
      <td>0</td>
      <td>3</td>
      <td>8324510655</td>
      <td>Student</td>
      <td>1383144942</td>
      <td>1.176909</td>
      <td>1</td>
      <td>86</td>
      <td>2</td>
    </tr>
    <tr>
      <th>739069</th>
      <td>1853</td>
      <td>913</td>
      <td>virology-001</td>
      <td>4027</td>
      <td>0</td>
      <td>3919391685</td>
      <td>Student</td>
      <td>1383151096</td>
      <td>1.177834</td>
      <td>1</td>
      <td>34</td>
      <td>2</td>
    </tr>
    <tr>
      <th>739070</th>
      <td>1854</td>
      <td>913</td>
      <td>virology-001</td>
      <td>4020</td>
      <td>0</td>
      <td>289235738</td>
      <td>Student</td>
      <td>1383152214</td>
      <td>1.178002</td>
      <td>0</td>
      <td>9</td>
      <td>2</td>
    </tr>
    <tr>
      <th>739072</th>
      <td>4040</td>
      <td>913</td>
      <td>virology-001</td>
      <td>0</td>
      <td>4</td>
      <td>8476531543</td>
      <td>Student</td>
      <td>1383173912</td>
      <td>1.181264</td>
      <td>2</td>
      <td>50</td>
      <td>2</td>
    </tr>
    <tr>
      <th>739073</th>
      <td>4019</td>
      <td>914</td>
      <td>virology-001</td>
      <td>0</td>
      <td>1</td>
      <td>289235738</td>
      <td>Student</td>
      <td>1383117411</td>
      <td>1.172771</td>
      <td>0</td>
      <td>71</td>
      <td>8</td>
    </tr>
  </tbody>
</table>
<p>668543 rows × 12 columns</p>
</div>




```python
#course_posts1.groupby(['id','date']).count()['dx'].unstack('id', fill_value=0).plot()
df1 = df.groupby('thread_id')['user_id'].count().to_frame().reset_index() #grouping the post_id with respect to user_type
df1
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
      <th>thread_id</th>
      <th>user_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>4682</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>3709</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>4388</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1662</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>3282</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>9283</th>
      <td>9344</td>
      <td>3</td>
    </tr>
    <tr>
      <th>9284</th>
      <td>9345</td>
      <td>1</td>
    </tr>
    <tr>
      <th>9285</th>
      <td>9346</td>
      <td>2</td>
    </tr>
    <tr>
      <th>9286</th>
      <td>9347</td>
      <td>2</td>
    </tr>
    <tr>
      <th>9287</th>
      <td>9348</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>9288 rows × 2 columns</p>
</div>



# feature extraction3

# 1. using groupby to count post_id with repect to user_type
# 2. assigning post_id count as num_messages
# 3. considering coursera staff as staff replied
# 4. assigning 0 as staff not replied and 1 as staff replied and then counting the number of times staff replied


```python
course_posts_1 = course_posts.groupby('user_type')['post_id'].count().reset_index() #grouping post_id with respect to user_type
course_posts_1['num_messages'] = course_posts_1['post_id']
#course_posts_1.drop('post_id',axis =1, inplace= True)
course_posts_1.head()



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
      <th>user_type</th>
      <th>post_id</th>
      <th>num_messages</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Anonymous</td>
      <td>70531</td>
      <td>70531</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Community TA</td>
      <td>17336</td>
      <td>17336</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Coursera Staff</td>
      <td>162</td>
      <td>162</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Coursera Tech Support</td>
      <td>228</td>
      <td>228</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Instructor</td>
      <td>8118</td>
      <td>8118</td>
    </tr>
  </tbody>
</table>
</div>




```python
#course_posts_1.loc[0]
course_posts['staff_replied'] = course_posts.user_type == 'Coursera Staff' #considering staff replied as coursera staff
course_posts.head()

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
      <th>post_id</th>
      <th>thread_id</th>
      <th>course_id</th>
      <th>parent_id</th>
      <th>order</th>
      <th>user_id</th>
      <th>user_type</th>
      <th>post_time</th>
      <th>relative_t</th>
      <th>votes</th>
      <th>num_words</th>
      <th>forum_id</th>
      <th>staff_replied</th>
      <th>Staff_Replied</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>3</td>
      <td>2</td>
      <td>analysenumerique-001</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>Anonymous</td>
      <td>1358942448</td>
      <td>-0.404753</td>
      <td>2</td>
      <td>23</td>
      <td>13</td>
      <td>False</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4</td>
      <td>2</td>
      <td>analysenumerique-001</td>
      <td>0</td>
      <td>2</td>
      <td>3992067770</td>
      <td>Instructor</td>
      <td>1359109877</td>
      <td>-0.373994</td>
      <td>0</td>
      <td>15</td>
      <td>13</td>
      <td>False</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7</td>
      <td>2</td>
      <td>analysenumerique-001</td>
      <td>0</td>
      <td>3</td>
      <td>3992067770</td>
      <td>Instructor</td>
      <td>1359129778</td>
      <td>-0.370338</td>
      <td>1</td>
      <td>9</td>
      <td>13</td>
      <td>False</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>8</td>
      <td>2</td>
      <td>analysenumerique-001</td>
      <td>0</td>
      <td>4</td>
      <td>0</td>
      <td>Anonymous</td>
      <td>1359130161</td>
      <td>-0.370267</td>
      <td>0</td>
      <td>2</td>
      <td>13</td>
      <td>False</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>15</td>
      <td>2</td>
      <td>analysenumerique-001</td>
      <td>0</td>
      <td>5</td>
      <td>3992067770</td>
      <td>Instructor</td>
      <td>1359214077</td>
      <td>-0.354851</td>
      <td>0</td>
      <td>31</td>
      <td>13</td>
      <td>False</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
course_posts.staff_replied.value_counts()
course_posts['Staff_Replied'] = 1 #assigning 1 as staff replied
```


```python
course_posts.loc[course_posts.staff_replied  ==False, 'Staff_Replied'] = 0 #assigning 0 as staff not replied
course_posts.staff_replied.value_counts().reset_index()
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
      <th>index</th>
      <th>staff_replied</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>False</td>
      <td>738912</td>
    </tr>
    <tr>
      <th>1</th>
      <td>True</td>
      <td>162</td>
    </tr>
  </tbody>
</table>
</div>


