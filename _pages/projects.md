---
permalink: /projects/
title: "Research projects"
layout: splash
classes: wide
author_profile: false
toc: true
toc_sticky: true
search: true
---
## Machine learning-based surrogate modeling

Surrogate-modeling techniques including Polynomial Chaos Expansion (PCE) is widely used for statistical estimation (aka. Uncertainty Quantification) of quantities of interests. PCE is a data-driven regression-based technique that relies on spectral polynomials as basis-functions. In this technique, the outputs of few numerical simulations (e.g. expensive computational models) are used to estimate the PCE coefficients within a regression framework combined with regularization techniques where the regularization parameters are estimated using standard cross-validation as applied in supervised machine learning methods. In the project we introduced an efficient method for estimating the PCE coefficients combining Elastic Net regularization with a data-driven feature ranking approach. Our goal is to increase the probability of identifying the most significant PCE components by assigning each of the PCE coefficients a numerical value reflecting the magnitude of the coefficient and its stability with respect to perturbations in the input data. In our evaluations, the proposed approach has shown high convergence rate for high-dimensional problems, where standard feature ranking might be challenging due to the curse of dimensionality. The presented method is implemented within a standard machine learning library ([scikit-learn](https://scikit-learn.org/stable/index.html)) allowing for easy experimentation with various solvers and regularization techniques (e.g. Tikhonov, LASSO, LARS, Elastic Net) and enabling automatic cross-validation techniques using a widely used and well tested implementation. We present a set of numerical tests on standard analytical functions, a two-phase subsurface flow model and a simulation dataset for CO2 sequestration in a saline aquifer. For all test cases, the proposed approach resulted in a significant increase in PCE convergence rates.

**Checkout [polychaos-learn](https://github.com/ahmed-h-elsheikh/polychaos-learn), an open source Polynomial Chaos Expansions library**
{: .notice--danger}

- Alexander Tarakanov, Ahmed H. Elsheikh, **Regression-based sparse polynomial chaos for uncertainty quantification of subsurface flow models**, Journal of Computational Physics, Volume 399, (2019). [URL](https://doi.org/10.1016/j.jcp.2019.108909)

- Alexadner Tarakanov, Ahmed H. Elsheikh, **Optimal Bayesian experimental design for subsurface flow problems**,
Computer Methods in Applied Mechanics and Engineering, Volume 370 (2020). [URL](https://doi.org/10.1016/j.cma.2020.113208)

- Ahmed H. Elsheikh, Ibrahim Hoteit, Mary F. Wheeler, **Efficient Bayesian inference of subsurface flow models using nested sampling and sparse polynomial chaos surrogates,** Computer Methods in Applied Mechanics and Engineering,
Volume 269, Pages 515-537 (2014). [URL](https://doi.org/10.1016/j.cma.2013.11.001)

## Multiscale modeling using deep learning

Multiscale methods aim to address the computational cost of elliptic problems on extremely large grids, by using numerically computed basis functions to reduce the dimensionality and complexity of the task. When multiscale methods are applied in uncertainty quantification to solve for a large number of parameter realizations, these basis functions need to be computed repeatedly for each realization. In our recent work (Chan et al. in J Comput Phys 354:493–511, 2017), we introduced a data-driven approach to further accelerate multiscale methods within uncertainty quantification. The basic idea is to construct a surrogate model to generate such basis functions at a much faster speed. The surrogate is modeled using a dataset of computed basis functions collected from a few runs of the multiscale method. Our previous study showed the effectiveness of this framework where speedups of two orders of magnitude were achieved in computing the basis functions while maintaining very good accuracy, however the study was limited to tracer flow/steady state flow problems. In this work, we extend the study to cover transient multiphase flow in porous media and provide further assessments.

- Chan, S., Elsheikh, A.H., **A machine learning approach for efficient uncertainty quantification using multiscale methods.** Journal of Computational Physics, volume 354, 493–511 (2017). [URL](https://doi.org/10.1016/j.jcp.2017.10.034)

- Chan, S., Elsheikh, A.H., **Data-driven acceleration of multiscale methods for uncertainty quantification: application in transient multiphase flow in porous media.** GEM - International Journal on Geomathematics 11, 3 (2020). [URL](https://doi.org/10.1007/s13137-019-0139-1)

---
## Representation and Generation of stochastic fields using GANs
Deep learning techniques are increasingly being considered for computational applications where—much like in computer vision—the challenges are characterized by high-dimensional spatial data dominated by multipoint statistics. In particular, a novel technique called generative adversarial networks (GANs) has been recently studied for spatial geological parametrization and synthesis, obtaining very impressive results that are at least qualitatively competitive with previous methods. The method obtains a neural network parametrization of the geology—so-called a generator—that is capable of reproducing very complex geological patterns with dimensionality reduction of several orders of magnitude. Subsequent works have addressed the conditioning task, i.e., using the generator to generate realizations honoring spatial observations (hard data). The current approaches, however, do not provide a parametrization of the conditional generation process. In this work, we propose a method to obtain a parametrization for direct generation of conditional realizations. The main idea is to simply extend the existing generator network by stacking a second inference network that learns to perform the conditioning. This inference network is a neural network trained to sample a posterior distribution derived using a Bayesian formulation of the conditioning task. The resulting extended neural network thus provides the conditional parametrization.

- Chan, S., Elsheikh, A.H., **Parametrization and generation of geological models with generative adversarial networks.** arXiv preprint arXiv:1708.01810 (2017). [URL](https://arxiv.org/abs/1708.01810)

- Chan, S., Elsheikh, A.H., **Parametric generation of conditional geological realizations using generative neural networks.** Computational Geosciences, volume 23, 925–952 (2019). [URL](https://doi.org/10.1007/s10596-019-09850-7)

- Chan, S., Elsheikh, A.H., **Parametrization of Stochastic Inputs Using Generative Adversarial Networks With Application in Geology**, Frontiers in Water, volume 2, pages 5 (2020). [URL](https://doi.org/10.3389/frwa.2020.00005)

---
## Model reduction using physics informed Deep Residual Recurrent Neural Networks
We introduced a deep residual recurrent neural network (DR-RNN) as an efficient model reduction technique for nonlinear dynamical systems. DR-RNN is inspired by the iterative steps of line search methods in finding the residual minimiser of numerically discretized differential equations. We formulate this iterative scheme as a stacked recurrent neural network (RNN) embedded with the dynamical structure of the emulated differential equations. Numerical examples demonstrate that DR-RNN can effectively emulate the full order models of nonlinear physical systems with a significantly lower number of parameters in comparison to standard RNN architectures. Further, we combined DR-RNN with Proper Orthogonal Decomposition (POD) for model reduction of time dependent partial differential equations. The presented numerical results show the stability of proposed DR-RNN as an explicit reduced order technique. We also show significant gains in accuracy by increasing the depth of proposed DR-RNNsimilar to other applications of deep learning.

- Kani, J.N., Elsheikh, A.H., **DR-RNN: A deep residual recurrent neural network for model reduction.**
arXiv preprint arXiv:1709.00939 (2017). [URL](https://arxiv.org/abs/1709.00939)
- J. Nagoor Kani, Elsheikh, A.H., **Reduced-Order Modeling of Subsurface Multi-phase Flow Models Using Deep Residual Recurrent Neural Networks.** Transport in Porous Media, volume 126, pages 713–741 (2019). [URL](https://doi.org/10.1007/s11242-018-1170-7)

---
## Robust calibration and predictions using imperfect physical models

In this work, we evaluate different algorithms to account for model errors while estimating the model parameters, especially when the model discrepancy (used interchangeably with “model error”) is large. In addition, we introduce two new algorithms that are closely related to some of the published approaches under consideration. Considering all these algorithms, the first calibration approach (base case scenario) relies on Bayesian inversion using iterative ensemble smoothing with annealing schedules without any special treatment for the model error. In the second approach, the residual obtained after calibration is used to iteratively update the total error covariance combining the effects of both model errors and measurement errors. In the third approach, the principal component analysis (PCA)‐based error model is used to represent the model discrepancy during history matching. This leads to a joint inverse problem in which both the model parameters and the parameters of a PCA‐based error model are estimated. For the joint inversion within the Bayesian framework, prior distributions have to be defined for all the estimated parameters, and the prior distribution for the PCA‐based error model parameters are generally hard to define. In this study, the prior statistics of the model discrepancy parameters are estimated using the outputs from pairs of high‐fidelity and low‐fidelity models generated from the prior realizations. The fourth approach is similar to the third approach; however, an additional covariance matrix of difference between a PCA‐based error model and the corresponding actual realizations of prior error is added to the covariance matrix of the measurement error.
The first newly introduced algorithm (fifth approach) relies on building an orthonormal basis for the misfit component of the error model, which is obtained from a difference between the PCA‐based error model and the corresponding actual realizations of the prior error. The misfit component of the error model is subtracted from the data residual (difference between observations and model outputs) to eliminate the incorrect relative contribution to the prediction from the physical model and the error model. In the second newly introduced algorithm (sixth approach), we use the PCA‐based error model as a physically motivated bias correction term and an iterative update of the covariance matrix of the total error during history matching. All the algorithms are evaluated using three forecasting measures, and the results show that a good parameterization of the error model is needed to obtain a good estimate of physical model parameters and to provide better predictions. In this study, the last three approaches (i.e., fourth, fifth, sixth) outperform the other methods in terms of the quality of estimated model parameters and the prediction capability of the calibrated imperfect models.

- Rammay, M.H., Elsheikh, A.H. & Chen, Y., **Robust Algorithms for History Matching of Imperfect Subsurface Models.** SPE Journal, volume 25, pages 3300–3316 (2020). [URL](https://doi.org/10.2118/193838-PA)

- Rammay, M.H., Elsheikh, A.H. & Chen, Y., **Flexible iterative ensemble smoother for calibration of perfect and imperfect models.** Computational Geosciences, volume 25, pages 373–394 (2021). [URL](https://doi.org/10.1007/s10596-020-10008-z)

- Rammay, M.H., Elsheikh, A.H. & Chen, Y., **Quantification of prediction uncertainty using imperfect subsurface models with model error estimation.** Journal of Hydrology, volume 576, pages 764-783 (2019). [URL](https://doi.org/10.1016/j.jhydrol.2019.02.056)


<!-- ## test code embedding

```python
def foo():
    if not bar:
        return True
```
### Figures in the text:

{% include figure image_path="/assets/images/unsplash-image-1.jpg" alt="this is a placeholder image" caption="This is a figure caption." %} -->

### Contact details
```
Email: <a.elsheikh> at Heriot-Watt address <hw.ac.uk>
Post: Heriot-Watt University, Edinburgh, EH14 1AS, UK
Tel: +44 (0)131 451 8304
Fax: +44 (0)131 451 3127
```
