# Python Global Constraints

This repo is for constraints files that help block conflicting packages. For now it only has overshadowing file that stops installing packages:

* niquists (depends on urllib3.future, added for faster resolution of niquists)
* urllib3.future

This list will be extended by packages that depend on the urlib3.future to provide faster resolution but it will work even without them, for example issuing:

`pip install grafana-wtf<=0.19.1` 

will not install `0.19.1` but `0.18.0` that does not require `urllib3.future`

If conflict resolution cannot be solved, pip will show this error:

```bash
ERROR: Cannot install niquests because these package versions have conflicting dependencies.

The conflict is caused by:
    The user requested niquests
    The user requested (constraint) niquests<0.0.0

To fix this you could try to:
1. loosen the range of package versions you've specified
2. remove package versions to allow pip attempt to solve the dependency conflict

ERROR: ResolutionImpossible: for help visit https://pip.pypa.io/en/latest/topics/dependency-resolution/#dealing-with-dependency-conflicts
```


# Setup

## Pip

### Pip Global Config 

  Issue pip config command to set constraint globally:
  
  ```
  pip config set global.constraint "https://raw.githubusercontent.com/alkuzad/python-global-constraints/master/stop-overshadowing.txt"
  ```

### Environment variable

Export to `~/.bashrc` or `~/.zshrc`:

```bash
export PIP_CONSTRAINT="https://raw.githubusercontent.com/alkuzad/python-global-constraints/master/stop-overshadowing.txt"
```

