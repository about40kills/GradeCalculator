# GradeCalculator

This repository contains a small Jupyter Notebook `grade_calculator.ipynb` and a sample data file `grades.csv` that computes student averages and class/subject statistics using pandas.

## Requirements

- Python 3.8+
- pandas
- numpy
- jupyterlab (or jupyter)

It's recommended to run inside a virtual environment.

## Quick setup (macOS / zsh)

```bash
# create and activate a virtual environment (optional but recommended)
python3 -m venv .venv
source .venv/bin/activate

# upgrade pip and install dependencies
pip install --upgrade pip
pip install pandas numpy jupyterlab nbconvert
```

## Run interactively (recommended)

- Open VS Code and click `grade_calculator.ipynb`, or run Jupyter Lab from the project folder:

```bash
jupyter lab
```

Open `grade_calculator.ipynb` in the browser and use Run All to execute cells. Make sure `grades.csv` is in the same folder (it is by default in this repo).

If Jupyter asks for a password and you never set one, use the token printed in the terminal when you started Jupyter (look for a URL containing `?token=...`). If you lost the terminal, run:

```bash
jupyter server list
```

This command prints running servers and tokens.

## Set or change a Jupyter password

To set a persistent password you can enter in the browser prompt:

```bash
jupyter notebook password
# or for newer versions
jupyter server password
```

Follow the interactive prompt to set a password.

## Run non-interactively (headless)

To execute the notebook and save outputs to a new notebook file:

```bash
jupyter nbconvert --to notebook --execute grade_calculator.ipynb --output grade_calculator_executed.ipynb
```

## Convert and run as a script

You can convert the notebook to a Python script and run it. Note: notebooks sometimes rely on implicit display; you may want to add explicit print() calls.

```bash
jupyter nbconvert --to script grade_calculator.ipynb
python grade_calculator.py
```

## Disable token/password for local development (insecure — only on trusted machines)

If you want to skip the token/password prompt for local development, start Jupyter with these flags:

```bash
jupyter lab --NotebookApp.token='' --NotebookApp.password=''
```

Only use that on a secure, local network or single-user machine.

## Notes specific to this notebook

- The notebook reads `grades.csv` with `pd.read_csv('grades.csv')` so run it from the repository root (same folder as the CSV).
- The notebook computes per-student averages with:

```python
grades['Average'] = grades[['Math','Science','English','History']].mean(axis=1)
```

This computes the row-wise mean across the selected subject columns.

## Troubleshooting

- If imports fail, ensure you installed packages into the environment being used by the Jupyter kernel. In VS Code, check the selected kernel.
- If you see `Permission` or `Address already in use` errors when starting Jupyter, make sure no other server is running or choose a different port: `jupyter lab --port 8889`.

---

If you'd like, I can also add a small code cell at the end of the notebook that prints the final DataFrame (`grades[['Student','Average']]`) to make script output explicit. Let me know and I will add it.
