# Materials Informatics Tutorial: 2D Magnets

A hands-on introduction to Python and materials informatics, built around a dataset of two-dimensional magnetic materials. No prior programming experience required.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/quantum-intelligence/semiconductor-manufacturing-analytics/blob/main/notebooks/materials_informatics.ipynb)


---

## What this is

A short tutorial in two parts, designed to be worked through in a single session:

**Part 1 — Introduction to Python.** Enough to be dangerous: notebooks, variables, lists and numpy arrays, loading a spreadsheet with pandas, filtering rows, and making a plot. Some exercises use the 2D magnets data.

**Part 2 — Introduction to materials informatics.** Turning chemical formulas into numbers a model can use, training a model to predict a magnetic property, evaluating it honestly, and recognising the need to carefully analyze materials datasets.

You will finish with a working notebook that predicts a property of a 2D magnet from its composition.

## Who it's for

Materials scientists, chemists, engineers and physicists who have heard that machine learning is useful and want to find out what it actually looks like. If you have never written a line of code, you are the target audience. If you already use Python daily, skip to Part 2.

## Learning outcomes

By the end you should be able to:

1. Run and modify code in a Jupyter notebook, and read an error message to find the line that failed.
2. Load a dataset with pandas, inspect it, filter rows, and plot a column.
3. Frame a materials question as a supervised regression problem, naming the inputs, the target, and what counts as one sample.
4. Explain why data is split into training, validation and test sets, fit a scikit-learn model, and interpret MAE and R² in the units of the problem.
5. Explain why a chemical formula cannot be given to a model directly, and describe how composition-based descriptors work.
6. Give at least two reasons a reported accuracy on a materials dataset may overstate real-world performance.

---

## Quick start

### Option 1 — Google Colab (recommended)

Nothing to install. Click a notebook below; it opens in your browser.

| Notebook | Open |
|---|---|
Introduction to Python & Materials informatics | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/quantum-intelligence/semiconductor-manufacturing-analytics/blob/main/notebooks/materials_informatics.ipynb) |


You need a Google account. The first cell installs everything and takes about a minute.

### Option 2 — Local install

```bash
git clone https://github.com/quantum-intelligence/semiconductor-manufacturing-analytics.git
cd semiconductor-manufacturing-analytics
python -m venv tutorial-env
source tutorial-env/bin/activate
pip install -r requirements.txt
jupyter lab
```

---

## Repository structure

```
.
├── data/
│   ├── gmagneticmoment_Ef_data.csv           # the tutorial dataset
│   └── README.md                # provenance, columns, units, license
├── notebooks/
│   └── materials_informatics.ipynb
├── slides/
│   └── Rhone Upwards Tutorial Round 1.ppt
├── requirements.txt
└── README.md
```

---

## The dataset

`data/magneticmoment_Ef_data.csv` contains two-dimensional magnetic materials data — the family of materials is derived from Cr₂Ge₂Te₆.

Typical columns:

| Column | Description | Units |
|---|---|---|
| `formula` | Chemical formula of the monolayer | — |
| `magnetic_moment` | Magnetic moment per magnetic atom | μ_B |
| `magnetic_order` | Ferromagnetic, antiferromagnetic | — |
| `formation_energy` | Formation energy per unit cell | eV/unit cell |




### Two warnings about this data

**The labels are calculated, not measured.** These properties come from DFT. Predicted Curie temperatures and anisotropies for 2D magnets are notoriously sensitive to the functional and the treatment of correlation, and experimental confirmation exists for only a handful of these materials. A model trained here predicts *what DFT would say*, which is not the same thing as what a material would do in the lab (or fab).

**"MAE" is ambiguous in this field.** It means *magnetic anisotropy energy* to a magnetism researcher and *mean absolute error* to a machine learning practitioner, and both appear in this field of study. The notebook shown here refers to the mean absolute error. Watch for this in the literature.

---

## Tentative schedule (3 hours)

| Time | Block |
|---|---|
| 0:00–0:30 | Lecture: Materials Informatics |
| 0:30–0:40 | Setup, open the notebook, run the first cell |
| 0:40–1:15 | Part 1 — Python |
| 1:15–2:00 | Part 2a — framing, descriptors, first model |
| 2:00–2:10 | Break |
| 2:10–2:55 | Part 2b — evaluation, and why the model performance score is optimistic |
| 2:55–3:00 | Wrap-up, limitations, where to go next |

---

## Troubleshooting

**A cell's output didn't change after I edited it.** Re-run it — Shift+Enter. Editing alone does nothing.

**`KeyError: 'Formation_energy'`.** Column names are case- and spelling-sensitive. Run `df.columns` to see the real names.

**`NameError: name 'df' is not defined`.** You skipped a cell, or restarted the kernel. Run everything from the top: *Runtime → Run all* in Colab.

**`ModuleNotFoundError` in Colab.** Re-run the first cell; Colab resets its environment after a period of inactivity.


---

## Where to go next

- **scikit-learn user guide** — the standard reference for everything in Part 2.
- **matminer** — featurisers, dataset loaders, and a large set of worked examples.
- **pymatgen** — structure manipulation and materials analysis.
- **C2DB / Materials Cloud 2D / 2DMatPedia** — computational databases of 2D materials, including magnetic ones.
- **"APS GDS Tutorials"** for more information.

---

## Contributing

Corrections and issue reports are welcome. If you use this material in your own teaching, an acknowledgement is appreciated but not required.

## Citation

If this tutorial contributed to work you publish, please cite it as:

```bibtex
@misc{REPO,
  author = {Trevor David Rhone},
  title  = {NSF UPWARDS Summer School, Materials Informatics Tutorial: Materials design and discovery},
  year   = {2026},
  url    = {https://github.com/quantum-intelligence/semiconductor-manufacturing-analytics}
}
```

Cite the underlying dataset separately, according to its own terms.

## License

Code and notebooks: MIT (see `LICENSE`).
Tutorial text and slides: CC BY 4.0.
The dataset is redistributed under its original license — see `data/README.md`.

## Acknowledgements

Thanks to the National Science Foundation UPWARDS for the Future Network for supporting the broader research environment.

