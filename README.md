# Exoplanet Stellar Analysis

## Project Overview

**Exoplanet Stellar Analysis** is a DA220 data analysis project titled **"Exoplanets and Stars."** The project uses data from the NASA Exoplanet Archive to investigate how host-star properties relate to exoplanet characteristics.

The project focuses on stellar mass, stellar radius, stellar effective temperature, stellar luminosity, planet mass, planet equilibrium temperature, planet radius, and discovery method. The rendered report documents an analytical subset of **869 exoplanets** for the multiple regression model, while the included `Data.csv` file is a broader NASA archive export containing additional records and variables.

The analysis combines exploratory visualization, hypothesis testing, correlation analysis, and regression modeling to connect statistical patterns with astronomy and astrophysics context.

## Live Demo

https://aniketgauba67.github.io/exoplanet-stellar-analysis/

This repository is prepared for GitHub Pages deployment from the `main` branch using the repository root (`/(root)`) as the publishing source. The root-level [`index.html`](index.html) file is the public entry point for the rendered report.

### GitHub Pages Deployment

1. Push the latest repository changes to GitHub.
2. In GitHub, open **Settings > Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
4. Set **Branch** to `main` and the folder to `/(root)`.
5. Save the settings and wait for GitHub Pages to publish the site.

The public site should then be available at:

```text
https://aniketgauba67.github.io/exoplanet-stellar-analysis/
```

### Updating or Rebuilding the Report

The original rendered report is preserved at [`DA220 Project/DA220Project.html`](DA220%20Project/DA220Project.html). To update the public site after regenerating the report:

1. Replace `DA220 Project/DA220Project.html` and any regenerated files in `DA220 Project/images/`.
2. Copy the updated report to the root as `index.html`.
3. Copy the updated image assets to the root-level `images/` folder.
4. Confirm that all HTML asset references use relative paths such as `images/image1.png`.
5. Commit and push the changes to `main`; GitHub Pages will redeploy automatically.

## Research Questions

1. **How are stellar properties correlated?**  
   The project examines relationships among stellar mass, temperature, radius, and luminosity, including an HR diagram and a mass-radius visualization.

2. **How does exoplanet equilibrium temperature relate to stellar mass and luminosity?**  
   A multiple linear regression model evaluates whether stellar mass and log-scale luminosity help explain variation in planet equilibrium temperature.

3. **Do planets discovered by Imaging vs. Radial Velocity differ significantly in mass?**  
   A Welch two-sample t-test compares planet masses between these discovery methods.

## Dataset

The dataset comes from the **NASA Exoplanet Archive**, specifically the planetary systems composite-style variables used in the report. The repository includes the data file as [`Data.csv`](Data.csv).

| Variable | Description |
| --- | --- |
| `pl_name` | Planet name |
| `hostname` | Host star name |
| `discoverymethod` | Method used to discover the planet |
| `disc_year` | Discovery year |
| `pl_rade` | Planet radius in Earth radii |
| `pl_bmasse` | Planet mass in Earth masses |
| `pl_dens` | Planet density |
| `pl_eqt` | Planet equilibrium temperature |
| `st_spectype` | Stellar spectral type |
| `st_teff` | Stellar effective temperature |
| `st_rad` | Stellar radius |
| `st_mass` | Stellar mass |
| `st_lum` | Stellar luminosity |
| `sy_dist` | System distance |

### Cleaning and Preprocessing

The report describes preprocessing in R with `dplyr` and `tidyverse`, including:

- Renaming columns to analysis-friendly names.
- Selecting variables relevant to the stellar and planetary research questions.
- Extracting the first character of `st_spectype` to group stars by spectral class.
- Filtering or omitting missing values for analyses that require complete variables.
- Grouping stellar mass and planet size into categories for the chi-square test.
- Using log-scale stellar luminosity in the equilibrium temperature regression.

Because the repository currently contains rendered report outputs rather than the original `.R`, `.Rmd`, or `.qmd` source file, the exact filtering sequence should be interpreted from the report and output tables.

## Methods Used

| Method | Purpose |
| --- | --- |
| Data wrangling with R, `dplyr`, and `tidyverse` | Clean, select, rename, and transform NASA archive variables |
| HR diagram visualization | Plot stellar luminosity against stellar temperature, colored by spectral type |
| Stellar mass vs. radius plot | Visualize the positive relationship between star size and mass |
| Correlation matrix | Quantify relationships among stellar temperature, mass, radius, and luminosity |
| Welch two-sample t-test | Compare planet mass for Imaging vs. Radial Velocity discoveries |
| Chi-square test | Test association between stellar mass group and planet size category |
| Multiple linear regression | Model planet equilibrium temperature using stellar mass and luminosity |
| Regression diagnostics | Assess residual behavior, normality, scale-location, and leverage |

## Key Findings

- **Discovery method matters:** Imaging-discovered exoplanets had significantly higher planet masses than Radial Velocity planets in the Welch two-sample t-test.
- **Stellar variables were strongly correlated:** Stellar temperature, mass, radius, and luminosity all showed positive correlations. The report identifies stellar temperature and stellar mass as the strongest relationship, with `r = 0.90`.
- **Planet size was associated with stellar mass group:** The chi-square test reported a significant association between stellar mass category and planet size category (`chi-square = 53.5`, `df = 4`, `p < 0.001`).
- **Equilibrium temperature was modeled from stellar properties:** The multiple regression model used stellar mass and stellar luminosity to model planet equilibrium temperature, reporting `R^2 = 0.474` across 869 observations.
- **Regression interpretation:** The report found positive coefficients for both stellar mass and luminosity, suggesting that hotter equilibrium temperatures are associated with larger stellar mass and luminosity, within the limits of the observational data.

