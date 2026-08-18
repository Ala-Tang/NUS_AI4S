# NumPy Easy & Medium Answer Kit — Student Guide

This kit covers **tasks 1–65 (Easy and Medium)**. Every exercise comes with a
fixed function header: you write the body, and a compiled teacher checker
compares your return value with the reference answer. Everything runs locally.

## 1. Set up the environment

You need CPython **3.11.x** and the packages pinned in this folder. The kit does
not include Python itself, so install Python 3.11 first if you do not have it.

### Option A — Conda (recommended)

If you do not have `conda` yet, follow `INSTALL_MINICONDA.md` first.

Run these commands from this folder:

```bash
conda env create -f environment.yml
conda activate ais5102
python -m ipykernel install --user --name ais5102 --display-name "Python (AIS5102)"
python -m jupyter lab
```

### Option B — Python 3.11 and venv

macOS or Linux:

```bash
python3.11 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python -m ipykernel install --user --name ais5102 --display-name "Python (AIS5102)"
python -m jupyter lab
```

Windows PowerShell:

```powershell
py -3.11 -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python -m ipykernel install --user --name ais5102 --display-name "Python (AIS5102)"
python -m jupyter lab
```

The `ipykernel install` line registers the kernel with Jupyter and is needed
only once per computer.

## 2. First run

1. Open `numpy-reference.html` in a browser. It is a static offline page; search
   exercises by number, prompt, NumPy function, or concept.
2. Open `numpy_easy_medium_compare.ipynb` in JupyterLab.
3. Select the **Python (AIS5102)** kernel.
4. Run the first cell. It should print `Checker loaded` and
   `Supported tasks: 1 to 65`.

Keep every file in this folder together — the notebook loads the checker from
beside itself.

## 3. Solving an exercise

Each exercise cell already contains the fixed header. Keep the function name and
parameters unchanged, and replace the `raise NotImplementedError(...)` line with
your NumPy logic:

```python
def q014(a, b):
    """Student solution for task 14."""
    return np.vstack((a, b))

show_result(checker.check(14, q014));
```

Rerun that cell to see the result. The checker compares the value your function
**returns**; printed text does not count. The trailing semicolon hides Jupyter's
duplicate display of the raw result dictionary.

Use the final summary cell to check all 65 functions at once.

## 4. How the checker works

For each test case, the checker runs the teacher function and your function on
separate copies of the same input, then compares the function name, signature,
return type, shape, dtype, values, and tuple structure. Floating-point results
are compared with a numerical tolerance. Variable names, comments, and
formatting inside your function are not graded.

## 5. Reading a result

| Issue | Meaning | First thing to check |
|---|---|---|
| Function name/header mismatch | The fixed `qNNN(...)` contract changed | Restore the exact header |
| Return type mismatch | Returned list/scalar/tuple/array type is wrong | Read the **Returns** contract |
| Shape mismatch | Dimensions differ from the expected result | Inspect `result.shape`, `axis`, and `reshape` |
| Dtype mismatch | A required dtype or integer/boolean kind is wrong | Inspect `result.dtype` and `astype` |
| Value mismatch | Shape/type are acceptable but values differ | Test a small input and check operation order |
| Return structure mismatch | Tuple/list length, order, or keys differ | Check the requested container structure |
| Your function raised an exception | Your code stopped with an error | Read **Details** and the **Try** suggestion |
| Required exception not raised | An invalid input must be rejected | Implement the documented validation |

`expected` is the teacher's value and `actual` is yours. Different cases cover
different shapes, dtypes, ties, NaNs, and boundary conditions.

## 6. Useful checker commands

```python
checker.describe(14)               # public prompt and contract
checker.example_inputs(14)         # a copied input case
checker.run_reference(14, *args)   # teacher behavior for supplied arguments
checker.check(14, q014)            # check one function
checker.check_all(globals())       # check every q001 through q065 found
```

## 7. Troubleshooting

- **`bad magic number`, or the checker will not import:** the kernel is not
  CPython 3.11. Select **Python (AIS5102)**.
- **`Python (AIS5102)` is missing from the kernel list:** activate the
  environment, rerun the `python -m ipykernel install` command above, then
  restart JupyterLab.
- **The checker or manifest cannot be found:** move the whole folder together,
  not just the notebook.
- **A cell still shows an old result:** rerun the cell, or use
  *Kernel → Restart Kernel and Run All Cells*.
- **A cell runs forever:** use *Kernel → Interrupt Kernel*, fix the loop, and
  rerun the cell.

## 8. Scope

- Tasks 1–35: Easy
- Tasks 36–65: Medium
- Tasks 66–100: no compiled answer is provided
