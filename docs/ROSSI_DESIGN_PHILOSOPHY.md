# The Rossi Design Philosophy: A Systematic Methodology for R Dataset Packages

**Author**: Renzo Caceres Rossi  
**License**: CC BY 4.0 (Creative Commons Attribution 4.0 International)  
**Citation**: Caceres Rossi, R. (2025). The Rossi Design Philosophy: A Systematic Methodology for R Dataset Packages.

---

## Abstract

The Rossi Design Philosophy is a systematic methodology for R dataset package development that enhances usability, transparency, and discoverability. It addresses critical challenges in the R ecosystem where dataset naming conventions are inconsistent and users must manually inspect each dataset to understand its structure and object type. This methodology was developed by Renzo Caceres Rossi and has been successfully implemented across multiple CRAN packages, providing empirical evidence of its effectiveness in improving user experience and package maintainability.

**Keywords**: R packages, dataset design, naming conventions, software methodology, data science

---

## Licensing and Attribution

The Rossi Design Philosophy is licensed under **Creative Commons Attribution 4.0 International (CC BY 4.0)**. You are free to use, share, adapt, and remix this methodology for any purpose, including commercial and educational uses, without restrictions.

**Attribution**: We kindly request that you credit Renzo Caceres Rossi as the creator when using or adapting this philosophy, but this is **optional and not mandatory**. A suggested citation is:  
Caceres Rossi, R. (2025). The Rossi Design Philosophy: A Systematic Methodology for R Dataset Packages.  
**Repository**: https://github.com/lightbluetitan/rossi-design-philosophy

**Optional Attribution File**: Including a `METHODOLOGY.md` file in the root of your package to document adherence to the Rossi Design Philosophy is recommended but **not mandatory**. You may also choose to include attribution in the `DESCRIPTION` file or a vignette, though this is also **optional and not mandatory**. Our primary goal is the widespread adoption of this philosophy within the R ecosystem to improve dataset package development. If you choose not to include attribution, there is no issue—just apply the philosophy and create great packages!

---

## Table of Contents

