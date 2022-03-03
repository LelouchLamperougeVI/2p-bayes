# 2p-bayes
Decode animal location in 1D under two-photon imaging. Method is based on
```
Interpreting Neuronal Population Activity by Reconstruction: Unified Framework With Application to Hippocampal Place Cells
Kechen Zhang, Iris Ginzburg, Bruce L. McNaughton, and Terrence J. Sejnowski
Journal of Neurophysiology 1998 79:2, 1017-1044 
```
but employs Maximum _a posteriori_ estimation with some "hacks" to circumvant the quirks inherent to two-photon calcium signals.

## Usage
The function has the following format: `md = sam_mape(x, n, trials, 'name', value)`. 

### Inputs
#### Required inputs
`x`: Vector of animal location in arbitrary unit

`n`: Matrix of deconvolved calcium activity expressed as **time x neuron**, with **time** being the same length as `x`

`trials`: Vector of trial numbers of the same length as `x`

#### Optional `'name', value` pairs
`'dt', 4`: Decoding time window (see Zhang et al. 1998)

`'bins', 50`: Number of distance bins

`'circ', false`: Compute circular error

`'cv', true`: Leave-one-out cross-validation

`'mle', false`: Use Maximum likelihood estimation instead (no prior)

`'penalty', 1e-2`: Constant penalty for 0 firing rate in place of log(0) = -inf

`'smooth', 5`: Gaussian smoothing factor

`'custom', vector`: Cross-validate on user specified indices

### Outputs
Output model is embedded in the `md` structure:

`md.decoded`: Vector of decoded animal locations

`md.x`: Vector of actual animal locations

`md.err`: Absolute error as a function of distance

`md.oerr`: Overall decoding error

`md.ops`: Input options/parameters

## About
This script has been featured in
```
Coordinated activities of retrosplenial ensembles during resting-state encode spatial landmarks
HaoRan Chang, Ingrid M. Esteves, Adam R. Neumann, Jianjun Sun, Majid H. Mohajerani and Bruce L. McNaughton
Philosophical Transactions of the Royal Society B 2020 375:1799
```
and
```
Spatial Information Encoding across Multiple Neocortical Regions Depends on an Intact Hippocampus
Ingrid M. Esteves, HaoRan Chang, Adam R. Neumann, JianJun Sun, Majid H. Mohajerani, Bruce L. McNaughton
Journal of Neuroscience 2021 41:2, 307-319
```
.
