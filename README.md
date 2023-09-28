# gify_plot
A simple Python package to turn your plots into gifs (Matplotlib, Seabron, Plotly)

# How to install it
`pip install gify_plot`

# Args
  ### Mandatory
  - X:list, ==> [ [x of type 1],[x of type 2],[x of type 3], ...]
  - Y:list, ==> same as X but for y elements. If only one Y el is given, then the array is updated to have the same length of X
  - plot_type:str, ==> the plot_type changes according to plot_library
  - plot_library:str, ==> plt | sns | px  (short forms for matplotlib.pyplot, seaborn and plotly.express)
  - name:str ==> the name of pngs and gif given as output,
  - plot_title:str,
  - xaxis_title:str,
  - yaxis_title:str,
  ### Optional
  - legend_labels=[], ==> if empty then progressive numbers are used for the elements in the legend. If inserted, be sure to put names in the same order of provided data
  - colors=["blue","red","green","orange","violet","yellow","black","brown","cyan"], ==> it must have at least the same length of groups provided in the provided data
  - sort_by_x=True, ==>Sorts value by xaxis (e.g. date)
  - sort_by_y=False ==>If set to True, it overrides sort_by_x

# How to use it
```
#A random df as a showcase
import numpy as np
import pandas as pd

df = pd.DataFrame({"G1_X" : np.random.randint(low=1, high=100, size=100),
                    "G2_X"  : np.random.randint(low=1,high=100, size=100),
                   "G1_Y" : np.random.randint(low=1, high=100, size=100),
                    "G2_Y"  : np.random.randint(low=1, high=100, size=100),
                     })
gify_plot(X=[df["G1_X"],df["G2_X"]],
           Y=[df["G1_Y"],df["G2_Y"]],
           plot_type="line", plot_library="plt", name="test_gif",
           plot_title="Test gif", xaxis_title="year", yaxis_title="time"
          )
```