## Visualizations and Outputs

The public GitHub Pages entry point is [`index.html`](index.html). The original rendered report is preserved at [`DA220 Project/DA220Project.html`](DA220%20Project/DA220Project.html). A PDF export is also included as [`DA220 Project 2.13.53 AM.pdf`](DA220%20Project%202.13.53%E2%80%AFAM.pdf), and a Word version is included as [`DA220 Project-1.docx`](DA220%20Project-1.docx).

Generated images are stored in [`DA220 Project/images/`](DA220%20Project/images/). A root-level copy is stored in [`images/`](images/) so `index.html` can load assets correctly when hosted by GitHub Pages.

| Output | File | Description |
| --- | --- | --- |
| Planet size by stellar mass group | `image1.png` | Stacked proportion chart used with the chi-square analysis |
| Stellar correlation table | `image2.png` | Correlation matrix for stellar temperature, mass, radius, and luminosity |
| Regression model table | `image3.png` | Multiple regression output for equilibrium temperature |
| Discovery method boxplot | `image4.png` | Planet mass comparison for Imaging vs. Radial Velocity |
| Introductory exoplanet graphic | `image5.png` | Visual context graphic used near the report introduction |
| Stellar mass-radius plot | `image6.png` | Scatterplot with regression line for stellar radius and mass |
| HR diagram | `image7.gif` | Hertzsprung-Russell diagram of luminosity vs. stellar temperature |
| Regression diagnostics | `image8.png` | Residual and leverage diagnostic plots |

## Repository Structure

```text
.
|-- index.html
|-- images/
|   |-- image1.png
|   |-- image2.png
|   |-- image3.png
|   |-- image4.png
|   |-- image5.png
|   |-- image6.png
|   |-- image7.gif
|   `-- image8.png
|-- favicon.svg
|-- Data.csv
|-- DA220 Project/
|   |-- DA220Project.html
|   `-- images/
|       |-- image1.png
|       |-- image2.png
|       |-- image3.png
|       |-- image4.png
|       |-- image5.png
|       |-- image6.png
|       |-- image7.gif
|       `-- image8.png
|-- DA220 Project 2.13.53 AM.pdf
|-- DA220 Project-1.docx
|-- LICENSE
`-- README.md
```

| Path | Purpose |
| --- | --- |
| `Data.csv` | NASA Exoplanet Archive dataset used for the analysis |
| `index.html` | GitHub Pages entry point for the public static site |
| `images/` | Root-level assets used by `index.html` on GitHub Pages |
| `favicon.svg` | Lightweight static favicon for the public site |
| `DA220 Project/DA220Project.html` | Rendered HTML report for the project |
| `DA220 Project/images/` | Generated visualization and model-output images referenced by the HTML report |
| `DA220 Project 2.13.53 AM.pdf` | PDF export of the project report |
| `DA220 Project-1.docx` | Word document version of the report |
| `LICENSE` | MIT License |
| `README.md` | Project documentation |

Note: the repository does not currently include the original R script, R Markdown file, or Quarto source file used to generate the rendered report.

## How to Run or Review the Project

### Option 1: Review the Rendered Report

Open the GitHub Pages-ready HTML report directly in a browser:

```text
index.html
```

The original generated HTML report remains available at `DA220 Project/DA220Project.html`. The PDF and Word exports can also be opened from the repository root.

### Option 2: Explore the Dataset in RStudio

1. Open RStudio.
2. Choose **File > New Project > Existing Directory**.
3. Select this repository folder.
4. Open `Data.csv` or load it in R.
5. Install required packages if needed:

```r
install.packages(c("tidyverse", "dplyr", "ggplot2", "knitr", "rmarkdown"))
```

If using Quarto for a future reproducible report, install Quarto and the R package if needed:

```r
install.packages("quarto")
```

Example dataset loading code:

```r
library(tidyverse)
library(dplyr)
library(ggplot2)

exoplanets <- read.csv("Data.csv")
glimpse(exoplanets)
```

To fully reproduce the rendered report, the original `.R`, `.Rmd`, or `.qmd` analysis source would need to be added to the repository.

## Skills Demonstrated

- Statistical analysis with observational astronomy data
- Data cleaning and preprocessing in R
- Regression modeling and interpretation
- Welch two-sample hypothesis testing
- Chi-square testing for categorical association
- Correlation analysis
- Data visualization with scientific context
- Scientific communication for a technical audience
- Astronomy and astrophysics data interpretation
- Translating statistical results into portfolio-ready conclusions

## Limitations

- The dataset is observational, so results describe associations rather than controlled experimental effects.
- Exoplanet discovery methods have known detection biases; Imaging and Radial Velocity are sensitive to different types of planets.
- Missing values affect which observations can be used in each statistical test or model.
- Correlation does not imply causation.
- Results depend on the variables available in the NASA Exoplanet Archive export.
- The current repository includes rendered report outputs but not the original executable analysis source, limiting full reproducibility from the repository alone.

## Author

**Aniket Gauba**

## License

This project is licensed under the MIT License. See [`LICENSE`](LICENSE) for details.
