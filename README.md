Liquet fork of `pydantic` - it includes:
- Early adoption of `__dataclas_transform__` typings of `ModelMetaClass`
  - https://github.com/samuelcolvin/pydantic/pull/2721
  - https://github.com/microsoft/pyright/blob/main/specs/dataclass_transforms.md
  - https://github.com/microsoft/pyright/discussions/1782
- Support for using `pyproject.toml` to configure `pydantic-mypy`
  - https://github.com/samuelcolvin/pydantic/pull/2908
- Patched schema generation when `allow_population_by_field_name` is set to `True`
  - https://github.com/samuelcolvin/pydantic/pull/3005
  - https://github.com/samuelcolvin/pydantic/issues/3004
  - https://github.com/tiangolo/fastapi/issues/3559

---

# pydantic

[![CI](https://github.com/pydantic/pydantic/workflows/CI/badge.svg?event=push)](https://github.com/pydantic/pydantic/actions?query=event%3Apush+branch%3Amain+workflow%3ACI)
[![Coverage](https://coverage-badge.samuelcolvin.workers.dev/pydantic/pydantic.svg)](https://coverage-badge.samuelcolvin.workers.dev/redirect/pydantic/pydantic)
[![pypi](https://img.shields.io/pypi/v/pydantic.svg)](https://pypi.python.org/pypi/pydantic)
[![CondaForge](https://img.shields.io/conda/v/conda-forge/pydantic.svg)](https://anaconda.org/conda-forge/pydantic)
[![downloads](https://pepy.tech/badge/pydantic/month)](https://pepy.tech/project/pydantic)
[![versions](https://img.shields.io/pypi/pyversions/pydantic.svg)](https://github.com/pydantic/pydantic)
[![license](https://img.shields.io/github/license/pydantic/pydantic.svg)](https://github.com/pydantic/pydantic/blob/main/LICENSE)

Data validation using Python type hints.

---

## Notice

**This branch relates to development of pydantic V2 which is not yet ready for release.**

If you're a user of pydantic, you probably want either
[pydantic V1.10 Documentation](https://docs.pydantic.dev/) or,
[`1.10.X-fixes` git branch](https://github.com/pydantic/pydantic/tree/1.10.X-fixes).

---

Fast and extensible, *pydantic* plays nicely with your linters/IDE/brain.
Define how data should be in pure, canonical Python 3.7+; validate it with *pydantic*.

## Help

See [documentation](https://docs.pydantic.dev/) for more details.

## Installation

Install using `pip install -U pydantic` or `conda install pydantic -c conda-forge`.
For more installation options to make *pydantic* even faster,
see the [Install](https://docs.pydantic.dev/install/) section in the documentation.

## A Simple Example

```py
from datetime import datetime
from typing import List, Optional
from pydantic import BaseModel

class User(BaseModel):
    id: int
    name = 'John Doe'
    signup_ts: Optional[datetime] = None
    friends: List[int] = []

external_data = {'id': '123', 'signup_ts': '2017-06-01 12:22', 'friends': [1, '2', b'3']}
user = User(**external_data)
print(user)
#> User id=123 name='John Doe' signup_ts=datetime.datetime(2017, 6, 1, 12, 22) friends=[1, 2, 3]
print(user.id)
#> 123
```

## Contributing

For guidance on setting up a development environment and how to make a
contribution to *pydantic*, see
[Contributing to Pydantic](https://docs.pydantic.dev/contributing/).

## Reporting a Security Vulnerability

See our [security policy](https://github.com/pydantic/pydantic/security/policy).
