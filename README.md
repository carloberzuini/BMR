# BMR
CONTEXT: Many statistical studies aim to assess the causal effect of a phenotype or exposure, X, on an outcome Y. In many such studies
an experimental design is unfeasible, and the only remaining option is to work on the basis of observational data. Unfortunately in
this case, no matter how impeccable is the study design, how accurate are the observations and smart the inference algorithm, there
is no guarantee that the result will not be biased due to unobserved confounding or reverse causation. A useful approach to this 
situation is Mendelian randomisation (MR) (Katan 1986, Davey 2003, Lawlor 2008). The bare bones of the idea are that, under
certain assumptions, for a  phenotype X to be a causal influence on an outcome Y, we expect a genetic variant Z that modulates 
X to likewise affect Y.  Information about Z can then be used as an instrument to assess the causal effect of X on Y, despite confounding.
In such a context, the variable Z will often be called an instrumental variable, or briefly, an instrument.

RELEVANCE: The potential impact of MR on science cannot be underestimated (Robinson 2017). In various occasions, an MR study based on
observational data has predicted the outcome  of a clinical trial, thereby supporting or casting doubt on  the motivating causal
hypothesis (see, for example, Voight 2012). Furthermore, MR can help biologists reconstruct a disease process from its molecular 
causes to its phenotypic manifestations, and unravel causal relationships of pharmacological relevance through the analysis of 
biobank data.

STATE OF THE ART: Recent developments, mostly in the frequentist realm, have focused on methods for multi-instrument MR (MIMR),
notably Egger regression (ER) and the weighted median estimator (WME) of Bowden (2016). These methods use multiple instruments,
while allowing an unspecified subset of them to affect the outcome directly. In brief, these methods allow for "cryptic" pleiotropy.

MOTIVATION: The existing frequentist approaches to MR do not coherently account for important sources of uncertainty, such as the
uncertainty arising from the estimation of the instrument-exposure (i-e) associations. Hence our concern that these methods may 
yield over-optimistic results. We attempt to remedy this by proposing a Bayesian approach to MR (Burgess 2010, 2012; Didelez 2007;
Jones 2012) which deals with cryptic pleiotropy, and can in principle acknowledge uncertainty at all levels of the model. 

PROPOSED BAYESIAN FRAMEWORK FOR MR: Our method allows the user to shape the prior of the entertained MR model on the basis of 
external information, for stronger and more  accurate inferences, although it will work with vague prior specifications, too. 
The method combines the power of Bayesian analysis with  that of Markov chain Monte Carlo (MCMC) inference, for an exceptional 
freedom in elaborating the  basic model. At the current point in time, this repository contains methods that do not deal with 
non-linear dependencies and  model uncertainty, and assume that the exposure variable X and and the noutcome variable Y are 
continuous.

The current version of the proposed method relaxes the  exclusion-restriction assumption, whereby an instrument cannot affect 
the outcome other than through their influence on the exposure, and allows the instruments to be correlated, for an increased 
power to  detect the  causal effect of interest, and to exert direct (sometimes called pleiotropic) effects on the outcome. 
By having the pleiotropic effects represented in the model by unknown parameters, and by imposing a prior distribution that 
assumes an  unspecified subset  of them to be zero, we obtain a proper  posterior distribution for the causal effect of interest. 
This posterior we sample via  Markov chain Monte Carlo to obtain point and interval  estimates. The model priors require a 
minimal input from  the user. 

An upcoming article on Biostatistics, by Carlo Berzuini, Hui Guo, Stephen Burgess and Luisa Bernardinelli, describes the method 
and reports about a simulation experiment that assesses its performance in terms of type-1 error and power in various
situations, including the presence of correlated instruments and instrument weakness. 

AIMS OF BMR PROJECT: The aim of the present project is to collaboorate in developing  Mendelian randomisation methods for 
situations of practical or scientific interest, within a Bayesian modelling framework. Possible directions of development 
are incorporating multiple  types of external information in the prior, handling multiple sources of uncertainty, and 
elaborating the basic model to tackle a new or extended class of problems, within the field of genomic epidemiology or other 
related areas.

R: We assume the availability of the free software environment for statistical computing and graphics called R. R compiles and
runs on a wide variety of UNIX platforms, Windows and MacOS. To download R, please access https://www.r-project.org and choose 
your  preferred CRAN mirror.

RSTUDIO: We assume the availability of the RStudio software, that allows the user to run R in a more user-friendly environment.
Rstudio is open-source (which means free), and available at http://www.rstudio.com/

SWEAVE: R includes a powerful and flexible system called Sweave for creating dynamic reports and reproducible research using LaTeX.
Sweave enables the embedding of R code within a LaTeX document to generate a PDF file that includes narrative and analysis, 
graphics, code, and the results of computations. Find detailed information about the use of Sweave within RStudio on
https://support.rstudio.com/hc/en-us/articles/200552056-Using-Sweave-and-knitr In order to run Sweave, you will need a LaTeX
installation.

STAN: We finally assume the availability of the  probabilistic modelling language STAN. For links to up-to-date code, examples, manuals, 
bug reports, feature requests, and  everything else related to  STAN, see the STAN home page: http://mc-stan.org/. Our current
implementation uses the R interface  to STAN called Rstan. The Rstan home page is http://mc-stan.org/rstan.html.


FILES CURRENTLY INCLUDED IN THIS REPOSITORY:

The file SweaveDocument contains a basic Sweave template. The document contains both LaTeX text sections and chunks of R code, interweaved 
with one another. Running this from within Rstudio will generate a PDF file that includes narrative and analysis, graphics, code, 
and the results of computations. You can use the document as a basis for developing more elaborate analyses, by altering both the 
LaTeX narrative and the  R code. Currently, the document contains two functions R that perform an essential role in the implementation 
of a Mendelian Randomisation analysis, and an illustrative implementation of an analysis where a dataset is simulated from a basic
Mendelian Randomisation model, in accord with modifiable parameter values, and then analysed by the method discussed in the
above mentioned paper. When using Rstudio, you can insert an R chunk via the Chunks menu at the top right of the Rstudio source
editor. Once the Sweave document is ready, you can run it from within Rstudio to generate the output PDF file.

The file LaTeXDocument contains the LaTeX output from running SweaveDocument.

The file PDFDocument has been generated by compiling LaTeXDocument.

No external data are provided.

For any queries write to carlo.berzuini@manchester.ac.uk







