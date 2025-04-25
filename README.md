"Supplementary-work-fitting-Leitao-framework" 
for 'Scaling Urban Infrastructure for Sustainable Development Goals with Efficiency and Equality' 
by Fernando F. Assad, Gabrielle M. Marega, Nitish R. Sarker, and David D. J. Meyer

Overview
This Jupyter notebook builds upon the existing codebase from Leitao et al. under the GNU General Public License v3.0 (GPL-3.0). No substantial modifications were made to the original code, but new SNIS and IBNET water and sewer datasets were added for model fitting using the Leitao framework.

Reference:
J.C. Leitao, J.M. Miotto, M. Gerlach, E.G. Altmann, Is this scaling nonlinear?, Royal Society Open Science 3, 150649 (2016) DOI: 10.1098/rsos.150649.

Modifications

- Added new input data: SNIS (2020) and IBNET (2015) water/sewer data. 
- Original datasets from Leitao (Brazil datasets) remain for exploration. 
- The data is always a tuple (x, y) of numpy arrays of the same size, where x is always (total or served) population.

License

This notebook follows the GPL-3.0 license as per the original repository. Refer to the original repo for full licensing details.

Code
- The easiset way to interact and run the code is through the Notebooks in the folder 
- Likelihood and Minimization: All inference is performed based on the likelihood of different models. The module `best_parameters.py` contains the definition of the likelihood functions of the models,
the minimization algorithm, and the parameters we use in it.  The bootstrap (100 repetitions as default) used to estimate error bars is also defined in this module, at `minimize_with_errors`.
- The Lognormal analysis (and other models provided by Leitao et al.) are defined in 'analysis_SNIS_IBNET.py'. The general settings are defined in 'LikelihoodAnalysis' and respective methods.
- For example, to get beta estimated by Log-Normal with free \delta and other statistical information, use

  from analysis_SNIS_IBNET import LogNormalAnalysis
  analysis = LogNormalAnalysis('brazil_sewerN', required_successes=24)
  
  analysis.beta[0]

  analysis.p_value

  analysis.bic

Results
- Pre-computed results are stored at `_results`. In case you want to reproduce some of the results stored in `_results`, you can delete the respective 
analysis in the directory and run (may take some time). 
- To recreate the supplementary figures S8 through S11 (both left and right figures), change the dataset names to 
brazil_sewerN (default), brazil_sewerM, brazil_waterN, brazil_waterM, ibnetsewerN, ibnetsewerM, ibnetwaterN, ibnetwaterM.
- The last two cells of the Notebook run through reproduce the stored results for all dataset and the data presented in supplementary Table S4.

References

This repository contains both data and code from the paper:
[1] Is this scaling non-linear? by Jorge C. Leitão, José M. Miotto, Martin Gerlach, and [Eduardo G. Altmann](https://www.maths.usyd.edu.au/u/ega/), [Royal Society Open Science 3, 150649 (2016)](https://royalsocietypublishing.org/doi/10.1098/rsos.150649).  | [See Notebook](https://github.com/edugalt/scaling/blob/master/notebooks/Notebook-FittingModels.ipynb) | [Open Notebook in Colab](https://colab.research.google.com/github/edugalt/scaling/blob/master/notebooks/Notebook-FittingModels-Colab.ipynb)
