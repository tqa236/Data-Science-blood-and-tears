# Python tips and tricks

1. [Log to multiple files](https://stackoverflow.com/questions/11232230/logging-to-two-files-with-different-settings)

```python
import logging
formatter = logging.Formatter('%(asctime)s %(levelname)s %(message)s')


def setup_logger(name, log_file, level=logging.INFO):
    """To setup as many loggers as you want"""

    handler = logging.FileHandler(log_file)        
    handler.setFormatter(formatter)

    logger = logging.getLogger(name)
    logger.setLevel(level)
    logger.addHandler(handler)

    return logger

# first file logger
logger = setup_logger('first_logger', 'first_logfile.log')
logger.info('This is just info message')

# second file logger
super_logger = setup_logger('second_logger', 'second_logfile.log')
super_logger.error('This is an error message')

def another_method():
   # using logger defined above also works here
   logger.info('Inside method')
```

2. Use `imageio` to read image easier

```python
import matplotlib.pylab as plt
from imageio import imread
filename = <IMAGE_PATH>
img = imread(filename)
plt.imshow(img)
```

3. [Fix `pipenv` imcomptability error](https://stackoverflow.com/questions/51540404/how-to-resolve-python-package-depencencies-with-pipenv)

```
pipenv lock --pre --clear
```

4. Make isort compatible with Black

```
isort --profile=black .
```

5. Use `vars` to access class's variable 

6. Some useful commands to debug `pipenv`

[✘ Locking Failed!](https://stackoverflow.com/questions/51540404/how-to-resolve-python-package-depencencies-with-pipenv)

```
pipenv lock --pre --clear
```

[Your Pipfile requires python_version 3.9, but you are using 3.8.3](https://github.com/pypa/pipenv/issues/2482)

```
which python
pipenv install --python=/path/to/your/python
```

7. Serve static website locally

```
python -m http.server 8000
```

8. Download files on Google Colab

```python
from google.colab import files
files.download("model.h5")
```

9. It's possible to install third party extensions directly from Jupyter Lab now

10. Jupyterlab Code Formatter Error Unable to find server plugin version (Ref: https://github.com/ryantam626/jupyterlab_code_formatter/issues/193)

```
jupyter server extension enable --py jupyterlab_code_formatter
```

11. Change Kernel name (Ref: https://queirozf.com/entries/jupyter-kernels-how-to-add-change-remove)

* Use `$ jupyter kernelspec list` to see the folder the kernel is located in
* In that folder, open up file `kernel.json` and edit option "display_name"
