# Final Project

## Introduction

This is a final project for the [Interacting with Data](https://github.com/Brown-BIOL2430-S04-Fall2015/syllabus) seminar in fall 2015. 

We present an interactive data exploration tool for comparing categories of observations across a high number of different metrics (up to about 10 measurements per observation) inspired by both radar charts and parallel coordinates. An application to population genetics is included. The interactive visualization of comparisons across scenarios of natural selection and across summary statistics for selection can give useful insight into which summary statistics are most useful for inferring different selection scenarios, and how similar or dissimilar aresummary statistics from each other.

View project here: https://rawgit.com/stephenrong/finalproject/master/index.html

## The data

The dataset includes 300 examples each of genomic sites (single nucleotide polymorphisms) evolving under 5 different scenarios of natural selection: neutrally evolving, hard selective sweeps, neutrally linked sites to hard selective sweeps, soft selective sweeps, and neutrally linked sites to soft selective sweeps. These genomic sites were simulated using the population genetic simulator *msms* (Ewing and Hermisson 2010). For each genomic site, 24 different population genetic summary statistics were computed. These summary statistics span multiple genetic patterns expected to be different under selection than under neutrality: site frequency spectrum deviations, linkage disequilibrium, population differentiation, haplotype homozygosity, and integrated haplotype homozygosity. Integrated haplytpe homozygosity statistics were computed using *selscan* (Szpiech and Hernandez 2014). This dataset corresponds to natural selection in the African population of the human demographic model from Gravel et al. (2011). Based on unpublished research work.

## Background

Population geneticists often use summary statistics to test for selection in the genome, and often scan the genome using multiple summary statistics that capture different signals in genetic variation. However, most studies do not distinguish between different scenarios of selection, and individual summary statistics have reduced power to discriminate between different scenarios of selection. Both of these shortcomings can be overcome by combining information from many summary statistics spanning multiple genetic patterns.

Here, we're interested in interactive visualization as a means of gaining insight into the comparisions between different scenarios of selection and comparisons between different summary statistics. Comparing categories of observations based on their distributions in a high number of dimensions is a challenge for visualization, since there are a limited number of dimensions and a limited number of elements on which to map multi-variate measurments. Two previous ways of comparing observations across a high number of individual measurements have inspired the current work

Firstly, radar charts plot multivariate data for a single or multiple categories of observations across axes arranged in a circle. Polygons are drawn connecting the measurements on each axis to create links between the multivariate measurements for each observation, thus creating a continuity between different views of the data (the different axes), while also providing a shape to aid holistic comparisons. Most often, radar charts plot only point observations (e.g. http://bl.ocks.org/nbremer/6506614), however variations such as the radial boxplot can plot distributions with confidence intervals and outliers, such as a periodic time series (e.g. http://bl.ocks.org/davidwclin/ad5d13db260caeffe9b3). 

Secondly, parallel coordinates plot multivariate data for a single or multiple categories of observations across axes arranged in parallel. Lines are drawn connecting measurements on each axis to create links between the multivariate measurements for each observation, thus again creating a continuity between different views of the data (the different axes). In contrast to radar charts, every line between multivariate measurements is draw in parallel coordinate visualizations (e.g. http://bl.ocks.org/mbostock/1341021), or alternatively, in Sankey diagrams, polygons representing continuity between categorical data are drawn (e.g. https://www.jasondavies.com/parallel-sets/).

Here, we take elements from both approaches (radar charts and parallel coordinates) plus small multiples to visualize distributions across scenarios of selection and across symmary statistics. One issue with both radar charts and parallel coordinates we wanted to address is that because the ordering of axes is static and fixed, comparisons between neighboring axes are given the most priority, whereas axes further apart are much harder to compare. In many applications, it would be nice to be able to quickly explore different ordering of axes, by removing or adding axes interactively--this interactive manipulation of axes is the main contribution of this project.

## This project

### Mapping of data to aesthetics

We chose to arrange our axes in parallel as in the parallel coordinate approach. Each axis is given a label, and clicking on an axis removes the axis from our visualization. All unused axes are listed as labels below the visualization, and clicking on any of these labels will add the axis to our visualization from the right. Thus, it is easy to add and remove parallel axes interactively, and the spacing between the axes scales automatically with the number of axes being considered. Here, each axis corresponds to an individual population genetic summary statistic for selection.

The scale of each axis automatically adjusts to the min and max of the associated summary statistic for the axis across all five categories of selection scenarios. Each axis has five parallel plots of the distribution of values of the associated summary statistic for all five categories of selection scenarios. These five parallel plots of points are given just enough spacing to be easy to discriminate visually, yet leave a slim enough vertical profile to ensure that many axes can be viewed together. These small multiples given an intuitive idea of how the summary statistics differ when compared across categories of selection scenarios and also how categories of selection scenarios differ across summary statistics.

Missing values are handled by placing points on a horizontal line below the visualization. This idea came from http://informationandvisualization.de/blog/parallel-coordinates-and-missing-values. A legend explaining the color codings for the five categories of selection scenarios is presented in the top left.

<!---How will aesthetic attributes ( X / Y / color / shape / size /texture / etc ) will be mapped to the data?--->

### Filtering

Following the Visual Information-Seeking Mantra: 

Overview: 24 axes are available in our dataset, split between the axes currently being visualized, and the remaining axes listed as labels below the visualization. Zoom and Filter: When the visualization is opened, 5 axes are visualized. Though there are 24 total axes that can be placed in the visualization, the visualization will only comfortably fit about 10 axes, so there's a limit to how far out the user can zoom. Both local comparisons between neighboring axes can be made, and global comparisons across axes. Details-On-Demand: All the axes can be added and removed, allowing the user to hone in on the comparisons they want to make and see varying views of the dataset. This also means the number of axes being visualized can vary from 1 to 10, allowing varying levels of zoom on the dataset, and thus different degrees of data density. Mouseovers for each datapoint embiggen all the other datapoints corresponding to the same observation, and thus allow for parallel coordinate like comparisons across axes.

<!---Are data filtered? ie in some views are some data not mapped to particular attributes of the image? What is the goal of the filtering?--->

### Extra ink

There is very little extra ink in the visualization. Two choices that were made were to make each data point a circle with wide enough radius and high enough opacity that the range outiers can be easily seen, since the tail distributions are what we are most interested in when we infer natural selection from summary statistic distributions. But these values were chosen as small as still possible to easily see, to minimize data ink and maximize data density--thus, they were chosen to trade-off between data ink + data density vs visual clarity. The missing values line is somewhat redundant, but is useful for reinforcing the observations of missing values, whil offering an aesthetic balance in its horizontal contrast to the otherwise vertical elements of the visualization. Mouseovers for points embiggens corresponding points in the same observatio, and thus uses interaction as a replacement to lines in parallel coordinates.

<!---Are there aesthetic attributes that are not mapped to the data? If so, what purpose do they serve ( redundancy for robustness / improve visual metaphor / but data in context / beauty / etc )?--->

<!---Are any data mapped to more than one aesthetic attribute? Why?--->

### Motion

Transitions are used to ensure continuity between different views of the data based on which axes were being visualized. As we add and remove axes, transitions in the positions of the remaining axes help the user keep track of which axes remain constant from view to view, even as their horizontal positions change to automatically scale to the available space. Thus, motion is used to reinforce the interactivity of adding and removing axes from the visualization.

<!---If motion is used, what purpose does it serve ( metaphor (eg representing motion in real world) / transition continuity between views / etc )--->

### Perspective

All the axes can be removed or added in any order to the visualization, allowing quick changes in views of the data, such as changing which axes comparisons are being made locally and globally, and varying the amount of information being visualized on the graph.

<!---To what extent is perspective (eg mappings) controlled by users vs hard coded in advance? How does this project aid in exploration vs exposition?--->

## Assessment

The visualizing was successful in addressing one of the main limitations of parallel coordinate visualizations and radar charts, that of the static fixedness of the ordering of the axes. By allowing the user to interactively add and remove axes at will, different views of the parallel axes can be explored in real time. Useful insight into the comparisons between categories of selection scenarios and between summary statistics can be gleaned. Mouseover events for points help make parallel comparisons across axes, providing intuition to questions such as are outliers in one summary statistic also outliers in the other summary statistics, does that depend on which summary statistics are being considered, and is ordered rankings of observations preserved across summary statistics?

As discussed above, one limitation of the current visualization is that only marginal distributions are displayed, and another limitation is that measurements are not connected from axis to axis as they would be in a parallel coordinate visualization. The lack of lines between parallel coordinates means that holistic comparisons across axes is not possible, though mouseover events are used for individual comparisons.

<!---Was the new visualization successful at providing insight that was not possible or more difficult with previous approaches?--->

<!---What are the main limitations of new approach?--->

<!---What are future directions this could go in?--->

