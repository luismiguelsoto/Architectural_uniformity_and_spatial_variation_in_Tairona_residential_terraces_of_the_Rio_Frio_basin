Terrace size, proximity, and ceramic type composition in the Río Frío basin, Sierra Nevada de Santa Marta, Colombia
--------------------------------------------------------------

This repository contains the R code and data used to analyze ceramic type composition among the terraces of the Río Frío basin (Sierra Nevada de Santa Marta, Colombia) during the Neguanje, Buritaca, and Tairona phases (approximately AD 100 to 1600), and to test whether that composition varies with terrace size and with proximity between terraces.

Repository Structure:
----------------------------------

1. Rdata:
   - Contains the two datasets, stored as sf objects in R data files (WGS 84 / UTM zone 18N, EPSG:32618), and the R Markdown file:
     • AAS_CERAMICS.RData: 12,058 sherds recorded on 494 terraces, one point per sherd located at its terrace, with 14 attribute fields.
     • AAS_POLYGON_SURVEY_RIO_FRIO.RData: the 52.2 km² full-coverage survey polygon.
     • AAS_RIO_FRIO_2026.Rmd: the R Markdown file that reproduces the analyses.

2. Data Fields (AAS_CERAMICS):
   - Fields used in the analyses:
     • UTM_East, UTM_North: terrace coordinates (m).
     • Period: ceramic phase (Neguanje, Buritaca, or Tairona).
     • Ceramic_ty: ceramic type.
     • Diam_Terra: terrace diameter (m).
   - Additional recorded attributes: Surface_tr, Decoration, Vessel_for, Function, Rim_type, Rim_cm, Core, Production, and Site_type.
   - In the attribute fields, NA means that the attribute is absent from the sherd. The 53 sherds whose preservation prevented phase and type assignment have no Period or Ceramic_ty and are excluded from the models.

3. R Code File:
   - The R Markdown file (AAS_RIO_FRIO_2026.Rmd) contains the code to:
     a) Load the required packages.
     b) Read the two datasets directly from GitHub.
     c) Build terrace-by-type count matrices for each phase.
     d) Fit multinomial, Dirichlet-multinomial, and terrace-class models, with bootstrap intervals and spatial block cross-validation.
     e) Test compositional dissimilarity by distance band and local similarity between neighboring terraces.
     f) Generate Figures 2 to 7 and Tables 1 and 2 as presented in the manuscript (Figure 1, the location map, is not produced by the code).
     g) Run the sensitivity analyses reported in the manuscript, whose results are kept as R objects in the session.
   - The code writes no files; all figures and tables are displayed in the RStudio session.

Software and Key Package Versions:
----------------------------------
- R version: [R 4.6.1]
- Key R packages used in this project include (with version numbers):
     • dplyr: version 1.2.1
     • ggplot2: version 4.0.3
     • knitr: version 1.52
     • sf: version 1.1.3
     • tidyr: version 1.3.2
- Base R packages: grid, parallel, stats, and utils.

Getting Started:
----------------------------------
1. Clone or download this repository.
2. Open the R Markdown file (Rdata/AAS_RIO_FRIO_2026.Rmd) in RStudio.
3. Ensure that you have an active Internet connection; the code reads the datasets directly from GitHub.
4. Run all chunks from top to bottom (Run All) to reproduce the figures and tables as presented in the manuscript. A fixed random seed (20261110) makes the simulations reproducible. The full run takes about six minutes on a computer with 32 logical processors, where it uses 16 parallel workers, and longer on computers with fewer cores.
5. For any issues, contact the corresponding author.

Manuscript Summary:
----------------------------------
Terrace diameter is often read as household investment and proximity as a proxy for interaction, yet neither has been tested against ceramic type composition among terraces of the Río Frío basin, Sierra Nevada de Santa Marta, Colombia. Because many terraces hold few sherds per phase, the 12,005 sherds of the Neguanje, Buritaca, and Tairona phases from 494 terraces were analyzed as counts. In all phases composition varies among terraces beyond sampling expectations, and models that allow this variation predict geographically withheld terraces better than a single shared composition in every partition. Terrace size adds little predictive information, because neither diameter classes nor a model of departure from the median diameter consistently improves the prediction of withheld terraces. Proximity gives a clearer signal, as neighboring terraces are more alike than independent variation allows in every phase. In Neguanje and Tairona, among terraces with at least 10 sherds, those less than 1 km apart are mostly more alike than expected and those 2 to 4 km apart less alike, a pattern that depends partly on particular regions. Occupants of terraces of different sizes thus drew on similar type repertoires, shared most closely with their neighbors, although type proportions alone cannot separate interaction from shared production or chronology.

For questions or further information, please contact: lms313@pitt.edu
