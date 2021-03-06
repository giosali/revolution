# revolution

![Supported Versions](https://img.shields.io/pypi/pyversions/revolution)
![PyPI Version](https://img.shields.io/pypi/v/revolution)
![GitHub Workflow Status](https://img.shields.io/github/workflow/status/GBS3/revolution/revolution)
[![codecov](https://codecov.io/gh/GBS3/revolution/branch/main/graph/badge.svg)](https://codecov.io/gh/GBS3/revolution)
![License](https://img.shields.io/pypi/l/revolution)

<img src="https://raw.githubusercontent.com/GBS3/revolution/main/media/icon.gif?token=AQ2HXW2ZE4ML27FSUQRTLGLAOEKU6" width="200" align="right">

An assortment of spinners to use while your Python programs run.

## Installation

In order to install `revolution`, run the following in your command line:

```
pip install revolution
```

## Usage

In order to use `revolution` in your code, importing it is as simple as:

```py
from revolution import Revolution
```

### Function decorator

`revolution` can be used as a **function decorator**:

```py
import time

from revolution import Revolution

@Revolution
def do_something():
    for _ in range(10):
        time.sleep(0.1)

do_something()
```

You can also provide it a description while you wait for your task to finish:

```py
import time

from revolution import Revolution

@Revolution(desc='Just passing time...')
def do_something():
    for _ in range(10):
        time.sleep(0.1)

do_something()
```

### with statement

Another possible way to implement `revolution` is through the use of a **with** statement:

```py
import time

from revolution import Revolution

with Revolution(desc='Running through numbers') as rev:
    for _ in range(100):
        time.sleep(0.1)
        rev.update(1) 
```

You can also include a visual counter by including a total:

```py
import time

from revolution import Revolution

with Revolution(desc='Counting up to 100', total=100) as rev:
    for _ in range(100):
        time.sleep(0.1)
        rev.update(1)
```

### for loop

If you give a Revolution object a **range object** or a **list**, you can then iterate over it:

```py
import time

from revolution import Revolution

total = 0
for i in Revolution(range(100)):
    total += i
    time.sleep(0.1)

print(total)
```

### Manual

Finally, you can use `revolution` by manually controlling when to stop it:

```py
from revolution import Revolution

rev = Revolution(desc='Doing things...')
rev.start()
# ...
rev.stop()
```

## Parameters

These are the available parameters for initializing a Revolution object:

```py
Revolution(func=None, desc='', total=None, style='', color='blue', success=None, safe=True, interval=None)
```

#### `func`
<details>
<summary>More info</summary>

`func` : list or range, optional

If this is a list or range object, it will iterate over each of the elements and return them one by one.

The `func` parameter should be left blank unless you initialize a Revolution object with a range object or a list.

</details>

#### `desc`
<details>
<summary>More info</summary>

`desc` : str, optional

A string to use in place of the text that displays beside the spinner.

</details>

#### `total`
<details>
<summary>More info</summary>

`total` : int, optional

An integer that indicates the total number of expected iterations.

</details>

#### `style`
<details>
<summary>More info</summary>

`style` : str, optional

A string that indicates which spinner style to use. If style is None or if it doesn't exist, the classic style will be used.

Available options can be viewed by running `revolution --example` or `revolution -e` in your console.

</details>

#### `color`
<details>
<summary>More info</summary>

`color` : str, optional

A string that indicates which color should be used for the spinner. If a color is not provided, the color will default to 'blue'.

Available options:
    * `black`
    * `red`
    * `green`
    * `yellow`
    * `blue`
    * `violet`
    * `cyan`
    * `white`

</details>

#### `success`
<details>
<summary>More info</summary>

`success` : str, optional

A string that will be displayed beside the spinner when the spinner animation stops.

</details>

#### `safe`
<details>
<summary>More info</summary>

`safe` : bool, optional

If True (default), spinners on Windows machines will always use the 'classic' style (even if a different style is provided).

If you are using a certain spinner style and are unsure as to how it will appear on Windows machines, it is recommended that you leave `safe` set to its default value.

</details>

#### `interval`
<details>
<summary>More info</summary>

`interval` : float, optional

A float value that is used to indicate the refresh rate of the entire spinner.

</details>

## Styles

There are multiple built-in spinner styles that you can take advantage of. *However*, only the classic spinner will be used on **Windows machines** unless you set `safe=False` when you initialize a Revolution object.

### classic

```
Revolution(style='classic')
```

<img src="https://raw.githubusercontent.com/GBS3/revolution/main/media/classic.gif" width="255">

* Windows-friendly
* If a Revolution object doesn't contain a specified style, this is the style that it will default to

### dots

```
Revolution(style='dots')
```

<img src="https://raw.githubusercontent.com/GBS3/revolution/main/media/dots.gif" width="255">

* Windows-friendly

### equal

```
Revolution(style='equal')
```

<img src="https://raw.githubusercontent.com/GBS3/revolution/main/media/equal.gif" width="255">

* Windows-friendly

### braille

```
Revolution(style='braille')
```

<img src="https://raw.githubusercontent.com/GBS3/revolution/main/media/braille.gif" width="255">

### braille_long

```
Revolution(style='braille_long')
```

<img src="https://raw.githubusercontent.com/GBS3/revolution/main/media/braille_long.gif" width="255">

### braille_crawl

```
Revolution(style='braille_crawl')
```

<img src="https://raw.githubusercontent.com/GBS3/revolution/main/media/braille_crawl.gif" width="255">

### braille_bounce

```
Revolution(style='braille_bounce')
```

<img src="https://raw.githubusercontent.com/GBS3/revolution/main/media/braille_bounce.gif" width="255">

### arc

```
Revolution(style='arc')
```

<img src="https://raw.githubusercontent.com/GBS3/revolution/main/media/arc.gif" width="255">

### clear_quadrants

```
Revolution(style='clear_quadrants')
```

<img src="https://raw.githubusercontent.com/GBS3/revolution/main/media/clear_quadrants.gif" width="255">

