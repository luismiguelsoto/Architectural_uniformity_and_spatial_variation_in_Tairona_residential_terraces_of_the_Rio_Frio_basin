Architectural uniformity and spatial variation in Tairona residential terraces of the Río Frío basin, Colombia
--------------------------------------------------------------
This repository contains the R code and data used to analyze architectural uniformity and spatial variation among 2,526 residential terraces attributed to the Tairona period (approximately AD 1000 to 1600) in the Río Frío basin (Sierra Nevada de Santa Marta, Colombia), and to examine whether terrace diameter similarity varies with distance, local architectural concentration, and terrain characteristics.

Repository Structure:
----------------------------------
1. Rdata:
   - Contains two spatial datasets stored as sf objects in R data files (WGS 84 / UTM zone 18N, EPSG:32618), a digital elevation model in GeoTIFF format, and the R Markdown file:
     - `AAS_TERRACES.RData`: 2,526 residential terraces attributed to the Tairona period, represented as points at their mapped centers, with four attribute fields.
     - `AAS_POLYGON_SURVEY_RIO_FRIO.RData`: the 52.2 km² full-coverage survey polygon.
     - `DEM_ALOS_PALSAR.tif`: the ALOS PALSAR digital elevation model with 12.5 m cells, used to derive elevation, slope, and relative topographic position.
     - `AAS_RIO_FRIO_2026.Rmd`: the R Markdown file that reproduces the analyses.

2. Data Fields (AAS_TERRACES):
   - Fields used in the analyses:
     - `UTM_East`, `UTM_North`: terrace coordinates (m).
     - `Terr_ID`: unique terrace identifier.
     - `Diam_Terra`: recorded terrace diameter (m).
   - Circular-equivalent terrace area is calculated from recorded diameter (πD²/4). All 2,526 residential terraces are retained in the analyses.

3. R Code File:
   - The R Markdown file (`AAS_RIO_FRIO_2026.Rmd`) contains the code to:
     - a) Load the required packages.
     - b) Read the three spatial datasets directly from GitHub.
     - c) Analyze terrace diameter distributions, dimensional variability, Gini coefficients, nearest-neighbor distances, and local architectural concentration.
     - d) Examine spatial aggregation using inhomogeneous pair correlation functions, global simulation envelopes, and alternative spatial point process models.
     - e) Analyze distance-dependent architectural similarity using normalized mark variograms, conditional variance, covariance, and correlation, with global and geographically restricted random-labeling procedures.
     - f) Derive terrain covariates from the digital elevation model, resampled to a 30 m analytical grid, and evaluate the relationships between terrace diameter, local architectural concentration, and terrain using regression models, spatial block bootstrap intervals, and spatial cross-validation.
     - g) Generate Figures 3 to 8 and Tables 1 and 2 as presented in the manuscript (Figures 1 and 2 are not produced by the code).
     - h) Run the sensitivity analyses reported in the manuscript and generate numerical summaries and a reproducibility audit.
   - The code exports Figures 3 to 8 as PDF files, displays tables and numerical summaries in the RStudio session, and maintains an internal cache of simulation results to reduce computational time during subsequent executions.

Software and Key Package Versions:
----------------------------------
- R version: [R 4.6.1]
- Key R packages used in this project include (with version numbers):
  - sf: version 1.1.3
  - ggplot2: version 4.0.3
  - patchwork: version 1.3.2
  - scales: version 1.4.0
  - knitr: version 1.52
  - spatstat.geom: version 3.8.2
  - spatstat.explore: version 3.8.2
  - spatstat.random: version 3.5.1
  - spatstat.model: version 3.7.2
  - GET: version 1.0.9
  - terra: version 1.9.50
  - ggspatial: version 1.1.11
  - curl: required for downloading datasets directly from GitHub.

Getting Started:
----------------------------------
1. Clone or download this repository.
2. Open the R Markdown file (`AAS_RIO_FRIO_2026.Rmd`) in RStudio.
3. Ensure that you have installed the required R packages and have an active Internet connection; the code reads all three spatial datasets directly from GitHub. If the repository is private, configure a GitHub personal access token through the `GITHUB_PAT` environment variable.
4. Run all chunks from top to bottom (Run All) to reproduce the figures and tables as presented in the manuscript. A fixed random seed (20261110) and deterministic seeds for individual realizations make the simulations reproducible. The primary analyses use 10,000 spatial point pattern simulations, 10,000 random-labeling permutations, and 10,000 bootstrap realizations. The code uses parallel processing, allocating 30 workers by default on a computer with 32 logical processors. Execution time depends on available computational resources and whether previously computed simulation results are available in the internal cache.
5. For any issues, contact the corresponding author.

Manuscript Summary:
----------------------------------
Residential platforms are a prominent feature of Tairona settlements in the Sierra Nevada de Santa Marta, Colombia, but little is known about how their dimensions vary with the distance between structures. This study examines 2,526 residential terraces attributed to the Tairona period (AD 1000 to 1600), documented through a full-coverage survey of 52.2 km² in the Río Frío basin. Spatial analyses assess whether neighboring terraces resemble one another in diameter and whether this resemblance is associated with local architectural concentration and terrain. Although 91% of the terraces measure between 8 and 13 m in diameter, their dimensions are more similar among pairs separated by less than 50 m than expected even when geographical differences in diameter distributions are preserved. This resemblance partly reflects a weak positive association between neighboring terrace diameters. Terrace diameter decreases slightly as architectural concentration increases, but concentration and terrain together explain less than 1% of the variation in diameter. Similarity among nearby terraces persists after accounting for both factors and under alternative analytical conditions. These findings are consistent with broadly shared building practices and provide a spatial basis for investigating the transmission of architectural knowledge, although alternative explanations for local resemblance cannot yet be excluded.

For questions or further information, please contact: lms313@pitt.edu
