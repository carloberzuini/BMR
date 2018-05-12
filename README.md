# BMR
R Code for Bayesian Mendelian Randomisation

CONTEXT: Many statistical studies aim to assess the causal effect of a phenotype or exposure, X, on an outcome Y. In many such studies
an experimental design is unfeasible, and the only remaining option is to work on the basis of observational data. Unfortunately in
this case, no matter how impeccable is the study design, how accurate are the observations and smart the inference algorithm, there
is no guarantee that the result will not be biased due to unobserved confounding or reverse causation. A useful approach to this 
situation is Mendelian randomisation (MR) (Katan 1986, Davey 2003, Lawlor 2008). The bare bones of the idea are that, under
certain assumptions, for a  phenotype X to be a causal influence on an outcome Y, we expect a genetic variant Z that modulates 
X to likewise affect Y.  Information about Z can then be used as an instrument to assess the causal effect of X on Y, despite confounding.

RELEVANCE: The potential impact of MR on science cannot be underestimated (Robinson 2017). In various occasions, an MR study based on
observational data has predicted the outcome  of a clinical trial, thereby supporting or casting doubt on  the motivating causal
hypothesis (see, for example, Voight 2012). Furthermore, MR can help biologists reconstruct a disease process from its molecular 
causes to its phenotypic manifestations, and unravel causal relationships of pharmacological relevance through the analysis of 
biobank data.

STATE OF THE ART: Recent developments, mostly in the frequentist realm, have focused on methods for multi-instrument MR (MIMR),
notably Egger regression (ER) and the weighted median estimator (WME) of (Bowden 2016). These methods use multiple instruments,
while allowing an unspecified subset of them to affect the outcome directly. In brief, these methods allow for "cryptic" pleiotropy.

MOTIVATION: The existing frequentist approaches to MR do not coherently account for important sources of uncertainty, such as the
uncertainty arising from the estimation of the instrument-exposure (i-e) associations. Hence our concern that these methods may 
yield over-optimistic results. We attempt to remedy this by proposing a Bayesian approach to MR (Burgess 2010, 2012; Didelez 2007;
Jones 2012) which deals with cryptic pleiotropy, and can in principle acknowledge uncertainty at all levels of the model. 

PROPOSED METHOD: Our method allows the user to shape the prior on the basis of external information, for stronger and more 
accurate inferences, although it will work with vague prior specifications, too. It combines the power of Bayesian analysis with 
that of Markov chain Monte Carlo (MCMC) inference, for an exceptional freedom in elaborating the basic model. At the current 
point in time, the method does not deal with non-linear dependencies and model uncertainty, and restricts our attention to 
continuous X and Y variables.

In the current version of the method, the instruments are not assumed to be independent, nor required to satisfy the 
exclusion-restriction assumption, whereby they cannot affect the outcome other than  through their influence  on the exposure.
In other words, instruments are allowed to be moderately correlated with each other, for an increased power to  detect the 
causal effect of interest, and to exert direct (sometimes called pleiotropic) effects on the outcome. By having these 
effects represented in the model by unknown parameters, and by imposing a prior distribution that assumes an  unspecified subset 
of them to be zero, we obtain a proper  posterior distribution for the causal effect of  interest. This posterior we sample via 
Markov chain Monte Carlo to obtain point and interval  estimates. The model priors require a minimal input from  the user. 

An upcoming article on Biostatistics, by Carlo Berzuini, Hui Guo, Stephen Burgess and Luisa Bernardinelli, describes the method 
and reports about a simulation experiment that assesses its performance in terms of type-1 error and power in various
situations, including the presence of correlated instruments and instrument weakness. 

AIMS OF PROJECT: The aim of the present project is to exploit a Bayesian perspective on Mendelian randomisation methods to develop 
them in practically important directions, such as incorporating multiple types of external information via informative priors, 
handling multiple sources of uncertainty, and elaborating the basic model in directions of applicative relevance, in an attempt to 
meet the demands of advanced research in genomic epidemiology.

SOFTWARE: Use of the software developed in the present project requires an installation of the statistical package R and of the 
probabilistic modelling language STAN. For links to up-to-date code, examples, manuals, bug reports, feature requests, and 
everything else related to  STAN, see the STAN home page: http://mc-stan.org/.

The R interface to STAN is Rstan. The Rstan home page is http://mc-stan.org/rstan.html. One of STAN's virtues is support of
variational inference. This is an approximate Bayesian inference technique (Jordan et al., 1999; Wainwright and Jordan, 2008)
that provides an approximation of the posterior distribution, P( unknown parameters | known quantities), for an
efficient bounding of the search space.

The user may wish to implement our method with the aid of the R function and of the STAN program described in the following 
two sections.

