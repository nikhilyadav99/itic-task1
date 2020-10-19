```python
# importing all the required packages
import pandas as pd
import numpy as np 
import matplotlib.pyplot as plt
import seaborn as sns
from pandas import DataFrame
```


```python
df = pd.read_csv("course_threads.csv") #loading the dataset
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
df1 = pd.read_csv("course_information.csv") #loading the dataset
df1.head(2)
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
  </tbody>
</table>
</div>




```python
df2 = pd.read_csv("course_posts.csv") #loading the dataset
df2.head(2)
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
  </tbody>
</table>
</div>



# Figure 1

# 1. sorting the values of num_threads in descending order
# 2. plotting the bargraph
# 3. as you can see, the graph is arranged in a descending order and there maximum number of threads in the course_id(intropsych-001)


```python
df1_sort = df1.sort_values(by = 'num_threads' , ascending = False) #sorting the values of the column in descending order
df1_sort.head(2)
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
      <th>33</th>
      <td>Introduction to Psychology</td>
      <td>intropsych-001</td>
      <td>8</td>
      <td>5</td>
      <td>5/6/2013</td>
      <td>NaN</td>
      <td>S</td>
      <td>E</td>
      <td>9300</td>
      <td>?</td>
      <td>11989</td>
    </tr>
    <tr>
      <th>58</th>
      <td>Video Games and Learning</td>
      <td>videogameslearning-001</td>
      <td>6</td>
      <td>5</td>
      <td>10/3/2013</td>
      <td>NaN</td>
      <td>E</td>
      <td>E</td>
      <td>8694</td>
      <td>NaN</td>
      <td>3415</td>
    </tr>
  </tbody>
</table>
</div>




```python
#plotting bar graph for graph 1
plt.figure(figsize=(20,5))
sns.barplot(data = df1_sort, x = 'course_id' , y = 'num_threads' , color = 'blue')
plt.xticks(rotation=90, horizontalalignment="center")
plt.title('Number of threads vs. course identifier')
plt.ylabel('Number of threads', fontsize=20)
plt.xlabel('course identifier', fontsize=20)
plt.show()
```


    
![png](output_7_0.png)
    


# Figure 3

# 1. grouping the user_type with respect to post_id
# 2. sorting the values in descending order
# 3. plotting the graph
# 4. as you can see, students have posted in the threads more than any other user_type


```python
df2_groupby = df2.groupby('user_type')['post_id'].count().to_frame().reset_index() #grouping the user_type with respect to post_id
```


```python
df2_sort = df2_groupby.sort_values(by = 'post_id' , ascending = False) #sorting the values in descending order
df2_sort
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
      <th>6</th>
      <td>Student</td>
      <td>630713</td>
    </tr>
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
      <th>5</th>
      <td>Staff</td>
      <td>11986</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Instructor</td>
      <td>8118</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Coursera Tech Support</td>
      <td>228</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Coursera Staff</td>
      <td>162</td>
    </tr>
  </tbody>
</table>
</div>




```python
#plotting bar graph for graph 3
sns.barplot(x = 'user_type' , y = 'post_id' , 
                    data = df2_sort , color = 'blue')
plt.yscale('log')
plt.xticks(rotation=90, horizontalalignment="center")
plt.xlabel('user type')
plt.ylabel('Number of messages')
```




    Text(0, 0.5, 'Number of messages')




    
![png](output_12_1.png)
    


# Figure 4

# 1. checking for posts in parent_id
# 2. using group_by to get the count of post_id with repect to the columns
# 3. replacing the column post_id with count
# 4. checking if it's a post or a comment and replacing it with the value from count
# 5. getting max values per thread_id and course_id
# 6. creating a dataframe where forum_=3,4 and merging the with earlier dataframe tmp
# 7. creating a dataframe with only three columns('forum_id', 'num_posts', 'num_comments')
# 8. Plotting the graph



