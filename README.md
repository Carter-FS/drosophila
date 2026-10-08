# drosophila

Groundwork for a connectome-constrained decoder of the adult *Drosophila* brain. The repo sets up a reproducible environment for the leaky integrate-and-fire model from [Shiu et al. (2024)](https://doi.org/10.1038/s41586-024-07763-9), which runs on the FlyWire connectome and is included as a git submodule. The decoder itself is not written yet.

**Status:** Experimental

## Requirements

- [uv](https://docs.astral.sh/uv/)
- Python 3.10 (pinned in `.python-version`)

## Install

```sh
git clone --recurse-submodules https://github.com/Carter-FS/drosophila.git
cd drosophila
uv sync
```

If you cloned without `--recurse-submodules`, run `git submodule update --init --recursive`.

The environment pins `setuptools<81` and `cython<3` so that brian2 2.5.1 can build its C++ code generation backend.

## Usage

The upstream tutorial notebook shows how to activate or silence neurons by FlyWire ID and read out spike times and rates:

```sh
uv run jupyter lab Drosophila_brain_model/example.ipynb
```

`main.py` is a placeholder entry point for the decoder.

## Repo layout

```
main.py                   # entry point (placeholder)
pyproject.toml, uv.lock   # pinned dependencies
Drosophila_brain_model/   # upstream model (git submodule)
  model.py                # LIF model: create_model, run_exp, run_trial
  utils.py                # load_exps, get_rate
  example.ipynb           # tutorial notebook
  Connectivity_783.parquet, Completeness_783.csv   # FlyWire v783 connectome
```

## References

- Shiu, P. K. et al. A *Drosophila* computational brain model reveals sensorimotor processing. *Nature* (2024). https://doi.org/10.1038/s41586-024-07763-9
- Dorkenwald, S. et al. Neuronal wiring diagram of an adult brain. *Nature* (2024). https://doi.org/10.1038/s41586-024-07558-y
- Currier, T. A. et al. Infrequent strong connections constrain connectomic predictions of neuronal function. *Cell* 188 (2025). https://doi.org/10.1016/j.cell.2025.05.007
- Zhang, Y. et al. Deep learning models of cognitive processes constrained by human brain connectomes. *Medical Image Analysis* 80 (2022). https://doi.org/10.1016/j.media.2022.102507

## Licence

Released under the MIT licence (see `LICENSE`). The upstream model in the submodule is also MIT licensed.
