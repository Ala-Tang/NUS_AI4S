# Student instructions

Keep all files in this folder together.

For complete setup instructions, checker internals, feedback explanations, and
troubleshooting, start with **`STUDENT_GUIDE.md`**.

1. Open `numpy-reference.html` in a browser. It remains a static, offline page.
   Search by task number, prompt, function, or keyword, and use the concept
   filter to narrow the exercises.
2. Open `numpy_easy_medium_compare.ipynb` in Jupyter.
3. Select the **Python (AIS5102)** Kernel.
4. Run the environment/checker-loading cells at the top.
5. For each exercise, keep the provided function header unchanged and replace
   only the `raise NotImplementedError(...)` line with your NumPy logic.
6. Rerun that exercise cell to compare your output with the teacher output.
7. Use the final summary cell to check all 65 functions.

For Easy and Medium tasks, the webpage shows a fixed function starter (the
header plus an empty `return`), public input/return contract, and a copy button.
These contracts describe shapes and required dtypes without revealing answers.

The checker validates the exact function name/signature, output shape, values,
and any explicitly required dtype or semantic kind (such as a boolean mask or
integer indices). Floating-point results use numerical tolerance. If a case
fails, the Notebook classifies the issue (header, return type, shape, dtype,
value, structure, or exception), shows relevant expected/actual behavior, and
suggests a next debugging step.

The compiled checker supports only tasks 1-65. Answers for tasks 66-100 are not
included.

## Included files

- `numpy-reference.html`: static offline reference and exercises
- `numpy_easy_medium_compare.ipynb`: student workspace with fixed headers
- `numpy_easy_medium_answers.cpython-311.pyc`: trusted teacher checker
- `task_contracts.json`: public prompts and function contracts, without answers
- `STUDENT_GUIDE.md`: complete student setup and usage manual
- `INSTALL_MINICONDA.md`: how to install Miniconda if you do not have `conda`
- `environment.yml` and `requirements.txt`: reproducible environment options
- `manifest.json`: checker version and compatibility information

Python bytecode is version-specific. A `bad magic number` message means the
wrong Kernel is selected; switch to **Python (AIS5102)**.