```python
df2['is_post'] = df2.parent_id==0 #checking for posts in parent_id
df2['is_post']
```




    0          True
    1          True
    2          True
    3          True
    4          True
              ...  
    739069    False
    739070    False
    739071    False
    739072     True
    739073     True
    Name: is_post, Length: 739074, dtype: bool




```python
# using group_by to get the count of post_id with repect to these columns
tmp = df2.groupby(['course_id', 'thread_id', 'is_post']).count()[['post_id']].reset_index() 
tmp
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
      <th>course_id</th>
      <th>thread_id</th>
      <th>is_post</th>
      <th>post_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>analysenumerique-001</td>
      <td>2</td>
      <td>False</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>analysenumerique-001</td>
      <td>2</td>
      <td>True</td>
      <td>9</td>
    </tr>
    <tr>
      <th>2</th>
      <td>analysenumerique-001</td>
      <td>3</td>
      <td>False</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>analysenumerique-001</td>
      <td>3</td>
      <td>True</td>
      <td>16</td>
    </tr>
    <tr>
      <th>4</th>
      <td>analysenumerique-001</td>
      <td>4</td>
      <td>True</td>
      <td>2</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>136402</th>
      <td>virology-001</td>
      <td>911</td>
      <td>True</td>
      <td>5</td>
    </tr>
    <tr>
      <th>136403</th>
      <td>virology-001</td>
      <td>912</td>
      <td>True</td>
      <td>2</td>
    </tr>
    <tr>
      <th>136404</th>
      <td>virology-001</td>
      <td>913</td>
      <td>False</td>
      <td>4</td>
    </tr>
    <tr>
      <th>136405</th>
      <td>virology-001</td>
      <td>913</td>
      <td>True</td>
      <td>4</td>
    </tr>
    <tr>
      <th>136406</th>
      <td>virology-001</td>
      <td>914</td>
      <td>True</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>136407 rows × 4 columns</p>
</div>




```python
tmp['count'] = tmp['post_id'] # replacing the column post_id with count
tmp.drop('post_id', axis=1, inplace=True)
tmp.head()
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
      <th>course_id</th>
      <th>thread_id</th>
      <th>is_post</th>
      <th>count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>analysenumerique-001</td>
      <td>2</td>
      <td>False</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>analysenumerique-001</td>
      <td>2</td>
      <td>True</td>
      <td>9</td>
    </tr>
    <tr>
      <th>2</th>
      <td>analysenumerique-001</td>
      <td>3</td>
      <td>False</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>analysenumerique-001</td>
      <td>3</td>
      <td>True</td>
      <td>16</td>
    </tr>
    <tr>
      <th>4</th>
      <td>analysenumerique-001</td>
      <td>4</td>
      <td>True</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
tmp['num_posts'] = 0
tmp['num_comments'] = 0

#checking if it's a post or a comment and replacing it with the value from count
tmp.loc[tmp.is_post == True, 'num_posts'] = tmp['count']
tmp.loc[tmp.is_post==False, 'num_comments'] = tmp['count']
tmp.head()
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
      <th>course_id</th>
      <th>thread_id</th>
      <th>is_post</th>
      <th>count</th>
      <th>num_posts</th>
      <th>num_comments</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>analysenumerique-001</td>
      <td>2</td>
      <td>False</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>analysenumerique-001</td>
      <td>2</td>
      <td>True</td>
      <td>9</td>
      <td>9</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>analysenumerique-001</td>
      <td>3</td>
      <td>False</td>
      <td>3</td>
      <td>0</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>analysenumerique-001</td>
      <td>3</td>
      <td>True</td>
      <td>16</td>
      <td>16</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>analysenumerique-001</td>
      <td>4</td>
      <td>True</td>
      <td>2</td>
      <td>2</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
