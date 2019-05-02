# Jupyter

## Common Issues & Troubleshooting

### ModuleNotFoundError

![](../.gitbook/assets/modulenotfounderror%20%281%29.png)

Jupyter Notebook tends to create path issues that disagree with the python path run locally. To fix this, I use the following troubleshooting methods:

#### Kernel.json

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
Available kernels:
  python3    /usr/local/share/jupyter/kernels/python3
```

Navigate to the `/kernels` directory and locate `kernel.json`

Inside:

```text
{
 "argv": ["python3", 
 "-m", 
 "IPython.kernel",
 "-f", 
 "{connection_file}"],
 "display_name": "Python 3",
 "language": "python"
}
```

Where it lists "python3" change it to your python path where the libraries are being installed. For example:

```text
{
 "argv": [
  "/usr/local/opt/python/bin/python3.7",
  "-m",
  "ipykernel_launcher",
  "-f",
  "{connection_file}"
 ],
 "display_name": "Python 3",
 "language": "python"
}
```

The python3 kernel should now be pointing at the correct directory. 

#### iPython Kernel Install

Navigate to the repository where the notebook files live and follow the recommendation in [this issue from the Jupyter Github.](https://github.com/jupyter/notebook/issues/2563)

> `ipython kernel install`

Check `kernel.json` to confirm that the path has been updated and that the path matches.

To confirm that your Jupyter notebook is running the same version of python:

In Jupyter notebook:

```text
import sys
sys.executable
'/usr/local/opt/python/bin/python3.7' # this is from kernel.json
```

In the terminal:

```text
$ python3
import sys
sys.executable
'/usr/local/opt/python/bin/python3.7'
'/Library/Frameworks/Python.framework/Versions/3.7/bin/python3'
```

Oops! If they don't match, then use the executable path from your locally installed python version to update `kernel.json`

Restart the notebook to see results. 

