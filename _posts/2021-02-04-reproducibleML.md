---
title: "Faster and reproducible ML results"
categories:
  - Blog
tags:
  - python
  - machine learning
---

Any machine learning researcher have to find an effective work-flow for fast experimentation and for reproducible results. This starts by fixing the random seeds
```python
import os
import random
import numpy as np
import torch
def fix_randseeds(seed=1234):
    try:
        os.environ['PYTHONHASHSEED'] = str(seed)
        random.seed(seed)
        np.random.seed(seed)
        torch.manual_seed(seed)
        torch.cuda.manual_seed(seed)
        torch.cuda.manual_seed_all(seed)

        torch.backends.cudnn.deterministic = True
        torch.backends.cudnn.benchmark = True
    except Exception as e:
        print(e)
        pass
```
Also, in many cases one needs to disable `numpy` threads and use parallel tools provided by the machine learning framework (e.g. `pytorch`) or use a python multiprocessing library. This could also speeds up standard machine learning libraries (`sklearn`, `lgbm`, etc.)

```python
import os
def force_single_thread():
    os.environ["OMP_NUM_THREADS"] = "1"
    os.environ["OPENBLAS_NUM_THREADS"] = "1"
    os.environ["MKL_NUM_THREADS"] = "1"
    os.environ["VECLIB_MAXIMUM_THREADS"] = "1"
    os.environ["NUMEXPR_NUM_THREADS"] = "1"
```
