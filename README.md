# Car Fuel Efficiency
:::

::: {.cell .markdown id="aWKzgUiCrorZ"}
## Introduction

What is the relationship between the power of a car\'s engine
(\"horsepower\") and its fuel efficiency (\"mpg\")? And how does this
relationship vary by the number of cylinders (\"cylinders\") the car
has? Let\'s find out.

In this project, we\'ll explore mpg dataset, which contains one row per
car model and includes information such as the year the car was made,
the number of miles per gallon (\"M.P.G.\") it achieves, the power of
its engine (measured in \"horsepower\"), and its country of origin.
:::

::: {.cell .markdown}
![car](vertopal_8993b510fb2f4fa9b63a5b02761fa0c4/3ebe22feb3b7cbdebda1ba8d585cbec11fe31d63.jpg)
:::

::: {.cell .code execution_count="3" id="cklHmIiqrbw-"}
``` python
# Import Matplotlib and Seaborn
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
```
:::

::: {.cell .markdown id="zLyOQWBQs3so"}
## Dataset
:::

::: {.cell .code execution_count="12" id="tUOYz4XKsUrk"}
``` python
mpg = pd.read_csv('mpg.csv')
```
:::

::: {.cell .code execution_count="13" colab="{\"base_uri\":\"https://localhost:8080/\"}" id="s1vwqAN9sq_S" outputId="d6fcfcc0-2b95-4f4f-eab2-a96afe6788fe"}
``` python
print(mpg.head())
```

::: {.output .stream .stdout}
        mpg  cylinders  displacement  horsepower  weight  acceleration  \
    0  18.0          8         307.0       130.0    3504          12.0   
    1  15.0          8         350.0       165.0    3693          11.5   
    2  18.0          8         318.0       150.0    3436          11.0   
    3  16.0          8         304.0       150.0    3433          12.0   
    4  17.0          8         302.0       140.0    3449          10.5   

       model_year origin                       name  
    0          70    usa  chevrolet chevelle malibu  
    1          70    usa          buick skylark 320  
    2          70    usa         plymouth satellite  
    3          70    usa              amc rebel sst  
    4          70    usa                ford torino  
:::
:::

::: {.cell .markdown id="k-GB_7Zt1s1z"}
## Plot style
:::

::: {.cell .code execution_count="29" id="d9GZDKL61uTf"}
``` python
sns.set_style("whitegrid")
sns.set_palette("Spectral")
```
:::

::: {.cell .markdown id="v7swSrxEs56Q"}
## Horsepower vs. mpg {#horsepower-vs-mpg}
:::

::: {.cell .code execution_count="30" colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":512}" id="6ask8frTsvFD" outputId="a396e76c-d314-4ae4-8a3c-60c2f7e794d9"}
``` python
# Create scatter plot of horsepower vs. mpg
g = sns.relplot(x='horsepower', y='mpg', style='origin', data=mpg, size='cylinders', hue='cylinders')

# Add a title
g.fig.suptitle("Car Horsepower vs. mpg")

plt.show()
```

::: {.output .display_data}
![](vertopal_8993b510fb2f4fa9b63a5b02761fa0c4/2a145484c2a2c27ea41eccbd4a665f1fb47ec8a9.png)
:::
:::

::: {.cell .markdown id="hFcFQmGLtuV4"}
## Year vs. mpg {#year-vs-mpg}
:::

::: {.cell .code execution_count="31" colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":512}" id="RWbhKNPatJ4Q" outputId="504b8d4a-f47b-4411-c0fa-2d53dc314bbe"}
``` python
# Create line plot
g = sns.relplot(x='model_year', y='mpg', style="origin",
            hue="origin", data=mpg, kind='line')

# Add a title
g.fig.suptitle("Model year vs. mpg")

# Show plot
plt.show()
```

::: {.output .display_data}
![](vertopal_8993b510fb2f4fa9b63a5b02761fa0c4/dd6bb168bb5604ea4cf25413eac3818864ea0e59.png)
:::
:::

::: {.cell .markdown id="7sDRXCPvuDvT"}
## Model year vs. Horsepower {#model-year-vs-horsepower}
:::

::: {.cell .code execution_count="32" colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":601}" id="X_8kTUGetqeQ" outputId="a885b4d8-66a1-4bd9-9a1d-5fd6f505df0d"}
``` python
# Add markers and make each line have the same style
g = sns.relplot(x="model_year", y="horsepower",
            data=mpg, kind="line",
            ci=None, style="origin",
            hue="origin", markers=True, dashes=False)

# Add a title
g.fig.suptitle("Model year vs. Horsepower")

# Show plot
plt.show()
```

::: {.output .stream .stderr}
    /usr/local/lib/python3.10/dist-packages/seaborn/axisgrid.py:848: FutureWarning: 

    The `ci` parameter is deprecated. Use `errorbar=None` for the same effect.

      func(*plot_args, **plot_kwargs)
:::

::: {.output .display_data}
![](vertopal_8993b510fb2f4fa9b63a5b02761fa0c4/6dd460d52006fccb9e731588cf4316b22dae170a.png)
:::
:::

::: {.cell .code execution_count="32" id="2IsapyDbt_6M"}
``` python
```
:::
