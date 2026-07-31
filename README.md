# Materials Informatics Tutorial: 2D Magnets

A hands-on introduction to Python and materials informatics, built around a dataset of two-dimensional magnetic materials. No prior programming experience required.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/quantum-intelligence/semiconductor-manufacturing-analytics/blob/main/notebooks/materials_informatics.ipynb)


---

## What this is

A short tutorial in two parts, designed to be worked through in a single session:

**Part 1 — Introduction to Python.** Enough to be dangerous: notebooks, variables, lists and dictionaries, loading a spreadsheet with pandas, filtering rows, and making a plot. Some exercises use the 2D magnets data.

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
│   ├── magneticmoment_Ef_data.csv           # the tutorial dataset
│   └── README.md                # provenance, columns, units, license
├── notebooks/
│   └── materials_informatics.ipynb
├── slides/
├── requirements.txt
└── README.md
```

---

## The dataset

`data/2d_magnets.csv` contains two-dimensional and layered magnetic materials — the family that includes CrI₃, Cr₂Ge₂Te₆, Fe₃GeTe₂, MnBi₂Te₄, and the transition-metal phosphorus trisulfides such as NiPS₃.

Typical columns:

| Column | Description | Units |
|---|---|---|
| `formula` | Chemical formula of the monolayer | — |
| `magnetic_moment` | Magnetic moment per magnetic atom | μ_B |
| `magnetic_order` | Ferromagnetic, antiferromagnetic, non-magnetic | — |
| `anisotropy_energy` | Magnetic anisotropy energy | meV/atom |
| `exfoliation_energy` | Energy to exfoliate from the bulk parent | meV/Å² |
| `formation_energy` | Formation energy per atom | eV/atom |
| `band_gap` | Electronic band gap | eV |

**Fill in `data/README.md` with the real provenance before publishing.** Record the source (e.g. C2DB, Materials Cloud 2D, 2DMatPedia, or your own calculations), the version and download date, the level of theory, and the license under which you are permitted to redistribute it. Several 2D materials databases have redistribution terms; check before committing the CSV.

### Two warnings about this data

**The labels are calculated, not measured.** These properties come from DFT. Predicted Curie temperatures and anisotropies for 2D magnets are notoriously sensitive to the functional and the treatment of correlation, and experimental confirmation exists for only a handful of these materials. A model trained here predicts *what DFT would say*, which is not the same thing as what a sample would do.

**"MAE" is ambiguous in this field.** It means *magnetic anisotropy energy* to a magnetism researcher and *mean absolute error* to a machine learning practitioner, and both appear in this tutorial. The notebooks spell both out in full. Watch for it in the literature.

---

## Suggested schedule (3 hours)

| Time | Block |
|---|---|
| 0:00–0:10 | Setup, open the notebook, run the first cell |
| 0:10–0:45 | Part 1 — Python |
| 0:45–1:40 | Part 2a — framing, features, first model |
| 1:40–1:50 | Break |
| 1:50–2:40 | Part 2b — evaluation, and why the number is optimistic |
| 2:40–3:00 | Wrap-up, limitations, where to go next |

---

## Troubleshooting

**A cell's output didn't change after I edited it.** Re-run it — Shift+Enter. Editing alone does nothing.

**`KeyError: 'Band_gap'`.** Column names are case- and spelling-sensitive. Run `df.columns` to see the real names.

**`NameError: name 'df' is not defined`.** You skipped a cell, or restarted the kernel. Run everything from the top: *Runtime → Run all* in Colab.

**`ModuleNotFoundError` in Colab.** Re-run the first cell; Colab resets its environment after a period of inactivity.

**Featurisation is slow or fails to install.** Use `data/2d_magnets_features.csv`, which has the descriptors already computed. The notebook shows how to switch.

---

## Where to go next

- **scikit-learn user guide** — the standard reference for everything in Part 2.
- **matminer** — featurisers, dataset loaders, and a large set of worked examples.
- **pymatgen** — structure manipulation and materials analysis.
- **C2DB / Materials Cloud 2D / 2DMatPedia** — computational databases of 2D materials, including magnetic ones.
- **"Best practices in machine learning for chemistry"** and similar methods commentaries — read one before you publish a model.

---

## Contributing

Corrections and issue reports are welcome. If you use this material in your own teaching, an acknowledgement is appreciated but not required.

## Citation

If this tutorial contributed to work you publish, please cite it as:

```bibtex
@misc{REPO,
  author = {AUTHOR NAME},
  title  = {Materials Informatics Tutorial: 2D Magnets},
  year   = {2026},
  url    = {https://github.com/ORG/REPO}
}
```

Cite the underlying dataset separately, according to its own terms.

## License

Code and notebooks: MIT (see `LICENSE`).
Tutorial text and slides: CC BY 4.0.
The dataset is redistributed under its original license — see `data/README.md`.

## Acknowledgements

ADD FUNDING, HOST INSTITUTION, DATASET AUTHORS, AND ANYONE WHO TESTED THE NOTEBOOKS.
