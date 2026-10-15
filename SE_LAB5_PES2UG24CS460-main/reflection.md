Lab 5: Static Code Analysis — Reflection

1. What is static code analysis?
Static code analysis means checking source code without running it. The tools read the code and point out possible bugs, security problems, and style mistakes before the program is ever used.

2. What is the difference between Pylint, Bandit, and Flake8?
Pylint looks at overall code quality, like missing docstrings, bad naming, and risky practices. Bandit is focused on security and flags insecure patterns such as SQL built from strings or weak random numbers. Flake8 only checks style and formatting based on PEP 8, like line length and whitespace.

3. Which issues did you fix?
With Bandit, I fixed an SQL injection risk by switching to a parameterized query, replaced random with secrets for generating PINs, and removed a try/except/pass block that hid errors. With Pylint, I fixed the mutable default argument log=[], an inconsistent return in rentBike, a == None comparison, an unused variable, missing docstrings, and camelCase function names. With Flake8, I fixed the long lines and the trailing whitespace.

4. How did these fixes improve the program?
The program is safer now because user input can no longer change the SQL query, and the PINs are harder to guess. It is also more reliable, since errors are reported instead of ignored, and the log list is no longer shared between calls. The code is easier to read too. The final Pylint score went from 3.89/10 to 9.74/10, with no Bandit findings and no Flake8 errors.

5. What did you learn?
I learned that each tool catches different kinds of problems, so using all three gives a fuller review than any one alone. I also learned that some bugs, like the mutable default argument, are easy to miss when reading code but are flagged right away by a tool. Re-running the tools after each fix helped me confirm that the problems were really gone.

6. What are the limitations of static analysis?
Static analysis can’t catch every runtime error or logic mistake, because it never actually runs the program. While wrapping lines for Flake8, my program broke and began returning None, and Flake8 didn’t warn me about that. Only running the program showed me. So manual review and testing are still needed.