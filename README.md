[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/uo-phys/comp-phys-26)

# Notebooks and Data for Computational Physics - Spring 26

This is a collection of notebooks and data, which will be added to throughout the term.

## Environment

This repository is setup to be plug-and-play with `uv`. After cloning or pulling updates to the repository, you can ensure all dependencies are in the local virtual environment by running

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
* Start our introduction to sampling: [Intro to Sampling.ipynb](notebooks/Intro%20to%20Sampling.ipynb)

### Week 2

* Continue our introduction to sampling, including importance sampling and starting MCMC: [Intro to Sampling.ipynb](notebooks/Intro%20to%20Sampling.ipynb)

### Week 3

* Use monte carlo methods to explore a 2-D Ising model: [Boltzmann and Ising (and some Metropolis).ipynb](notebooks/Boltzmann%20and%20Ising%20(and%20some%20Metropolis).ipynb)
* Start building the statistical foundation behind regression: [Intro to Regression.ipynb](notebooks/Intro%20to%20Regression.ipynb)

### Week 4

* Return to [Intro to Sampling.ipynb](notebooks/Intro%20to%20Sampling.ipynb) and implement MCMC sampling.
* Continue building the statistical foundation behind regression: [Intro to Regression.ipynb](notebooks/Intro%20to%20Regression.ipynb)
* Introduce Gaia data and explore the solar neighborhood: [Solar Neighborhood w Gaia.ipynb](notebooks/Solar%20Neighborhood%20w%20Gaia.ipynb)

### Week 5

* Introduce `JAX` and `numpyro`: [Intro to NumPyro.ipynb](notebooks/Intro%20to%20NumPyro.ipynb)
* Explore coin flipping example to develop intuition for Bayes' theorem: [Coin Flipping w Numpyro.ipynb](notebooks/Coin%20Flipping%20w%20Numpyro.ipynb)


## Data Provenance

### Exploring births in the US

US Birth data from the Social Security Administration, prepared by FiveThirtyEight.

[source](https://github.com/fivethirtyeight/data/tree/master/births)

This data can be with a wget command:

```bash
mkdir -p ../data
wget -qO ../data/US_births_2000-2014_SSA.csv https://raw.githubusercontent.com/fivethirtyeight/data/master/births/US_births_2000-2014_SSA.csv
```
### Synthetic data for linear regression

This data accompanies [Hogg, Bovy, and Lang (2010)](https://arxiv.org/abs/1008.4686).  It can be downloaded directly with

```bash
!wget -O ../data/data_yerr.dat https://raw.githubusercontent.com/davidwhogg/DataAnalysisRecipes/master/straightline/src/data_yerr.dat
```

### Solar Neighborhood w/ Gaia

We will use the [Gaia DR3 data release](https://gea.esac.esa.int/archive/) to explore the solar neighborhood. The data is available from the Gaia Archive. We will use the following query to get the data:

```sql
SELECT TOP 300000 phot_g_mean_mag+5*log10(parallax)-10 AS mg, bp_rp, parallax FROM gaiadr3.gaia_source
WHERE parallax_over_error > 10
AND parallax > 10
AND phot_g_mean_flux_over_error>50
AND phot_rp_mean_flux_over_error>20
AND phot_bp_mean_flux_over_error>20
AND phot_bp_rp_excess_factor < 1.3+0.06*power(phot_bp_mean_mag-phot_rp_mean_mag,2)
AND phot_bp_rp_excess_factor > 1.0+0.015*power(phot_bp_mean_mag-phot_rp_mean_mag,2)
AND visibility_periods_used>8
AND astrometric_chi2_al/(astrometric_n_good_obs_al-5)<1.44*greatest(1,exp(-0.4*(phot_g_mean_mag-19.5)))
```

### CO<sub>2</sub> Concentrations in Mauna Loa, Hawaii

Monthy-averaged CO<sub>2</sub> concentrations measured in Mauna Loa, Hawaii, hosted by the NOAA:

```bash
!wget -q ftp://aftp.cmdl.noaa.gov/products/trends/co2/co2_mm_mlo.txt -O ../data/co2_mm_mlo.txt
```
