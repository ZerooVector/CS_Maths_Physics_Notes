#RL
# INDEX
[[Ep.1 Introduction to RL]]
[[Ep.2 Some Algo to solve RL Problem]]
[[Ep.3 Single Agent Deep RL]]

```python
import seaborn as sns
import matplotlib.pyplot as plt
sns.set_style("darkgrid")
iris = sns.load_dataset('iris')
sns.FacetGrid(iris, hue ="species", height = 5).map(plt.scatter, 'sepal_length', 'petal_length').add_legend()
plt.show()
```

```python
@html("<h1>HTML Caption</h1>")
@html('''
<svg width="100%" height="100%" viewBox="0 0 600 600" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
  <circle cx="300" cy="300" r="250" style="fill:peru;" />
  <circle cx="200" cy="250" r="50" style="fill:black;" />
  <circle cx="400" cy="250" r="50" style="fill:black;" />
  <circle cx="190" cy="230" r="20" style="fill:white;" />
  <circle cx="390" cy="230" r="20" style="fill:white;" />
  <circle cx="250" cy="400" r="85" style="fill:saddlebrown;" />
  <circle cx="350" cy="400" r="85" style="fill:saddlebrown;" />
  <ellipse cx="300" cy="380" rx="50" ry="35" style="fill:black;" />
  <ellipse cx="130" cy="100" rx="110" ry="70" style="fill:saddlebrown;"/>
<ellipse cx="470" cy="100" rx="110" ry="70" style="fill:saddlebrown;" />
</svg> 
''')
```