tmp = tmp.groupby(['course_id', 'thread_id']).max().reset_index() #getting max values per thread_id and course_id
tmp.head()
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
      <th>course_id</th>
      <th>thread_id</th>
      <th>is_post</th>
      <th>count</th>
      <th>num_posts</th>
      <th>num_comments</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>analysenumerique-001</td>
      <td>2</td>
      <td>True</td>
      <td>9</td>
      <td>9</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>analysenumerique-001</td>
      <td>3</td>
      <td>True</td>
      <td>16</td>
      <td>16</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>analysenumerique-001</td>
      <td>4</td>
      <td>True</td>
      <td>2</td>
      <td>2</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>analysenumerique-001</td>
      <td>7</td>
      <td>True</td>
      <td>3</td>
      <td>3</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>analysenumerique-001</td>
      <td>8</td>
      <td>True</td>
      <td>8</td>
      <td>8</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
#creating a dataframe where forum_=3,4 and merging the with earlier dataframe tmp
fig4_dat = df.query("forum_id == 4|forum_id==3").merge(tmp, on=['course_id', 'thread_id'])
fig4_dat.head(2)
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
      <th>is_post</th>
      <th>count</th>
      <th>num_posts</th>
      <th>num_comments</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5</td>
      <td>assetpricing-001</td>
      <td>Quizzes and Homeworks</td>
      <td>3</td>
      <td>Forums</td>
      <td>0.0</td>
      <td>Forums/ Quizzes and Homeworks</td>
      <td>2</td>
      <td>242</td>
      <td>0</td>
      <td>3</td>
      <td>True</td>
      <td>5</td>
      <td>5</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6</td>
      <td>assetpricing-001</td>
      <td>Quizzes and Homeworks</td>
      <td>3</td>
      <td>Forums</td>
      <td>0.0</td>
      <td>Forums/ Quizzes and Homeworks</td>
      <td>2</td>
      <td>122</td>
      <td>0</td>
      <td>3</td>
      <td>True</td>
      <td>4</td>
      <td>4</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
#creating a dataframe with only three columns
fig4_dat = fig4_dat[['forum_id', 'num_posts', 'num_comments']]
fig4_dat.head(2)
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
      <th>forum_id</th>
      <th>num_posts</th>
      <th>num_comments</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>3</td>
      <td>5</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>4</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
#plotting scatterplot for the graph4
sns.scatterplot(data=fig4_dat, x='num_posts', y='num_comments', hue='forum_id')

#setting limits for x and y axis

plt.xlim(0,100)
plt.ylim(0,100)

#setting labels and the title
plt.xlabel("Number of Posts")
plt.ylabel("Number of Comments")
plt.title("Scatter plot showing relationship between Number of comments and number of posts for Assignments and Study Group");
```


    
![png](output_22_0.png)
    


# Figure 2

# Figure 2a

# 1. using groupby to get the count of threads per course_id
# 2. using groupby to get the thread_size of a single thread 
# 3. merging two datasets('thread_size', 'course_id')
# 4. using groupby to get mean thread_size count per course_id
# 5. merging two datasets(thread_size_per_course_df, thread_count_df)
# 6. plotting the graph
# 7. the graph tends to have a non linear relationship between thread_size and thread_count


```python
#using groupby to get the count of threads per course_id
thread_count_df = DataFrame({'thread_count' : df.groupby( [ "course_id"] ).size()}).reset_index()
thread_count_df.head()
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
      <th>course_id</th>
      <th>thread_count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>analysenumerique-001</td>
      <td>119</td>
    </tr>
    <tr>
      <th>1</th>
      <td>assetpricing-001</td>
      <td>673</td>
    </tr>
    <tr>
      <th>2</th>
      <td>automata-002</td>
      <td>429</td>
    </tr>
    <tr>
      <th>3</th>
      <td>bigdata-edu-001</td>
      <td>585</td>
    </tr>
    <tr>
      <th>4</th>
      <td>bioinformatics-001</td>
      <td>1160</td>
    </tr>
  </tbody>
