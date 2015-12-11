# Final Project

## Introduction

This is a final project for the [Interacting with Data](https://github.com/Brown-BIOL2430-S04-Fall2015/syllabus) seminar in fall 2015. 

We present an interactive data exploration tool for comparing categories of observations across a high number of different metrics (up to about 10 measurements per observation) inspired by both radar charts and parallel coordinates. An application to population genetics is included. The interactive visualization of comparisons across scenarios of natural selection and across summary statistics for selection can give useful insight into which summary statistics are most useful for inferring different selection scenarios, and how similar or dissimilar aresummary statistics from each other.

Clone Git repository to view project.

## The data

The dataset includes 300 examples each of genomic sites (single nucleotide polymorphisms) evolving under 5 different scenarios of natural selection: neutrally evolving, hard selective sweeps, neutrally linked sites to hard selective sweeps, soft selective sweeps, and neutrally linked sites to soft selective sweeps. These genomic sites were simulated using the population genetic simulator *msms* (Ewing and Hermisson 2010). For each genomic site, 24 different population genetic summary statistics were computed. These summary statistics span multiple genetic patterns expected to be different under selection than under neutrality: site frequency spectrum deviations, linkage disequilibrium, population differentiation, haplotype homozygosity, and integrated haplotype homozygosity. Integrated haplytpe homozygosity statistics were computed using *selscan* (Szpiech and Hernandez 2014). This dataset corresponds to natural selection in the African population of the human demographic model from Gravel et al. (2011). Based on unpublished research work.

## Background

Population geneticists often use summary statistics to test for selection in the genome, and often scan the genome using multiple summary statistics that capture different signals in genetic variation. However, most studies do not distinguish between different scenarios of selection, and individual summary statistics have reduced power to discriminate between different scenarios of selection. Both of these shortcomings can be overcome by combining information from many summary statistics spanning multiple genetic patterns.

Here, we're interested in interactive visualization as a means of gaining insight into the comparisions between different scenarios of selection and comparisons between different summary statistics. Comparing categories of observations based on their distributions in a high number of dimensions is a challenge for visualization, since there are a limited number of dimensions and a limited number of elements on which to map multi-variate measurments. Two previous ways of comparing observations across a high number of individual measurements have inspired the current work

Firstly, radar charts plot multivariate data for a single or multiple categories of observations across axes arranged in a circle. Polygons are drawn connecting the measurements on each axis to create links between the multivariate measurements for each observation, thus creating a continuity between different views of the data (the different axes), while also providing a shape to aid holistic comparisons. Most often, radar charts plot only point observations (e.g. http://bl.ocks.org/nbremer/6506614), however variations such as the radial boxplot can plot distributions with confidence intervals and outliers, such as a periodic time series (e.g. http://bl.ocks.org/davidwclin/ad5d13db260caeffe9b3). 

Secondly, parallel coordinates plot multivariate data for a single or multiple categories of observations across axes arranged in parallel. Lines are drawn connecting measurements on each axis to create links between the multivariate measurements for each observation, thus again creating a continuity between different views of the data (the different axes). In contrast to radar charts, every line between multivariate measurements is draw in parallel coordinate visualizations (e.g. http://bl.ocks.org/mbostock/1341021), or alternatively, in Sankey diagrams, polygons representing continuity between categorical data are drawn (e.g. https://www.jasondavies.com/parallel-sets/).

Here, we take elements from both approaches (radar charts and parallel coordinates) to visualize distributions across scenarios of selection and across symmary statistics.

## This project

### Mapping of data to aesthetics



<!---How will aesthetic attributes ( X / Y / color / shape / size /texture / etc ) will be mapped to the data?--->

### Filtering

<!---Are data filtered? ie in some views are some data not mapped to particular attributes of the image? What is the goal of the filtering?--->

### Extra ink

<!---Are there aesthetic attributes that are not mapped to the data? If so, what purpose do they serve ( redundancy for robustness / improve visual metaphor / but data in context / beauty / etc )?--->

<!---Are any data mapped to more than one aesthetic attribute? Why?--->

### Motion

<!---If motion is used, what purpose does it serve ( metaphor (eg representing motion in real world) / transition continuity between views / etc )--->

### Perspective

<!---To what extent is perspective (eg mappings) controlled by users vs hard coded in advance? How does this project aid in exploration vs exposition?--->

## Assessment

<!---Was the new visualization successful at providing insight that was not possible or more difficult with previous approaches?--->

<!---What are the main limitations of new approach?--->

<!---What are future directions this could go in?--->

