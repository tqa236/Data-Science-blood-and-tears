# Python tips and tricks

* [Log to multiple files](https://stackoverflow.com/questions/11232230/logging-to-two-files-with-different-settings)

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

* Use `imageio` to read image easier

```python
import matplotlib.pylab as plt
from imageio import imread
filename = <IMAGE_PATH>
img = imread(filename)
plt.imshow(img)
```

* [Fix `pipenv` imcomptability error](https://stackoverflow.com/questions/51540404/how-to-resolve-python-package-depencencies-with-pipenv)

```
pipenv lock --pre --clear
```