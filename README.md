
<!-- README.md is generated from README.Rmd. Please edit that file -->

# Bioflow

<!-- badges: start -->

[![Lifecycle:
experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://lifecycle.r-lib.org/articles/stages.html#experimental)
<!-- badges: end -->

The goal of the bioflow project is to provide methods and tools for
understanding or using evolutionary forces (mutation, gene flow,
migration and selection) such as automatic state-of-the-art genetic
evaluation (selection force). Designed to be database agnostic, it can
retrieve data from the available phenotypic-pedigree databases (EBS,
BMS, BreedBase), genotypic databases (GIGWA), and environmental
databases (NASAPOWER) data, quickly map some required features
(columns), and carry the analytical procedures.

## Scope and target audience

The current scope is limited to enable Biometrical Genetics methods
recommended by the Quantitative Genetics community of the CGIAR
\[Excellence in Breeding (EiB) and collaborator centers, now Accelerated
Breeding Initiative (ABI)\] to standardize the methods and key
performance indicators (KPIs) used across the CGIAR for decision making.
For our collaborators, please keep this in mind when submitting pull
requests for new methods since these may not be accepted if the are not
under the current recommended approaches (see contribution process
below).

The target audience is the breeders and geneticists from the CGIAR.

## Roles and responsabilities

In this project we have two different roles

Maintainers: Have the permission and responsibility to commit, push, and
merge changes. Contributor: Have the permission and responsibility to
commit, push using forked versions.

The current list of maintainers and contributors is the following:

Mainteiners: Khaled Al-Sham’aa, Ibnou Dieng, Eduardo Covarrubias
Contributor: Bert De Boeck, Raul Eizaguirre, Abhishek Rathore, Roma Das,
Keith Gardner, Angela Pacheco, Fernando Toledo, Juan Burgueno, Aubin
Amagnide, Luis Delgado Munoz, Christian Cadena, Christian Werner, Sergio
Cruz, Alaine Gulles, Justine Bonifacio.

## Demo server

A demo of the application can be accessed at:

<https://cgiar-market-intelligence.shinyapps.io/bioflow/>

## Local installation

If you wish to install bioflow locally in your computer in case you have
internet problems you can run the following three lines in your R or R
studio console (make sure you uncomment the lines):

``` r
# devtools::install_github("Breeding-Analytics/bioflow")
# library(bioflow)
# bioflow::run_app()
```

The first line will install bioflow as an r package in your computer.
The second line will call the library/application to the environment.
And the third line will start the application.

## Cloning the repositories to contribute

You can clone the development version of bioflow like this:

1)  Install the dependency packages cgiarBase, cgiarPipeline, cgiarOcs

``` r
# 1) Install the dependency packages
# devtools::install_github("Breeding-Analytics/cgiarBase")
# devtools::install_github("Breeding-Analytics/cgiarPipeline")
# devtools::install_github("Breeding-Analytics/cgiarOcs")
```

2)  Clone the GitHub repository in your computer

``` r
# 2) Clone the repository in your computer
# git clone https://github.com/Breeding-Analytics/bioflow.git
```

Now you can start making changes to the code to later make a pull
request. Let us tell you more how to contribute.

## Contribution process

In this collaborative development model, anyone can fork an existing
repository and push changes to their personal fork. You do not need
permission from the original repository to push to your own fork. The
changes can be merged into the original repository by the project
maintainer. When you open a pull request proposing changes from your
user-owned fork to a branch in the source (upstream) repository, you can
allow anyone with push access to the upstream repository to make changes
to your pull request. This model is popular with open-source projects as
it reduces the amount of friction for new contributors and allows people
to work independently without upfront coordination.

For more details, please check the following guidelines:
<https://docs.github.com/en/get-started/exploring-projects-on-github/contributing-to-a-project>

### Contributing an R function or a shiny module?

If you wish to contribute a function that can be used across modules
(e.g., a function to summarize data) please make your pull request to
the cgiarBase repository.

If you wish to contribute a pipeline in the form of an R function, make
sure that it can use the data structure proposed (an example can be
found calling data(example) in any of the packages) and submit your new
pipeline function to the cgiarPipeline repository.

If you wish to contribute a shiny module please make sure that it can
use the data structure proposed and make your pull request to the
bioflow repository.

### How is a contribution review and accepted?

Priority issues and functionalities will be posted in the confluence
space for internal and external collaborators interested in contributing
(link).

The submitted functions will be tested using a sample of multiple
datasets collected by the different centers to ensure that new functions
and interfaces perform well across a variety of scenarios.

Here are some business rules that need to be followed:

1)  The elements (data frames) in the data structure are fixed and no
    additional tables should be added. The list structure contains the
    following elements:

<!-- -->

1)  data: a list with datasets for raw phenotypes, genotypes, pedigree,
    qtl profile and weather
2)  metadata: a list of datasets specifying the column name mapping of
    the raw datasets and the columns expected by bioflow.
3)  modifications: a list of datasets specifying the modifications that
    should be done to the raw datasets and the columns expected by
    bioflow.
4)  status: a table indicating what module the user has run and the
    timestamp (ID) associated to the run
5)  modeling: a table keeping track of the modeling paramters used
    during the run a given analysis.
6)  metrics: a table to store relevant metrics associated to an analysis
    for reporting purposes.
7)  predictions: a table of predictions for individuals, crosses,
    markers, or haplotypes to be used for decision making or
    visualization.

The data strucure from bioflow and expected columns can be understood by
running the function:

``` r
cgiarBase::create_getData_object()
```

2)  Functions should not be written inside the interface. The functions
    should be stored in the cgiarBase, cgiarGenomics or cgiarPipeline
    packages.

3)  Functions should be documented properly and include examples.

### Types of contributions that will be accepted (check list)

Only contributions that met the following criteria will be accepted:

1)  Functions that contribute to the main goal of bioflow (see scope
    section above).

2)  Functions that enable methods approved by the Quantitative Genetics
    community lead by the Accelerated Breeding Initiative (before EiB).

3)  Functions that are proven better than existing methods, robust
    enough to handle the variability of data encountered across the
    CGIAR (use sample datasets to test your own function).

### Open an issue before submitting a pull-request

For more information about GitHub Issues and Pull Request (PR)
templates, please check the following link:
<https://github.blog/2016-02-17-issue-and-pull-request-templates/>

### When it’s appropriate to follow up?

Within 7 days after a pull request is submitted.
