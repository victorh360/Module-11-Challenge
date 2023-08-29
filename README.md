# Module-11-Challenge

## Overview

In Module 11 we have now moved on to scraping data from websites. There are two parts to this challenge, we were provided a starter file for each one.

In the part 1 we are tasked with scraping text from a Mars News website. For part 2 we were to scrape a Mars weather data stored in a table on a website. We then were to create visuals for the data.

## Contents

- data- Directory containing csv data we generated in the Mars Weather notebook.
- part_1_mars_news.ipynb - Notebook used to scrape title and preview text data.
- part_2_mars_weather.ipynb - Notebook used to scrape Mars weather data and create visuals. 

## Resources

- Used https://medium.com/geekculture/web-scraping-tables-in-python-using-beautiful-soup-8bbc31c5803e for syntax used to scrape weather table data.

```
data = []

for row in table:
    columns = row.find_all("td")
    
    if(columns != []):
          
        id = columns[0].text.strip()
        date = columns[1].text.strip()
        sol = columns[2].text.strip()
        ls = columns[3].text.strip()
        month = columns[4].text.strip()
        min_temp = columns[5].text.strip()
        pressure = columns[6].text.strip()
    
        rows = {"id": id,
                "terrestrial_date": date,
                "sol": sol,
                "ls": ls,
                "month": month,
                "min_temp": min_temp,
                "pressure": pressure}
    
        data.append(rows)
```
- Used https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.astype.html and https://pandas.pydata.org/docs/reference/api/pandas.to_datetime.html#pandas.to_datetime for syntax used to change dataframe data types.

```
df.terrestrial_date  = pd.to_datetime(df.terrestrial_date)
df.sol = df.sol.astype("int")
df.ls = df.ls.astype("int")
df.month = df.month.astype("int")
df.min_temp = df.min_temp.astype("float")
df.pressure = df.pressure.astype("float")
```


## Notes

- The provided notebooks had the titles as Module 12 Challenge, corrected to Module 11.

- Kept getting an error on part 2 when trying to set a y label on the final visual. Did some research and found suggestions to import matplotlib again seperate from matplotlib.pyplot. Fixed the error by importing matplotlib again.

```
from splinter import Browser
from bs4 import BeautifulSoup as soup
import matplotlib.pyplot as plt
import matplotlib
import pandas as pd

```