- [Introduction](#introduction)
- [Core Design Principles](#core-design-principles)
- [Official Suffix Taxonomy](#official-suffix-taxonomy)
- [Implementation Guide](#implementation-guide)
- [Real-World Implementation](#real-world-implementation)
- [Benefits and Impact Analysis](#benefits-and-impact-analysis)
- [Quality Assurance and Testing Framework](#quality-assurance-and-testing-framework)
- [Empirical Validation](#empirical-validation)
- [Adoption Guidelines](#adoption-guidelines)
- [Future Directions and Evolution](#future-directions-and-evolution)
- [License and Attribution](#license-and-attribution)
- [Contact and Contributions](#contact-and-contributions)
- [Appendices](#appendices)

---

## Introduction

### What is the Rossi Design Philosophy?

The Rossi Design Philosophy is a systematic methodology for R dataset package development that enhances usability, transparency, and discoverability. It addresses critical challenges in the R ecosystem where dataset naming conventions are inconsistent and users must manually inspect each dataset to understand its structure and object type.

This methodology was developed by Renzo Caceres Rossi and has been successfully implemented across multiple CRAN packages, providing empirical evidence of its effectiveness in improving user experience and package maintainability.

### Motivation and Problem Statement

Traditional R dataset packages suffer from several usability issues:

- **Ambiguous naming**: Dataset names don't indicate their R object type
- **Inconsistent conventions**: No standardized approach across packages
- **Discovery challenges**: Users must manually explore package contents
- **Documentation gaps**: Type information buried in documentation files

The Rossi Design Philosophy addresses these challenges through systematic design principles.

---

## Core Design Principles

### 1. Structural Transparency Principle

Dataset names **must explicitly indicate their R object type** through standardized suffixes, eliminating ambiguity and reducing cognitive load for users.

```r
# Traditional approach (ambiguous - requires inspection)
data(economic_data)
str(economic_data)  # User must execute this to understand structure

# Rossi Philosophy (transparent - immediately clear)
data(economic_data_tbl_df)  # User knows it's a tibble without inspection
```

**Rationale**: Users should understand the data structure before loading, enabling better workflow planning and reducing errors in downstream analysis.

### 2. Predictive Consistency Principle

All datasets **must follow the standardized pattern** `dataset_name_object_suffix`, creating predictable naming conventions across the entire package ecosystem.

```r
# Consistent implementation across different data types
seoul_air_quality_tbl_df    # Tibble with air quality measurements
korea_provinces_df          # Standard data frame with provincial data
trade_correlation_matrix    # Matrix object with correlation data
survey_responses_list       # List object with structured responses
```

**Rationale**: Predictable patterns reduce learning curves, improve IDE autocompletion, and enable automated analysis tools.

### 3. Enhanced Discoverability Principle

Each package **must include a standardized `view_datasets_packagename()` function** that provides centralized dataset exploration without requiring individual data loading.

```r
# Standardized discovery function
view_datasets_SouthKoreAPIs()  # Lists all available datasets with types
view_datasets_ChinAPIs()       # Shows China-focused datasets
view_datasets_NeuroDataSets()  # Displays neuroscience datasets
```

**Rationale**: Users need efficient ways to explore package contents without loading each dataset individually or parsing documentation files.

### 4. User-Centric Documentation Principle

Dataset documentation **must explicitly state the object type in both the name and description**, ensuring users always know what they're working with.

```r
#' Korean General Social Survey Data
#'
#' This dataset, KoreanSocialSurvey_tbl_df, is a **tibble** containing...
#' The suffix 'tbl_df' indicates that the dataset is a **tibble object**.
```

**Rationale**: Clear, redundant communication about data types prevents user confusion and reduces support burden.

---

## Official Suffix Taxonomy

The Rossi Design Philosophy establishes the following standardized suffixes for R dataset packages:

| Suffix       | R Object Type         | Use Case                        | Example                   |
|--------------|-----------------------|---------------------------------|---------------------------|
| `_df`        | data.frame            | Standard rectangular data       | population_data_df        |
| `_tbl_df`    | tibble                | Modern data frames with enhanced features | air_quality_tbl_df |
| `_matrix`    | matrix                | Mathematical/statistical matrices | correlation_matrix      |
| `_list`      | list                  | Complex nested data structures  | survey_responses_list     |
| `_array`     | array                 | Multi-dimensional arrays        | brain_scan_array          |
| `_sf`        | spatial features (sf) | Geographic/spatial data         | city_boundaries_sf        |
| `_ts`        | time series           | Temporal data with time indexing | gdp_growth_ts           |
| `_xts`       | extensible time series | Advanced time series with metadata | stock_prices_xts      |

---

## Implementation Guide

### Step 1: Apply Systematic Suffixes

Transform traditional naming to Rossi-compliant naming:

```r
# Before: Traditional naming (ambiguous)
korea_population <- data.frame(...)
economic_indicators <- tibble(...)
correlation_data <- matrix(...)

# After: Rossi Philosophy (transparent)
korea_population_df <- data.frame(...)
economic_indicators_tbl_df <- tibble(...)
correlation_data_matrix <- matrix(...)
```

### Step 2: Create the Discovery Function

Every package must include a standardized exploration function following this template:

```r
#' View Available Datasets in [PackageName]
#'
#' This function lists all datasets available in the '[PackageName]' package.
#' If the '[PackageName]' package is not loaded, it stops and shows an error message.
#' If no datasets are available, it returns a message and an empty vector.
#'
#' @return A character vector with the names of the available datasets.
#'         If no datasets are found, it returns an empty character vector.
#' @examples
#' if (requireNamespace("[PackageName]", quietly = TRUE)) {
#'   library([PackageName])
#'   view_datasets_[PackageName]()
#' }
#' @export
view_datasets_[PackageName] <- function() {
  # Check if the package is loaded
  if (!"[PackageName]" %in% .packages()) {
    stop("The '[PackageName]' package must be loaded to view its datasets.")
  }
  
  # Extract dataset information
  datasets_info <- utils::data(package = "[PackageName]")$results
  
  # Check if there are datasets available
  if (nrow(datasets_info) == 0) {
    message("No datasets are currently available in the '[PackageName]' package.")
    return(character(0))
  }
  
  # Extract dataset names
  datasets <- datasets_info[, "Item"]
  
  # Display the message with available datasets
  message("Datasets available in the '[PackageName]' package:")
  
  # Return a vector of datasets without printing to the console
  return(datasets)
}
```

### Step 3: Document with User-Centric Clarity

Documentation must explicitly communicate the data type:

```r
#' Korean Bone Density Measurements
#'
#' This dataset, KoreanBoneDensity_df, is a **data frame** containing bone mass 
#' density measurements of South Korean subjects at three body locations.
#'
#' The suffix '_df' indicates that the dataset is a **data frame object**, 
#' ensuring users immediately understand the data structure before loading.
#'
#' @name KoreanBoneDensity_df
#' @format A data frame with 969 observations and 7 variables:
#' \describe{
#'   \item{Sex}{Sex of the subject (factor with 2 levels)}
#'   \item{Age}{Age of the subject in years (integer)}
#'   ...
#' }
#' @source Data taken from the \pkg{SRMData} package version 1.0.1
#' @usage data(KoreanBoneDensity_df)
"KoreanBoneDensity_df"
```

---

## Real-World Implementation

### SouthKoreAPIs Package Case Study

The SouthKoreAPIs package demonstrates successful implementation of the Rossi Design Philosophy:

```r
# Load package following Rossi Philosophy
library(SouthKoreAPIs)

# Discover available datasets using the standard function
datasets <- view_datasets_SouthKoreAPIs()
# Message output: "Datasets available in the 'SouthKoreAPIs' package:"
# Returns: character vector with dataset names

# View the returned dataset names
print(datasets)
# [1] "AutoOwnershipKorea_df"     "GasSales_Korea_tbl_df"    
# [3] "HeptathlonSeoul1988_df"    "KOSPI200_list"            
# [5] "KPopIdols_tbl_df"          "KoreanBoneDensity_df"     
# [7] "SeoulAdminAreas_sf"        "SolarRadiation_df"        
```

### Dataset Examples from SouthKoreAPIs

The following examples show how the Rossi Design Philosophy is implemented in practice:

| Dataset Name            | Object Type         | Content Description                        |
|-------------------------|---------------------|--------------------------------------------|
| AutoOwnershipKorea_df   | data.frame          | Korean Auto Ownership Data                 |
| GasSales_Korea_tbl_df   | tibble              | Korea Natural Gas Sales with Temperature   |
| KOSPI200_list           | list                | Korea Stock Price Index 200 (KOSPI 200)    |
| SeoulAdminAreas_sf      | spatial features    | Administrative Areas of Seoul, South Korea  |
| KoreanBoneDensity_df    | data.frame          | Bone quality in South Koreans              |

---

## Benefits and Impact Analysis

### For End Users

| Benefit            | Description                                  | Impact Level |
|--------------------|----------------------------------------------|--------------|
| Immediate clarity  | Data type known before loading               | High         |
| Faster workflows   | No time wasted on type inspection            | High         |
| Better planning    | Can prepare appropriate analysis pipelines   | Medium       |
| Reduced errors     | Fewer type-related mistakes                  | High         |

### For Package Developers

| Benefit                  | Description                           | Impact Level |
|--------------------------|---------------------------------------|--------------|
| Clear standards          | Systematic naming guidelines           | High         |
| Consistent decisions     | No arbitrary naming choices           | Medium       |
| Better maintenance       | Predictable package structure          | High         |
| Professional appearance  | Modern, user-focused design           | Medium       |

### For the R Ecosystem

| Benefit                    | Description                           | Impact Level |
|----------------------------|---------------------------------------|--------------|
| Cross-package compatibility | Standardized conventions              | High         |
| Tool development           | Enables automated analysis systems    | High         |
| Educational value          | Clear methodology for teaching        | Medium       |
| Quality improvement        | Raises standards for data packages    | High         |

---

## Quality Assurance and Testing Framework

The Rossi Design Philosophy emphasizes comprehensive testing to ensure package reliability and user experience consistency. This framework covers all aspects of dataset package development with standardized testing approaches.

### Testing the Discovery Function

Every `view_datasets_packagename()` function must include comprehensive tests to validate functionality, user experience, and data integrity.

#### Example Implementation: SouthKoreAPIs Package

**Function Implementation:**

```r
#' View Available Datasets in SouthKoreAPIs
#'
#' This function lists all datasets available in the 'SouthKoreAPIs' package.
#' If the 'SouthKoreAPIs' package is not loaded, it stops and shows an error message.
#' If no datasets are available, it returns a message and an empty vector.
#'
#' @return A character vector with the names of the available datasets.
#'         If no datasets are found, it returns an empty character vector.
#' @examples
#' if (requireNamespace("SouthKoreAPIs", quietly = TRUE)) {
#'   library(SouthKoreAPIs)
#'   view_datasets_SouthKoreAPIs()
#' }
#' @export
view_datasets_SouthKoreAPIs <- function() {
  # Check if the package is loaded
  if (!"SouthKoreAPIs" %in% .packages()) {
    stop("The 'SouthKoreAPIs' package must be loaded to view its datasets.")
  }
  # Extract dataset information
  datasets_info <- utils::data(package = "SouthKoreAPIs")$results
  # Check if there are datasets available
  if (nrow(datasets_info) == 0) {
    message("No datasets are currently available in the 'SouthKoreAPIs' package.")
    return(character(0))
  }
  # Extract dataset names
  datasets <- datasets_info[, "Item"]
  # Display the message with available datasets
  message("Datasets available in the 'SouthKoreAPIs' package:")
  # Return a vector of datasets without printing to the console
  return(datasets)
}
```

**Comprehensive Testing Suite:**

```r
library(testthat)
library(SouthKoreAPIs)

test_that("view_datasets_SouthKoreAPIs works when package is loaded", {
  result <- view_datasets_SouthKoreAPIs()
  expect_type(result, "character")
  expect_true(length(result) > 0)
})

test_that("view_datasets_SouthKoreAPIs prints correct message", {
  output <- capture_messages(view_datasets_SouthKoreAPIs())
  expect_match(
    output[1],
    "Datasets available in the 'SouthKoreAPIs' package:",
    fixed = TRUE
  )
})

test_that("view_datasets_SouthKoreAPIs returns expected datasets", {
  datasets <- view_datasets_SouthKoreAPIs()
  expected_datasets <- c(
    "AutoOwnershipKorea_df",
    "GasSales_Korea_tbl_df",
    "HeptathlonSeoul1988_df",
    "KOSPI200_list",
    "KPopIdols_tbl_df",
    "KoreanBoneDensity_df",
    "KoreanElection2017_df",
    "KoreanSocialSurvey_tbl_df",
    "MERSKorea2015_list",
    "NFIColumnNames_df",
    "RegionalKorea_df",
    "SeoulAdminAreas_sf",
    "SeoulDistrictPop_df",
    "SeoulH3Data_tbl_df",
    "SeoulMosquito_tbl_df",
    "SolarRadiation_df",
    "SouthKoreaBirths_tbl_df",
    "SouthKoreaCovid19_tbl_df",
    "demographicsKR_tbl_df",
    "migrationflows_tbl_df"
  )
  # Check if all expected datasets are present
  missing_datasets <- setdiff(expected_datasets, datasets)
  expect_true(
    length(missing_datasets) == 0,
    info = paste("Missing datasets:", paste(missing_datasets, collapse = ", "))
  )
})
```

### Testing Coverage Areas

The testing framework ensures complete validation of:

1. **Function Behavior**: Correct return types and values
2. **User Experience**: Appropriate messaging and feedback
3. **Data Integrity**: All expected datasets are present and accessible
4. **Error Handling**: Proper responses to edge cases
5. **Naming Compliance**: Suffix consistency across all datasets

### Implementation Workflow

For package developers, the testing process is streamlined through copy-paste templates:

1. **Copy the function template** and replace `[PackageName]` with your package name
2. **Copy the testing suite** and update the expected datasets list
3. **Run tests** to validate implementation
4. **Add methodology attribution** (optional, as described in the Licensing and Attribution section)

### Optional Methodology Attribution File

Developers are encouraged, but not required, to include a `METHODOLOGY.md` file in the package root directory to document adherence to the Rossi Design Philosophy. Below is a suggested template:

```markdown
# Methodology Attribution

This package implements the Rossi Design Philosophy for R dataset packages.

**Methodology License**: CC BY 4.0  
**Created by**: Renzo Caceres Rossi (2025)  
**Repository**: https://github.com/lightbluetitan/rossi-design-philosophy  
**Citation**: Caceres Rossi, R. (2025). The Rossi Design Philosophy: A Systematic Methodology for R Dataset Packages.

## Implementation

This package follows RDP principles including:
- Systematic suffix naming (_df, _tbl_df, _matrix, etc.)
- view_datasets_PackageName() discovery function  
- Transparent object type documentation
```

This attribution is **optional and not mandatory**. Developers may also choose to include attribution in the `DESCRIPTION` file (e.g., "This package follows the Rossi Design Philosophy, Caceres Rossi, 2025"), though this is also **optional**. Our primary goal is the adoption of the Rossi Design Philosophy to enhance the R ecosystem.

---

## Empirical Validation

The Rossi Design Philosophy has been successfully implemented across 20+ CRAN packages created by the methodology's author. These packages demonstrate the gradual evolution and refinement of the design principles across different domains:

### Dataset Packages (Pure Data Collections)

**Medical and Health Sciences:**
- **[neurodatasets](https://lightbluetitan.github.io/neurodatasets/)**: Neurological and brain research datasets
- **[cardiodatasets](https://lightbluetitan.github.io/cardiodatasets/)**: Cardiovascular research data
- **[pulmodatasets](https://lightbluetitan.github.io/pulmodatasets/)**: Pulmonary and respiratory datasets  
- **[meddatasets](https://lightbluetitan.github.io/meddatasets/)**: General medical research data
- **[oncodatasets](https://lightbluetitan.github.io/oncodatasets/)**: Oncology and cancer research datasets
- **[digestivedatasets](https://lightbluetitan.github.io/digestivedatasets/)**: Digestive system research data

**Social and Economic Sciences:**
- **[timeseriesdatasets](https://lightbluetitan.github.io/timeseriesdatasets_R/)**: Time series data collections
- **[usdatasets](https://lightbluetitan.github.io/usdatasets/)**: United States socioeconomic datasets
- **[crimedatasets](https://lightbluetitan.github.io/crimedatasets/)**: Crime and public safety data
- **[educationr](https://lightbluetitan.github.io/educationr/)**: Educational research datasets

### API Packages with Datasets

**Regional Data APIs:**
- **[southkoreapis](https://lightbluetitan.github.io/southkoreapis/)**: South Korea economic and social data APIs
- **[chinapis](https://lightbluetitan.github.io/chinapis/)**: China economic and social data APIs
- **[indiapis](https://lightbluetitan.github.io/indiapis/)**: India socioeconomic data APIs
- **[japanapis](https://lightbluetitan.github.io/japanapis/)**: Japan statistical data APIs

**Latin American Data APIs:**
- **[colombiapi](https://lightbluetitan.github.io/colombiapi/)**: Colombia official statistics APIs
- **[argentinapi](https://lightbluetitan.github.io/argentinapi/)**: Argentina government data APIs
- **[brazildataapi](https://lightbluetitan.github.io/brazildataapi/)**: Brazil statistical data APIs
- **[mexicodataapi](https://lightbluetitan.github.io/mexicodataapi/)**: Mexico official data APIs

### Implementation Evolution

These packages represent the gradual development and refinement of the Rossi Design Philosophy, with earlier packages serving as proof-of-concept implementations and later packages demonstrating mature application of all four core principles. The diversity across medical, social, economic, and regional domains validates the methodology's universal applicability in R dataset package development.

### Educational Validation

Educational validation is currently being conducted through the official **"Desarrollo de Paquetes (Packages) en R"** course offered by the IEEE EMBS chapter at Universidad de Piura (August 23 - September 20, 2025).

#### Course Details

- **Instructor**: Renzo Caceres Rossi (R Specialist, Data Science Research Peru mentor, IEEE and LatinR international conference speaker)
- **Duration**: 4 weeks (August 23 - September 20, 2025)
- **Schedule**: Saturdays and Sundays, 4:00 - 6:00 PM (GMT-5)
- **Modality**: Virtual synchronous sessions
- **Participants**: Students from Peru and Colombia
- **Certification**: Official certificate included

#### Practical Implementation

Students are developing individual R packages following the Rossi Design Philosophy principles, with guaranteed outcomes:

- **Official R publication**: Each student's package will be published on CRAN
- **Global availability**: Packages accessible for worldwide download
- **Professional documentation**: Complete technical documentation following Rossi standards
- **Quality assurance**: Validated and tested packages

This real-world implementation provides empirical evidence of the methodology's effectiveness in educational settings, with students successfully applying all four core principles to create professional-grade R packages.

---

## Adoption Guidelines

### For New Packages

1. **Plan naming from the start** using Rossi principles
2. **Implement the discovery function** as part of core functionality
3. **Document types explicitly** in all dataset descriptions
4. **Test with users** to validate clarity and usability
5. **Optionally include attribution** in `METHODOLOGY.md` or `DESCRIPTION` to acknowledge the Rossi Design Philosophy (not mandatory)

### For Existing Packages

1. **Assess current naming** against Rossi standards
2. **Plan migration strategy** considering backward compatibility
3. **Update documentation** to emphasize data types
4. **Add discovery function** to enhance user experience
5. **Optionally include attribution** in `METHODOLOGY.md` or `DESCRIPTION` (not mandatory)

### Implementation Checklist

| Implementation Step          | Priority | Effort Level | Status |
|-----------------------------|----------|--------------|--------|
| Apply suffix taxonomy       | High     | Low          | ☐      |
| Create view_datasets_*() function | High     | Medium       | ☐      |
| Update documentation         | High     | Medium       | ☐      |
| Add examples                | Medium   | Low          | ☐      |
| Test with users             | High     | Medium       | ☐      |
| Add optional attribution     | Low      | Low          | ☐      |

---

## Future Directions and Evolution

### Planned Enhancements

1. **Extended suffix taxonomy** for specialized data types
2. **IDE integration** with RStudio and VS Code
3. **Automated validation tools** for package developers
4. **Community contribution guidelines** for new suffixes

### Research Opportunities

- **User experience studies** comparing traditional vs. Rossi-compliant packages
- **Adoption pattern analysis** across different R communities
- **Performance impact assessment** of naming conventions on analysis workflows
- **Cross-language applicability** to Python, Julia, and other data science languages

---

## License and Attribution

### License Terms

**License**: This methodology is licensed under **CC BY 4.0** (Creative Commons Attribution 4.0 International License). 

You are free to:

- Share and redistribute in any format
- Adapt, remix, and build upon the methodology
- Use for any purpose, including commercial applications

### Optional Attribution

When implementing, referencing, or building upon the Rossi Design Philosophy, attribution to Renzo Caceres Rossi is appreciated but **not mandatory**. Our primary goal is the adoption of this philosophy to enhance the R ecosystem. Suggested ways to provide attribution include:

#### For Package Documentation (Optional)
> "This package follows the Rossi Design Philosophy for dataset naming and organization. Developed by Renzo Caceres Rossi (2025)."

#### For Academic Citations (Optional)
> Caceres Rossi, R. (2025). The Rossi Design Philosophy: A Systematic Methodology for R Dataset Packages.

#### For Conference Presentations (Optional)
> "Implementation based on the Rossi Design Philosophy by Renzo Caceres Rossi"

#### In the `DESCRIPTION` File (Optional)
> Description: A collection of datasets following the Rossi Design Philosophy for transparent naming and discovery (Caceres Rossi, 2025, CC BY 4.0).

Including a `METHODOLOGY.md` file in the package root is recommended but **not mandatory**. If you choose not to include attribution, there is no issue—just apply the philosophy to create high-quality dataset packages.

---

## Contact and Contributions

**Author**: Renzo Caceres Rossi  
**Email**: arenzocaceresrossi@gmail.com  
**GitHub**: https://github.com/lightbluetitan/rossi-design-philosophy

### Contributing to the Philosophy

The Rossi Design Philosophy continues to evolve based on community feedback and real-world implementations. Contributions, suggestions, and case studies are welcome through the official repository.

### Reporting Issues or Improvements

If you identify areas for improvement or have suggestions for additional suffixes or principles, please contribute through the established channels.

---

## Appendices

### Appendix A: Complete Function Template

```r
# Complete template for implementing Rossi Design Philosophy
# Replace [PackageName] with your actual package name

#' View Available Datasets in [PackageName]
#'
#' This function lists all datasets available in the '[PackageName]' package.
#' If the '[PackageName]' package is not loaded, it stops and shows an error message.
#' If no datasets are available, it returns a message and an empty vector.
#'
#' @return A character vector with the names of the available datasets.
#'         If no datasets are found, it returns an empty character vector.
#' @examples
#' if (requireNamespace("[PackageName]", quietly = TRUE)) {
#'   library([PackageName])
#'   view_datasets_[PackageName]()
#' }
#' @export
view_datasets_[PackageName] <- function() {
  # Check if the package is loaded
  if (!"[PackageName]" %in% .packages()) {
    stop("The '[PackageName]' package must be loaded to view its datasets.")
  }
  
  # Extract dataset information
  datasets_info <- utils::data(package = "[PackageName]")$results
  
  # Check if there are datasets available
  if (nrow(datasets_info) == 0) {
    message("No datasets are currently available in the '[PackageName]' package.")
    return(character(0))
  }
  
  # Extract dataset names
  datasets <- datasets_info[, "Item"]
  
  # Display the message with available datasets
  message("Datasets available in the '[PackageName]' package:")
  
  # Return a vector of datasets without printing to the console
  return(datasets)
}
```

### Appendix B: Documentation Template

```r
#' [Dataset Title]
#'
#' This dataset, [dataset_name_suffix], is a **[object type]** containing [description].
#'
#' The suffix '[suffix]' indicates that the dataset is a **[object type] object**, 
#' ensuring users immediately understand the data structure before loading.
#'
#' @name [dataset_name_suffix]
#' @format A [object type] with [n] observations and [p] variables:
#' \describe{
#'   \item{variable1}{Description of variable1}
#'   \item{variable2}{Description of variable2}
#'   ...
#' }
#' @source [Original data source]
#' @usage data([dataset_name_suffix])
"[dataset_name_suffix]"
```

---

**Note on Attribution**: The CC BY 4.0 license ensures that Renzo Caceres Rossi receives appropriate credit as the creator of this methodology while allowing maximum freedom for community adoption and adaptation. Including attribution in `METHODOLOGY.md`, `DESCRIPTION`, or elsewhere is appreciated but **not mandatory**, as our primary goal is the widespread adoption of the Rossi Design Philosophy to enhance the R ecosystem.

**Version**: 1.0  
**Last Updated**: 2025  
**Status**: Active development and community adoption