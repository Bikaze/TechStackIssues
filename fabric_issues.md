##Issue 1

I had this when deploying my website using Fabric 1.14.post1 on Ubuntu 24.04 LTS:

```
Traceback (most recent call last):
  File "/home/bkz/.local/bin/fab", line 5, in <module>
    from fabric.main import main
  File "/home/bkz/.local/share/pipx/venvs/fabric3/lib/python3.12/site-packages/fabric/main.py", line 12, in <module>
    from collections import Mapping
ImportError: cannot import name 'Mapping' from 'collections' (/usr/lib/python3.12/collections/__init__.py)
```

This is what I got from perplexity.ai:

![solution from perplexity](images/fabric1.png)

In summary:

To resolve that issues I opened this file in the fabric package at:

```
/home/bkz/.local/share/pipx/venvs/fabric3/lib/python3.12/site-packages/fabric/main.py
```
the line: ```from collections import Mapping``` was causing problems.
as suggested by the AI :), I added ".abc" and the line became: ```from collections.abc import Mapping```. And, that was it.
