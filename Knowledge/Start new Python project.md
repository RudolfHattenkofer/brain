```swift
pipenv install --dev --pre black
pipenv install --dev pytest

touch run_tests
chmod +x run_tests

# Add dependencies, then lock them
pipenv lock --requirements > requirements.txt
```

```swift
repos:
-   repo: https://github.com/python/black
    rev: stable
    hooks:
    - id: black
      language_version: python3.7
```

```swift
#!/bin/bash

pipenv run pytest -vv
```



