# M02 Sprint Project

> [!NOTE]
> You have 60 minutes to clean a catastrophic CSV into tidy format while maintaining granular Git history. Then present your approach and results to the class.
>

## The Challenge

We'll use synthetic datasets in `./data` folder. Your tasks are:

1. Create a figure showing the data in `./data/1d-data.csv`. This dataset consists of the effect of a treatment for 10 subjects. Make sure to label your axes and create a non-misleading data. You can choose any appropriate visualization method (e.g., line plot, bar plot, etc.).
2. Create a figure showing the data in `./data/2d-data.csv`. This dataset consists 2D measurements of samples. You may choose any appropriate visualization method (e.g., heatmap, contour plot, surface plot, etc.). Make sure to label your axes and create a non-misleading data.
3. Create a figure showing the data in `./data/1d-multi-method-data.csv`. This dataset consists of measurements (i.e., "AUC-ROC") of samples using multiple methods. Your goal is to highlight "Proposed" against "Baseline 1" and "Baseline 2", .... "Baseline 9" by using preattentive visual encoding. Make sure to (1) label your axes, (2) create a non-misleading visualizaation, and (3) highlight "Proposed" effectively.

Make atomic commits for each step (you can make multiple commits per step, which is encouraged).

## Git Branching Workflow

You must use git branches to organize your work. Each dataset requires three sequential branches:

### Branch Structure

For each dataset (1d-data, 2d-data, 1d-multi-method), create three branches:

**Branch 1: `<dataset>-notes`**
- Document your understanding of the dataset
- Create a markdown file (e.g., `notes-1d-data.md`) describing the data structure, key observations, and visualization strategy
- Commit and push the notes file

**Branch 2: `<dataset>-format`**
- Branch from `<dataset>-notes` after merging to master
- Load and inspect the data
- Clean or transform the data if needed
- Save formatted data or create data loading functions
- Commit each formatting decision separately
- Push your work

**Branch 3: `<dataset>-viz`**
- Branch from `<dataset>-format` after merging to master
- Create the visualization code
- Generate the final figure
- Save figure to `./paper/figs/`
- Commit visualization code and output
- Push your work

### Example Workflow for 1d-data.csv

```bash
# Start with notes branch
git checkout -b 1d-data-notes
# [Write your notes file]
git add notes-1d-data.md
git commit -m "Add analysis notes for 1d treatment data"
git push -u origin 1d-data-notes
git checkout master
git merge 1d-data-notes
git push

# Continue with formatting branch
git checkout -b 1d-data-format
# [Write data loading/formatting code]
git add notebooks/format_1d_data.ipynb
git commit -m "Load and validate 1d treatment data structure"
git commit -m "Verify treatment groups and subject IDs"
git push -u origin 1d-data-format
git checkout master
git merge 1d-data-format
git push

# Finish with visualization branch
git checkout -b 1d-data-viz
# [Create visualization]
git add notebooks/viz_1d_data.ipynb
git commit -m "Create bar plot comparing treatment effects"
git add paper/figs/1d-treatment-effects.png
git commit -m "Generate final 1d treatment figure"
git push -u origin 1d-data-viz
git checkout master
git merge 1d-data-viz
git push
```

### Complete Branch List

You should create and merge these nine branches in order:

1. `1d-data-notes` → `1d-data-format` → `1d-data-viz`
2. `2d-data-notes` → `2d-data-format` → `2d-data-viz`
3. `1d-multi-method-notes` → `1d-multi-method-format` → `1d-multi-method-viz`

## The Rules

- **Time:** 60 minutes of work, followed by presentations.
- **Version Control:** Every change must be committed and pushed. No batch commits. Your commit messages must explain why you made each change.
- **Branching:** You must follow the branching workflow described above. Each dataset requires three branches (notes, format, viz). Merge each branch to master before starting the next.
- **Requirements:** Visualizations must be clear and non-misleading. Notes files must document your thinking. Code must be well-organized.

## Evaluation

Judges evaluate four dimensions:

**Visualization Quality (25%):** Are the visualizations clear, non-misleading, and effective?
**Git Branching Workflow (25%):** Did you create and merge the required branches? Are branches named correctly and merged in the right order?
**Git History (20%):** Do commits tell a story? Are they atomic and well-described?
**Documentation (30%):** Can you clearly explain your visualization strategy and key decisions in your notes files?

## Submission

Submit the link to your GitHub repository to Brightspace. 

## Set up

Install [uv](https://docs.astral.sh/uv/getting-started/installation/). And then create a virtual environment using:

Open `pyproject.toml` in a text editor and change the project name and add your project dependencies.

If you want to install a Python package, run:

```bash 
uv add <package-name>
```

If you need to install non-Python dependencies, you can use conda or mamba as described below.

#### Miniforge

Install miniforge [GitHub - conda-forge/miniforge: A conda-forge distribution.](https://github.com/conda-forge/miniforge).

First create a virtual environment for the project.

    mamba create -n project_env_name python=3.7
    mamba activate project_env_name

Install `ipykernel` for Jupyter. 

    mamba install -y -c bioconda -c conda-forge ipykernel numpy pandas scipy matplotlib seaborn tqdm

Create a kernel for the virtual environment that you can use in Jupyter lab/notebook.

    python -m ipykernel install --user --name project_env_kernel_name

## Kickstarter code

```python 
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns   
# Load the data
data_table = pd.read_csv('./data/data.csv')

# Your code here
```
