# Jupyter

## Common Issues & Troubleshooting

### ModuleNotFoundError

![](../.gitbook/assets/modulenotfounderror%20%281%29.png)

Jupyter Notebook tends to create path issues that disagree with the python path run locally. To fix this, I use the following troubleshooting steps:

#### Check Jupyter path

In the terminal:

```text
# check Jupyter path
$ which -a jupyter
/usr/local/bin/jupyter # sample output

# check default python path
$ which -a python
/usr/bin/python

# check python3 path
$ which -a python3
/usr/local/bin/python3
```

If there is disagreement between the paths \(as shown above\), you can redirect the Jupyter kernel to point at the desired directory.

```text
# identify where Jupyter stores kernel information
$ jupyter kernselspec list
```

