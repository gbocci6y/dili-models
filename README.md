# DILI prediction models

Jupyter notebooks accompanying the machine learning workflows for drug-induced liver injury (DILI) prediction described in the associated manuscript. The repository is intended to support inspection and reproduction of the analyses. The results may depend on the data files, software versions, and execution settings described below.

## Repository contents

| Path | Description |
|---|---|
| `notebooks/tier0_model_workflow.ipynb` | Tier 0 model workflow. |
| `notebooks/tier2_model_workflow.ipynb` | Tier 2 model workflow. |
| `notebooks/altast_model_workflow.ipynb` | ALT/AST model workflow. |
| `notebooks/tbl_model_workflow.ipynb` | TBL model workflow. |
| `notebooks/dilirank2_tier0_predictions.ipynb` | Tier 0 temporal validation using DILIrank 2.0 data. |
| `data/` | Folder containing the input workbook used by the notebooks. |
| `results/` | Destination for generated result tables and predictions. |

## Requirements and setup

Python dependencies are documented in [`environment.yml`](environment.yml). The recommended starting point is:

```bash
conda env create -f environment.yml
conda activate dili-models
python -m ipykernel install --user --name dili-models --display-name "Python (dili-models)"
cd notebooks
jupyter-lab
```

Launch JupyterLab from the `notebooks/` directory so the notebooks’ existing `../data/` and `../results/` relative paths resolve correctly. Select the **Python (dili-models)** kernel. The environment specification pins the principal dependencies but may not reproduce every platform-specific detail of the original environment. See the environment README for details.

## Running the notebooks

1. Ensure you have access to the required input workbook in `data/` named `Supporting Information 2.xlsx`.
2. Start JupyterLab from the repository root.
3. Open the relevant notebook under `notebooks/`.
4. Read the notebook from top to bottom and execute the cells in order. Some workflows perform hyperparameter optimisation and may take substantial time.
5. Generated tables and prediction files are written to `results/` by the relevant notebooks. The exact filenames depend on the workflow and selected split/endpoint settings.

The notebooks resolve the input workbook using relative paths and no longer require a user-specific absolute file path. Run them with the working directory set to `notebooks/`, as described above, so output paths also resolve correctly.

## Reproducibility notes

- Model results can vary with package versions, operating system, numerical libraries, random seeds, and execution settings.
- The notebooks may write intermediate or final result files to `results/`. These generated files are not required to create the environment.
- The included UMAP visualisations and applicability-domain analyses should be interpreted as exploratory analyses rather than standalone proof of model generalisability.

## Citation

If you use these workflows, please cite the associated manuscript and the relevant software packages, including RDKit and the machine-learning libraries used. Add the final manuscript citation here once the article has been accepted or published.
