This folder contains files for the
documentation: [https://metaurban-simulator.readthedocs.io/](https://metaurban-simulator.readthedocs.io/).

To build documents locally, please run the following codes:

```bash
pip install sphinx sphinx_rtd_theme myst-nb
pip install sphinx-copybutton
rm -rf build/ && make html
# or
rm -rf build/ && sphinx-build -j 4 source build
```

add `-b linkcheck` for linkcheck. some cross-referenced link might be broken in the check result, which is expected.
This tool can only check some external links. For checking cross-reference, using tools like `linkchecker`.


### Execution some files when building doc

The doc is set to disable executing all `.ipynb`.
For enabling executing certain files and generate result when compiling the doc, set in the file metadata with:

```python
{
    "mystnb": {
        "execution_mode": "force"
    }
}
```

For more details, see: https://myst-nb.readthedocs.io/en/latest/configuration.html

### Execution some cells in a file

If you only want to execute some cells, first set in the file metadata with

```python
{
    "mystnb": {
        "execution_mode": "auto"
    }
}
```

It will auto run cells that doesn't run before. 
And you need to skip all cells you don't want to run with cell tags:

```python
{"tags": ["skip-execution"]}
```

### Preprocess-Add colab link
Everytime the `make html` is called, all `ipynb` file will have corresponding colab link in it by modifying the source
code. So you will find that your source code is modified in git. Please commit that changes as well.
