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

<div class="cell markdown" id="risZsp2ysoDJ">

</div>

<div class="cell markdown" id="9xZnRXM7x0Cv">

# CUHK-STAT1013: Practical Assignment Part 1: Sharing Your Idea and Data

</div>

<div class="cell markdown" id="9Fy05KAkyJI0">

## The gender pay gap dataset background

**Description**:

Dataset describing the gender pay gap in Hong Kong.The gender pay gap is
the average difference between the remuneration for working men and
women.

**Excel**:\[<https://docs.google.com/spreadsheets/d/1YmdKUuoc2yQjqWK0qgac7VIeDhUAqe70/edit?usp=sharing&ouid=106015626278235736762&rtpof=true&sd=true>\]

**Sample size**: 100

</div>

<div class="cell code" execution_count="5"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="Om85mbqufqWk" outputId="241d6dd8-53b6-4e9a-c889-3199bf15c3d8">

``` python
from google.colab import drive
drive.mount('/content/drive')
```

<div class="output stream stdout">

    Mounted at /content/drive

</div>

</div>

<div class="cell code" execution_count="6"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="fhUhfjcSgIq6" outputId="75d65e9c-eb2c-41c2-cdad-d5a2e9a91010">

``` python
import pandas as pd
path='/content/drive/MyDrive/Colab Notebooks/Downloads/Stat1013 Project Dataset.xlsx'
df= pd.read_excel(path)
print(df)
```

<div class="output stream stdout">

          Name  Gender  Age   Job Types  Salary
    0      Ava  Female   42   Part-time    9000
    1     Emma  Female   29   Full-time   17000
    2    David    Male   32   Full-time   21000
    3   Sophia  Female   48   Part-time   10000
    4     Carl    Male   27   Full-time   30000
    ..     ...     ...  ...         ...     ...
    95     May  Female   46   Part-time   10000
    96    Gary    Male   23   Full-time   22000
    97  Marvin    Male   42  Freelancer   32000
    98    Mark    Male   31   Full-time   29000
    99   Pearl  Female   27   Full-time   28000

    [100 rows x 5 columns]

</div>

</div>

<div class="cell markdown" id="k85zO7zxys4H">

## Hypothesis

-   Tell us what your idea is and why you have chosen to pursue this
    idea.
    -   The gender pay gap not only reduces women's lifetime earnings
        but also hurts the whole of society by increasing gender
        inequality.
    -   I am interested in "*Do women face inequality in the Hong Kong
        gender pay gap?*"
-   What two groups you are comparing:
    -   **G1**: Average salary of males in Hong Kong ; **G2**: Average
        salary of females in Hong Kong
-   What you will be measuring (i.e., what your response variable will
    be)
    -   `Salary`
-   Is your response variable quantitative rather than categorical?
    -   `Salary` is a quantitative variable.
-   Make a prediction about what kind of difference you expect to see
    between your samples and WHY.
    -   I would expect that **G1** \> **G2** since [Workplace gender
        disparity widens in Hong
        Kong](https://hrmasia.com/workplace-gender-disparity-widens-in-hong-kong/).
-   Talk about how you will gather your data
    -   I created a questionnaire and collected responses from 50 women
        and 50 men about their job types(Full-time, Part-time, or
        Freelancer) and salaries.
-   If you had unlimited resources (time, money, staff, etc.) how would
    you collect your data?
    -   \(i\) Attempt to collect more data on salary through
        questionnaires and Interviews;
    -   \(ii\) Investigate if the provided dataset is a good random
        sampling subset of the Hong Kong population;
    -   (iii)Collect payroll documents from different people, provided
        consent is obtained

</div>

<div class="cell markdown" id="3GOdPWT03PQB">

## Prepare your dataset

</div>

<div class="cell code" execution_count="7"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:206}"
id="mUxJb4hxvpHQ" outputId="280c9fa2-6916-404c-c74a-543c297b36e6">

``` python
## load dataset from excel

import pandas as pd
path='/content/drive/MyDrive/Colab Notebooks/Downloads/Stat1013 Project Dataset.xlsx'
df= pd.read_excel(path)
df.head(5)
```

<div class="output execute_result" execution_count="7">

         Name  Gender  Age  Job Types  Salary
    0     Ava  Female   42  Part-time    9000
    1    Emma  Female   29  Full-time   17000
    2   David    Male   32  Full-time   21000
    3  Sophia  Female   48  Part-time   10000
    4    Carl    Male   27  Full-time   30000

</div>

</div>

<div class="cell markdown" id="55xAIxVa3hpQ">

-   Tell us what groups you want to compare in the dataset
    -   **G1** (salary \| gender = male) vs. **G2** (salary \| gender=
        female)

</div>

<div class="cell markdown" id="13PdL3ht3902">

-   Print first 5 records of each group, respectively.

</div>

<div class="cell code" execution_count="8"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="UNL0WXav3hLj" outputId="f17ef6bc-4418-4fe8-e466-72958fe0cf40">

``` python
## First 5 records of G1 (male)
(df[df['Gender'] == 'Male']['Salary']).head(5)
```

<div class="output execute_result" execution_count="8">

    2    21000
    4    30000
    5    25000
    6    27000
    7    15000
    Name: Salary, dtype: int64

</div>

</div>

<div class="cell code" execution_count="9"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="dhe52HVB4T1O" outputId="b452e320-4520-43fa-ce21-07d13682f1de">

``` python
## First 5 records of G2 (female)
(df[df['Gender'] == 'Female']['Salary']).head(5)
```

<div class="output execute_result" execution_count="9">

    0      9000
    1     17000
    3     10000
    9     20000
    12    12000
    Name: Salary, dtype: int64

</div>

</div>

<div class="cell code" execution_count="10"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:206}"
id="loTM_J8VyPBP" outputId="13b1a7f9-d486-4f14-e60f-aa4374a5f5c7">

