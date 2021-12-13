# Museum-Artists-and-Artworks-Analysis

### Analysis of data from Museum of Modern Art Collection
By Danny Lam <br>
December 9, 2021

## Assessment

1. Which artist in this data set lived the longest?
2. Who are the top 10 artists by the number of artworks?
3. Which artist created the most artwork by total surface area?
4. Did any artists have artwork acquired during their lifetime?
5. Data quality review 
6. Issues I ran into
7. What I learned

## Data

The data used in this assessment is sourced from the Mueseum of Modern Art (MoMA) on Kaggle:<br>
https://www.kaggle.com/momanyc/museum-collection <br>

There are 2 datasets:
- artists = 15,091 records and 6 columns
- artworks = 130,262 records and 21 columns

## Data Quality:
- At first glance, I could tell that the `artists` data looks easier to browse through. 
- There were lots of null values in the `Birth Year` and `Death Year` columns. 
- I made an assumption that null values in `Death Year` means that the artist is still alive. That was an error because there was an artist born in 1731 with a null `Death Year`. I had to go back and revise my cleaning to be more accurate.
- For the `artworks` data, although I did not use a lot of the columns for my analysis, there were tons of nulls for every column.
- I found out that there was an outlier date of `1216-10-18` for the `Acquisition Date` column. It was even formatted different on the csv file. 
- While I was solving Question 3, I noticed that Richard Serra's artwork ["To Lift"](https://www.moma.org/collection/works/101902) had a height of 9140 cm when it was suppose to be 91.4 cm. Good thing that data error didn't make Richard the top artist when I was doing my analysis. 
- I assume that there are tons more errors, big or small, in these datasets, and that's the reality of dirty data. 

## Problems I faced:
- The results of the oldest living artist was a company intead of a artist or person. I had to move on to the second top result since the first one was inaccurate.
- In the artworks dataset, there are many unknown artists that is labeled as `Unknown photographer` instead of being null. Because of that, it messed up my analysis. 
- I had a tough time understanding what question 3 really meant by total surface area. I say this because most measurements were null except for `Height (cm)` and `Width (cm)`. I ended up adding `Depth (cm)` to the surface area equation to be able to work with more data.
- For question 4, I ran into issues when converting the `Acquisition Date` datatype from object to datetime. I found out that there is a timestamp of `1216-10-18`, which is a clear error so. After changing the value, my code to convert the datatype format worked.
- I made the mistake of concatenating my datasets together instead of merging them. `Concat` left a lot of null values for `Birth Year` and `Death Year`, while `merge` properly joined the datasets together. This made searching for my conditions a lot easier.

## What I learned:
- I need to make sure I understand the question correctly before I even start my cleaning process and analysis.
- The quality of the data will not always be perfect, so I have to minimize as much errors as possible to maximize accuracy of results.
- Some questions took longer to prepare for, while other questions were quicker to obtain the result.
- Paying attention to the amount of non-null and null values in each column can give you a better understanding of what is going on and can help with troubleshooting.
- I learned how to join 2 datasets together using `merge` method in `pandas`, just like how SQL uses `JOIN`.
