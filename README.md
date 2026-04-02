[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/uo-phys/comp-phys-26)

# Notebooks and Data for Computational Physics - Spring 26

This is a collection of notebooks and data, which will be added to throughout the term.

## Environment

This repository is setup to be plug-and-play with `uv`. After cloning or pulling updates to the repository, you can ensure all depencies are in the local virtual environment by running

```bash
uv sync
```

You can either activate the environment manually, or run commands through `uv` to make use of the environment, e.g.,

```bash
uv run jupyter lab
```

`uv run` will even take care of environment syncing automatically if it hasn't already been done.

## Notebooks

### Week 1

* Explore data on birth rates in the US: [Birth Data Exploration.ipynb](notebooks/Birth%20Data%20Exploration.ipynb)

## Data Provenance

### Exploring births in the US

US Birth data from the Social Security Administration, prepared by FiveThirtyEight.

[source](https://github.com/fivethirtyeight/data/tree/master/births)

This data can be with a wget command:

```bash
mkdir -p ../data
wget -qO ../data/US_births_2000-2014_SSA.csv https://raw.githubusercontent.com/fivethirtyeight/data/master/births/US_births_2000-2014_SSA.csv
```
