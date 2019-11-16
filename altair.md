# Import altair
``` python
import altair as alt
#if in notebook
alt.renderers.enable("notebook")
```
# Histogram
``` python
alt.Chart(minidf).mark_bar().encode(
    x=alt.X('Brain Weight', bin=alt.Bin(maxbins=20), title="Brain Weight Binned",),
    y="count()"
).properties(
    width=200,
    height=200,
    title="Histogram of Brain Weight"
 
)
```
# Scatterplot
``` python
scattter=alt.Chart(df).mark_circle().encode(
    x="Body Weight",
    y="Brain Weight"
)
```
# Bar Chart
``` python
trends_bar=alt.Chart(trends).mark_bar().encode(
    x="search_term",
    y="sum(value)",
    color="search_term"
)
```
# Line Chart
``` python
trends_line=alt.Chart(trends).mark_line().encode(
    x=alt.X("date:T", timeUnit="yearmonth"),
    y="sum(value)",
    color="search_term"
)
```
# Map
``` python

```
# Horizontal concatenation
``` python
 trends_bar | trends_line 
 ```
 # Vertical concatenation
 ``` python 
  trends_bar & trends_line 
 ```
 # Single selection (interaction)
  ``` python
selection=alt.selection_interval(encodings=["x"])

trends_line=alt.Chart(trends).mark_line().encode(
    x=alt.X("date:T", timeUnit="yearmonth"),
    y="sum(value)",
    color="search_term"
).transform_filter(
    selectioni
)

trends_line_small=alt.Chart(trends).mark_line().encode(
    x=alt.X("date:T", timeUnit="yearmonth"),
    y="sum(value)",
    color="search_term"
).properties(
    height=50,
    selection=selection
)
 ```
 # Interval Selection(interacivo)
  ``` python 
 select_interval=alt.selection_interval(encodings=["x"])

trends_line=alt.Chart(trends).mark_line().encode(
    x=alt.X("date:T", timeUnit="yearmonth"),
    y="sum(value)",
    color="search_term"
).properties(
    selection=select_interval

)

trends_bar=alt.Chart(trends).mark_bar().encode(
    x="search_term",
    y="sum(value)",
    color="search_term"
).transform_filter(
    select_interval
) 
  ```
