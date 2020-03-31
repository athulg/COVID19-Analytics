# COVID19-Analytics
COVID-19 Analytics performed on data-sets from CSSEGISandData/COVID-19 and Worldometer.com/coronavirus


Dependencies:
Jupyter Notebook
Python2.7

Jupyter Notebook:


import pandas as pd
import numpy as np
import requests
from datetime import datetime
import os
url = "https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv"
df = pd.read_csv(url)

df.head()

d1=df.groupby('Country/Region').sum()

d1.head()

d1["New Cases"] = ""

for i in range(len(d1)):
    d1.iloc[i,-1]=d1.iloc[i,-2]-d1.iloc[i,-3]
    
d1.head(200)

import matplotlib as plt

d1.head(10).plot(kind = 'bar', y = 'New Cases')

d1=d1.sort_values(by='New Cases', ascending=False)
d1.head()

d1.tail(10).plot(kind = 'bar', y = 'New Cases')

d1.head(10).plot(kind = 'pie', y = '3/29/20')

d1.head(10).plot(kind = 'pie',y = d1.columns[-1])