``` python
## Any other data description and visualization you want to add.

df.describe(include='all').T
```

<div class="output execute_result" execution_count="10">

               count unique        top freq     mean          std     min  \
    Name         100     99       Mike    2      NaN          NaN     NaN   
    Gender       100      2     Female   50      NaN          NaN     NaN   
    Age        100.0    NaN        NaN  NaN    34.38     8.887376    20.0   
    Job Types    100      3  Full-time   66      NaN          NaN     NaN   
    Salary     100.0    NaN        NaN  NaN  23210.0  9132.354515  7000.0   

                   25%      50%      75%      max  
    Name           NaN      NaN      NaN      NaN  
    Gender         NaN      NaN      NaN      NaN  
    Age           27.0     33.5     42.0     50.0  
    Job Types      NaN      NaN      NaN      NaN  
    Salary     16500.0  23500.0  30000.0  42000.0  

</div>

</div>

<div class="cell code" execution_count="11"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:339}"
id="zEgfWXaKGvNC" outputId="7ffc3566-f916-4186-eedb-8bc79a30719e">

``` python
## Any other data description and visualization you want to add.
import matplotlib.pyplot as plt
import seaborn as sns
plt.rcParams['figure.figsize'] = [10, 5]

sns.set()
sns.stripplot(data=df, x="Salary", y="Gender")
plt.show()
```

<div class="output display_data">

![](35a687f420cfd9fb33508d948e19c7f9f3079507.png)

</div>

</div>

<div class="cell code" execution_count="13"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:339}"
id="6OU5svFljeiF" outputId="4ae31ac3-12bb-48a3-d534-99cdda5dbd07">

``` python
## Any other data description and visualization you want to add.
import matplotlib.pyplot as plt
import seaborn as sns
plt.rcParams['figure.figsize'] = [10, 5]

sns.histplot(df, x='Job Types', hue='Gender')
plt.show()
```

<div class="output display_data">

![](5c73a77f7f2c5c3f8d5af96242625d18362c41ac.png)

</div>

</div>
