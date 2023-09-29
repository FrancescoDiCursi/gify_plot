# gify_plot
A simple Python package to turn your plots into gifs (Matplotlib, Seabron, Plotly).

# How to install it
`pip install gify_plot`

# Args
  ### Mandatory
  - **original_df**:pd.DataFrame ==> a dataset containing at least three columns:
    - xaxis_title (i.e., a list of int or float; dates will be added in future, use only year for now; a range >= 20 years is suggested)
    - yaxis_title (i.e., a list of int or float )
    - category (i.e., categorical variables, n groups <=7 suggested)
  - **plot_type**:str ==> The plot_type changes according to plot_library
  - **plot_library**:str ==> plt | sns | px  (short forms for matplotlib.pyplot, seaborn and plotly.express)
  - **name**:str ==> The name of pngs and gif given as output,
  - **plot_title**:str 
  - **xaxis_title**:str ==> The name of the column with x values
  - **yaxis_title**:str ==> The name of the column with y values
  ### Optional
  - **colors** = ["blue","red","green","orange","violet","yellow","black","brown","cyan"] ==> it must have at least the same length of groups provided in the data
  - **duration** = 100 ==> The delay in skipping to the next frame in ms
  - **loop** = 0
  - **save_frames** = True ==> If False, delete all png files that have been used to create the gif

# How to use it
```
# WARNING:

# Using more than 5/7 categories ends with a cluttered result.
# The fewer, the better.

# The following csv can be freely downlaoded at https://www.kaggle.com/datasets/sazidthe1/world-gdp-data?select=gdp_data.csv

df=pd.read_csv("gdp_data.csv")
temp_df=df[(df["country_name"].isin(["Italy","Spain"]))]
gify_plot(temp_df,
           plot_type="line", plot_library="plt", name="test_gif",
           plot_title="GDP per country", xaxis_title="year", yaxis_title="value", category="country_code",
           save_frames=False
          )
```

**OUTPUT**: It ouputs a list of png in the dedicated folder, along with the resulting gif.

# Supported libraries and plots:
- **plt** (i.e., matplotlib.pyplot):
  - line
  - bar
  - scatter
  - stackplot (no legend)
- **sns** (i.e., seaborn):
  - lineplot
  - scatterplot
  - barplot
- **px** (i.e., plotly.express):
  - line
  - scatter
  - area
  - bar
