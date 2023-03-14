---
jupyter:
  colab:
  kernelspec:
    display_name: Python 3
    name: python3
  language_info:
    name: python
  nbformat: 4
  nbformat_minor: 0
---

<div class="cell markdown" id="9xZnRXM7x0Cv">

# CUHK-STAT1013: Practical Assignment Part 1: Sharing Your Idea and Data

</div>

<div class="cell markdown" id="9Fy05KAkyJI0">

## Dataset background

**Description**:

Dataset describing daily mean temperatures at the Hong Kong Observatory
in 1922 and 2022

**Hong Kong Observatory**:
<https://www.weather.gov.hk/en/cis/dailyElement.htm?ele=TEMP&y=1922> ,
<https://www.weather.gov.hk/en/cis/dailyElement.htm?ele=TEMP&y=2022>

**Sample size**: 368

**Feature documentation**:

| Feature                | Class | Shape | Dtype   |
|:-----------------------|:------|:------|:--------|
| Year                   |       |       | int64   |
| Month                  |       |       | int64   |
| Day                    |       |       | int64   |
| Date                   |       |       | object  |
| Daily Mean Temperature |       |       | float64 |

</div>

<div class="cell markdown" id="k85zO7zxys4H">

## Hypothesis

-   Tell us what your idea is and why you have chosen to pursue this
    idea.
    -   I am interested in "*Is annual mean temperature in 2022 higher
        than that in 1922 in Hong Kong?*"
    -   I am interested in how global warming affects Hong Kong
-   What two groups you are comparing:
    -   **G1**: annual mean temperature in 1922 **G2**: annual mean
        temperature in 2022
-   What you will be measuring (i.e., what your response variable will
    be)
    -   `Daily Mean Temperature`
-   Is your response variable quantitative rather than categorical?
    -   `Daily Mean Temperature(°C)` is interval data, which can be
        regarded as a quantitative variable.
-   Make a prediction about what kind of difference you expect to see
    between your samples and WHY.
    -   We'd expect that **G2** \> **G1** due to Global Warming
-   Talk about how you will gather your data
    -   From Hong Kong Observatory link:
        <https://www.weather.gov.hk/en/cis/dailyElement.htm?ele=TEMP&y=1922>
        ,
        <https://www.weather.gov.hk/en/cis/dailyElement.htm?ele=TEMP&y=2022>
    -   cluster sampling (select all daily mean temperatures within odd
        months)
    -   collect data into a spreadsheet
-   If you had unlimited resources (time, money, staff, etc.) how would
    you collect your data?
    -   collect more data on daily mean temperature
    -   investigate if the provided dataset is a good random sampling
        subset of the original population.

</div>

<div class="cell markdown" id="3GOdPWT03PQB">

## Prepare your dataset

</div>

<div class="cell code" execution_count="2"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:206}"
id="mUxJb4hxvpHQ" outputId="ab6aa4cf-2d60-49ec-fa8c-820deffdeff0">

``` python
## load dataset

import pandas as pd

df = pd.read_csv('https://docs.google.com/spreadsheets/d/e/2PACX-1vTSjUpHK-cGrLDo5JgLPAiVO7PylGavEuW-o5Nt14saLue5bhLN84ec3da7zGYFPw/pub?output=csv')
df.head(5)
```

<div class="output execute_result" execution_count="2">

       Year  Month  Day      Date  Daily Mean Temperature
    0  1922      1    1  1922/1/1                    18.8
    1  1922      1    2  1922/1/2                    16.9
    2  1922      1    3  1922/1/3                    16.9
    3  1922      1    4  1922/1/4                    16.4
    4  1922      1    5  1922/1/5                    17.4

</div>

</div>

<div class="cell markdown" id="55xAIxVa3hpQ">

-   Tell us what groups you want to compare in the dataset
    -   **G1** (daily mean temperature \| year = 1922) vs. **G2** (daily
        mean temperature \| year = 2022)

</div>

<div class="cell markdown" id="13PdL3ht3902">

-   Print first 5 records of each group, respectively.

</div>

<div class="cell code" execution_count="5"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="UNL0WXav3hLj" outputId="fa352415-3157-4cc2-ae97-a1995b362008">

``` python
## First 5 records of G1 (male)
(df[df['Year'] == 1922]['Daily Mean Temperature']).head(5)
```

<div class="output execute_result" execution_count="5">

    0    18.8
    1    16.9
    2    16.9
    3    16.4
    4    17.4
    Name: Daily Mean Temperature, dtype: float64

</div>

</div>

<div class="cell code" execution_count="6"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="dhe52HVB4T1O" outputId="58188193-0f7a-44e9-b4c0-aacb0a318264">

``` python
## First 5 records of G2 (female)
(df[df['Year'] == 2022]['Daily Mean Temperature']).head(5)
```

<div class="output execute_result" execution_count="6">

    184    17.6
    185    18.4
    186    18.3
    187    19.1
    188    20.4
    Name: Daily Mean Temperature, dtype: float64

</div>

</div>

<div class="cell code" execution_count="4"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:661}"
id="zEgfWXaKGvNC" outputId="c8867cdc-0d9d-4feb-fa03-50eeae75de0d">

``` python
## Any other data description and visualization you want to add.
import matplotlib.pyplot as plt
import seaborn as sns
plt.rcParams['figure.figsize'] = [10, 5]

sns.set()

sns.histplot(df, x='Year', y='Daily Mean Temperature')
plt.show()
sns.violinplot(data=df, x='Year',  y='Daily Mean Temperature')
plt.show()
## Open question, be flexible and no example can be provided.
```

<div class="output display_data">

![](39530118ae6591256620de914bde85ffc87a7def.png)

</div>

<div class="output display_data">

![](1ea7d8162290871d96ba5227799c1c7e71517d8b.png)

</div>

</div>