</table>
</div>




```python
#using groupby to get the thread_size of a single thread 
thread_size_df = DataFrame({'thread_size' : df.groupby( [ "thread_id"] ).size()}).reset_index()
thread_size_df.head()
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
      <th>thread_size</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>46</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>50</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>48</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>55</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>51</td>
    </tr>
  </tbody>
</table>
</div>




```python
thread_size_df_1 = pd.merge(thread_size_df, df, on='thread_id', how='inner')[['thread_size', 'course_id']] #merging two datasets
thread_size_per_course_df = thread_size_df_1.groupby(['course_id']).mean() #using groupby to get mean thread_size count per course_id
thread_size_per_course_df.head()
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
      <th>thread_size</th>
    </tr>
    <tr>
      <th>course_id</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>analysenumerique-001</th>
      <td>57.025210</td>
    </tr>
    <tr>
      <th>assetpricing-001</th>
      <td>48.829123</td>
    </tr>
    <tr>
      <th>automata-002</th>
      <td>52.655012</td>
    </tr>
    <tr>
      <th>bigdata-edu-001</th>
      <td>50.029060</td>
    </tr>
    <tr>
      <th>bioinformatics-001</th>
      <td>40.534483</td>
    </tr>
  </tbody>
</table>
</div>




```python
fig_2_a_df = pd.merge(thread_size_per_course_df, thread_count_df, on='course_id', how='inner') #merging two datasets
```


```python
#plotting scatterplot
f, ax = plt.subplots(figsize=(7, 7))
ax.set(xscale="log", yscale="log")
sns.regplot(x="thread_count", y="thread_size", data=fig_2_a_df, ax=ax, scatter_kws={"s": 100})
```




    <AxesSubplot:xlabel='thread_count', ylabel='thread_size'>




    
![png](output_30_1.png)
    


# Figure 2b

# 1. grouping the user_id with respect to course_id
# 2. naming user_id as num_users
# 3. merging two datasets(thread_size_per_course_df, user_count_df)
# 4. plotting the graph
# 5. the graph tends to have a non linear relation between num_of users and thread_size


```python
thread_size_df.head()
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
      <th>thread_size</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>46</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>50</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>48</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>55</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>51</td>
    </tr>
  </tbody>
</table>
</div>




```python
user_count_df = df2.groupby('course_id')['user_id'].count().to_frame().reset_index() #grouping the user_id with respect to course_id
user_count_df['num_users'] = user_count_df['user_id'] #naming user_id as num_users
```


```python
user_count_df.head()
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
      <th>course_id</th>
      <th>user_id</th>
      <th>num_users</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>analysenumerique-001</td>
      <td>741</td>
      <td>741</td>
    </tr>
    <tr>
      <th>1</th>
      <td>assetpricing-001</td>
      <td>3025</td>
      <td>3025</td>
    </tr>
    <tr>
      <th>2</th>
      <td>automata-002</td>
      <td>2715</td>
      <td>2715</td>
    </tr>
    <tr>
      <th>3</th>
      <td>bigdata-edu-001</td>
      <td>4210</td>
      <td>4210</td>
    </tr>
    <tr>
      <th>4</th>
      <td>bioinformatics-001</td>
      <td>9258</td>
      <td>9258</td>
    </tr>
  </tbody>
</table>
</div>




```python
fig_2_b_df = pd.merge(thread_size_per_course_df, user_count_df, on='course_id', how='inner') #merging two datasets
```


```python
#plotting scatterplot
f, ax = plt.subplots(figsize=(7, 7))
ax.set(xscale="log", yscale="log")
sns.regplot(x="num_users", y="thread_size", data=fig_2_b_df, ax=ax, scatter_kws={"s": 100})
```




    <AxesSubplot:xlabel='num_users', ylabel='thread_size'>




    
![png](output_37_1.png)
    

