# unbending

### Python Jupyter notebooks for reproducing results in the main text and the supplementary information.

* Main.ipynb is used for reproducing figures/results in the main text.

* SI.ipynb is used for reproducing results/figures in the supplementary information.

* common.ipynb is the auxiliary file containing shared variables and functions for both Main.ipynb and SI.ipynb. 

To use common.ipynb as a module, declare the following statement at the top of the code:

```python
import import_ipynb
from common import *
```
