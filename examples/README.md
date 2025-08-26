# Examples of Rossi Design Philosophy Implementation

This folder provides practical examples of how the **Rossi Design Philosophy (RDP)** has been implemented in various R dataset packages. These examples are designed to support the "Desarrollo de Paquetes en R" course at Universidad de Piura (August 23 - September 20, 2025) and benefit the broader R community. Each example includes the package name, its GitHub URL, its web page (if available).

---

## 1. timeSeriesDataSets
- **Description**: The timeSeriesDataSets package provides a comprehensive collection of time series datasets for R, implementing RDP with systematic suffix naming (e.g., `AirPassengers_ts`, `elecdemand_msts`) .
- **GitHub URL**: [https://github.com/lightbluetitan/timeseriesdatasets_R](https://github.com/lightbluetitan/timeseriesdatasets_R)
- **Web Page**: [https://lightbluetitan.github.io/timeseriesdatasets_R/](https://lightbluetitan.github.io/timeseriesdatasets_R/)

---

## 2. usdatasets
- **Description**: The usdatasets package provides a diverse collection of U.S.-exclusive datasets, encompassing various fields such as crime, economics, education, finance, energy, implementing RDP with systematic suffix naming (e.g., `births14_tbl_df`, `USArrests_df`) .
- **GitHub URL**: [https://github.com/lightbluetitan/usdatasets](https://github.com/lightbluetitan/usdatasets)
- **Web Page**: [https://lightbluetitan.github.io/usdatasets/](https://lightbluetitan.github.io/usdatasets/)

---

## 3. crimedatasets
- **Description**: The crimedatasets package provides a comprehensive collection of datasets exclusively focused on crimes, criminal activities, and related topics., implementing RDP with systematic suffix naming (e.g., `sentencing_sf`, `vehiclethefts_tbl_df`) .
- **GitHub URL**: [https://github.com/lightbluetitan/crimedatasets](https://github.com/lightbluetitan/crimedatasets)
- **Web Page**: [https://lightbluetitan.github.io/crimedatasets/](https://lightbluetitan.github.io/crimedatasets/)

---

## 4. educationR
- **Description**: The educationR package provides a comprehensive collection of datasets related to education, covering topics such as student performance, learning methods, test scores, absenteeism, and other educational metrics, implementing RDP with systematic suffix naming (e.g., `Homework_tbl_df`, `UCBAdmissions_table`) .
- **GitHub URL**: [https://github.com/lightbluetitan/educationr](https://github.com/lightbluetitan/educationr)
- **Web Page**: [https://lightbluetitan.github.io/educationr/](https://lightbluetitan.github.io/educationr/)

---

## 5. MedDataSets
- **Description**: The MedDataSets package provides a comprehensive collection of datasets related to medicine, diseases, treatments, drugs, and public health, implementing RDP with systematic suffix naming (e.g., `Aids2_df`, `fdeaths_ts`) .
- **GitHub URL**: [https://github.com/lightbluetitan/meddatasets](https://github.com/lightbluetitan/meddatasets)
- **Web Page**: [https://lightbluetitan.github.io/meddatasets/](https://lightbluetitan.github.io/meddatasets/)

---

## 6. ColombiAPI
- **Description**: The ColombiAPI package provides a seamless interface to access diverse public data about Colombia through the API-Colombia, a RESTful API, implementing RDP with systematic suffix naming (e.g., `Bogota_airstations_df`, `Bogota_holidays_Date`). It also includes the helper function `view_datasets()` to explore available datasets.
- **GitHub URL**: [https://github.com/lightbluetitan/colombiapi](https://github.com/lightbluetitan/colombiapi)
- **Web Page**: [https://lightbluetitan.github.io/colombiapi/](https://lightbluetitan.github.io/colombiapi/)

---

## 7. MexicoDataAPI
- **Description**: The MexicoDataAPI package provides a unified interface to access open data from the World Bank API and the REST Countries API, with a focus on Mexico, implementing RDP with systematic suffix naming (e.g., `mexico_elections_df`, `mexico_abb_chr`). It also includes the helper function `view_datasets_MexicoDataAPI()` to explore available datasets.
- **GitHub URL**: [https://github.com/lightbluetitan/mexicodataapi](https://github.com/lightbluetitan/mexicodataapi)
- **Web Page**: [https://lightbluetitan.github.io/mexicodataapi/](https://lightbluetitan.github.io/mexicodataapi/)

---

## 8. ChileDataAPI
- **Description**: The ChileDataAPI package provides a unified interface to access open data from the FINDIC API and the REST Countries API, with a focus on Chile, implementing RDP with systematic suffix naming (e.g., `chile_earthquakes_tbl_df`, `malleco_tree_rings_ts`). It also includes the helper function `view_datasets_ChileDataAPI()` to explore available datasets.
- **GitHub URL**: [https://github.com/lightbluetitan/chiledataapi](https://github.com/lightbluetitan/chiledataapi)
- **Web Page**: [https://lightbluetitan.github.io/chiledataapi/](https://lightbluetitan.github.io/chiledataapi/)

---

## 9. infectiousR
- **Description**: The infectiousR package provides a seamless interface to access real-time data on infectious diseases through the disease.sh API, a RESTful API offering global health statistics, implementing RDP with systematic suffix naming (e.g., `china_dengue_tbl_df`, `nfluenza_vax_survey_df`). It also includes the helper function `view_datasets_infectiousR()` to explore available datasets.
- **GitHub URL**: [https://github.com/lightbluetitan/infectiousr](https://github.com/lightbluetitan/infectiousr)
- **Web Page**: [https://lightbluetitan.github.io/infectiousr/](https://lightbluetitan.github.io/infectiousr/)




---

## Notes on RDP Application
The Rossi Design Philosophy is a recent proposal (2025), and the packages listed above were developed and are maintained by the same author, Renzo Caceres Rossi. As such, you will not find the `METHODOLOGY.md` file or any formal attribution to the RDP in these packages, as they predate the formalization of the attribution process. However, they embody the RDP principles in practice.

In future updates to this repository or this file, we will highlight packages—whether by the author or other developers—that formally adopt the RDP with attributions (e.g., via `METHODOLOGY.md` or a note in `DESCRIPTION`). Attribution is **not required** and **not requested**; it is merely **recommended** and left to the free choice of each developer. Our goal is to encourage widespread adoption of the RDP within the R ecosystem, and we welcome its use with or without attribution.

---

## How to Use These Examples
- **For the Course**: Students can study these implementations to apply RDP principles to their own CRAN packages, gaining hands-on experience with suffix naming, discovery functions, and documentation.
- **For the Community**: Developers are encouraged to adapt these examples. Optionally, you may attribute the RDP using the [templates/METHODOLOGY.md](https://github.com/lightbluetitan/rossi-design-philosophy/tree/main/templates/METHODOLOGY.md) template, though this is not required.

---

## Contributing
If you have implemented the RDP in your package, consider sharing an example here! Submit a pull request with:
- Package name, GitHub URL, and web page.
- A brief description of the RDP implementation.

See [Contact and Contributions](https://github.com/lightbluetitan/rossi-design-philosophy/blob/main/docs/ROSSI_DESIGN_PHILOSOPHY.md#contact-and-contributions) for details.