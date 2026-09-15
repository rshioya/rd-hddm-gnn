# RD-HDDM-GNN

Reproducibility package for **Residual-driven hierarchical graph neural network for sparse-sensor steady-state temperature-field reconstruction**.

## Method

The fine-mesh GNN produces the full-field prediction. Sensor observation residuals are restricted to connected subdomains, communicated on a coarse graph, prolongated to fine nodes, and applied only as a gated correction.

## Repository layout

- `src/`: model and reusable implementation
- `configs/`: parameter-matched baseline, final RD-HDDM-GNN, smoke-test, and sensitivity configurations
- `scripts/`: training, evaluation, aggregation, and paper-table export
- `audits/`: architecture, alpha=0 equivalence, partition, and sensor audits
- `tests/`: unit tests
- `data/`: frozen prospective-dataset lock and manifest; large NPZ files should be archived in Zenodo
- `paper_results/`: compact CSV/JSON evidence supporting the manuscript tables and partition audit

## Installation

```bash
git clone https://github.com/rshioya/rd-hddm-gnn.git
cd rd-hddm-gnn
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
```

## Quick validation

```bash
python -m pytest -q
python audits/test_mesh_backbone_equivalence.py
python audits/audit_architecture.py
```

## Reproduction

Inspect the YAML files before execution and replace machine-specific paths with portable relative paths.

```bash
python scripts/run.py --config configs/smoke_test.yaml
python scripts/run.py --config configs/baseline.yaml
python scripts/run.py --config configs/rd_hddm_alpha001.yaml
python scripts/evaluate_20seeds.py --help
python scripts/measure_computational_cost.py --help
```

The exact command-line arguments may depend on the retained project adapter. Verify every command locally before creating the public release.

## Data and checkpoints

GitHub contains manifests and compact paper-result files. Large generated meshes and multi-seed checkpoints should be uploaded to Zenodo and linked here:

- Dataset DOI: `not yet assigned`
- Software release DOI: `not yet assigned`

## Citation

See [`CITATION.cff`](CITATION.cff). Add the journal DOI and Zenodo version DOI after publication/release.

## License

Code is released under the MIT License. Confirm that all third-party code and data permit redistribution before publication.

<!-- DOI-METADATA:BEGIN -->
## Archived release

The public reproducibility package is archived on Zenodo.

- DOI: https://doi.org/10.5281/zenodo.22769372
- GitHub repository: https://github.com/rshioya/rd-hddm-gnn

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.22769372.svg)](https://doi.org/10.5281/zenodo.22769372)
<!-- DOI-METADATA:END -->
