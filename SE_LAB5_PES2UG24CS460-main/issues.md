# Issues Found and Fixed

| Issue | Type | Line(s) | Description | Fix Approach |
|---|---|---|---|---|
| SQL injection (B608) | Security (Medium) | 9 | Query built by joining strings with user input | Use a parameterized query with `?` placeholders |
| Weak random PIN (B311) | Security (Low) | 22 | `random` is not secure for PINs | Use `secrets.randbelow()` |
| try/except/pass (B110) | Security (Low) | 34-35 | Errors silently ignored | Catch `sqlite3.Error` and print a message |
| Mutable default argument (W0102) | Bug | 8 | `log=[]` is shared between calls | Default to `None`, create the list inside the function |
| Inconsistent return (R1710) | Bug | 14-18 | `rentBike` returned `True` or `None` | Added `return False` |
| `== None` (C0121 / E711) | Style | 40 | Wrong None check, and it crashed if the station didn't exist | Use `is None` and check the row first |
| Unused variable (W0612 / F841) | Quality | 27 | `summary` was never used | Deleted it |
| Missing docstrings, camelCase names (C0114, C0116, C0103) | Style | many | Not PEP 8 | Added docstrings, renamed to snake_case |
| Long lines, trailing whitespace (E501, W291) | Style | 5, 9, 15, 17, 26, 27, 33, 39 | Over 79 characters | Wrapped the lines |

## Results
| Tool | Before | After |
|---|---|---|
| Pylint | 3.89/10 | 9.74/10 |
| Bandit | 1 Medium, 2 Low | 0 issues |
| Flake8 | 10+ errors | 0 errors |