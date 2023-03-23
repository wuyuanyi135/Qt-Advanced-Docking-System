1. Create Virtual environment
2. Install dependency # TODO: how to install from pyproject.toml

```
pip install "sip==6.7.7", "PyQt-builder==1.11.0", "PyQt5==5.15.9", "PyQt5-sip==12.11.1"
```

3. build wheel:

```
sip-wheel --build-dir build --pep484-pyi --jobs 8
```

# Troubleshoot

```
sip-wheel: 'C:\Qt\5.15.2\msvc2019_64\bin\qmake.exe -recursive PyQtAds.pro' failed returning 3
```

This is because the compiler (e.g., `cl.exe` is not found in path. start the terminal
using `Developer Powershell for VS 2022`)


-----

``` 
UnicodeDecodeError: 'utf-8' codec can't decode byte 0xb3 in position 14: invalid start byte
```

When backtrace the exception, we could simply hack `venv\lib\site-packages\sipbuild\project.py:550` to

```python
try:
    yield str(line, encoding=sys.stdout.encoding)
except:
    pass
```




