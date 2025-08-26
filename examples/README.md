# Examples of Rossi Design Philosophy Implementation

This folder provides practical examples of how the **Rossi Design Philosophy (RDP)** has been implemented in various R dataset packages. These examples are designed to support the "Desarrollo de Paquetes en R" course at Universidad de Piura (August 23 - September 20, 2025) and benefit the broader R community. Each example includes the package name, its GitHub URL, its web page (if available), and illustrative images showing RDP implementation.

---

## 1. timeSeriesDataSets
- **Description**: The timeSeriesDataSets package provides a comprehensive collection of time series datasets for R, implementing RDP with systematic suffix naming (e.g., `AirPassengers_ts`, `elecdemand_msts`) .
- **GitHub URL**: [https://github.com/lightbluetitan/timeseriesdatasets_R](https://github.com/lightbluetitan/timeseriesdatasets_R)
- **Web Page**: [https://lightbluetitan.github.io/timeseriesdatasets_R/](https://lightbluetitan.github.io/timeseriesdatasets_R/)
- **Image**: 
  <center>![timeSeriesDataSets Example](/images/timeseriesdatasets_001.png)</center>
  *Image shows the datasets within timeSeriesDataSets Package with clear suffixes.*

---


## Notes on RDP Application
The Rossi Design Philosophy is a recent proposal (2025), and the packages listed above (SouthKoreAPIs, NeuroDataSets, ArgentinAPI) were developed and are maintained by the same author, Renzo Caceres Rossi. As such, you will not find the `METHODOLOGY.md` file or any formal attribution to the RDP in these packages, as they predate the formalization of the attribution process. However, they embody the RDP principles in practice.

In future updates to this repository or this file, we will highlight packages—whether by the author or other developers—that formally adopt the RDP with attributions (e.g., via `METHODOLOGY.md` or a note in `DESCRIPTION`). Attribution is **not required** and **not requested**; it is merely **recommended** and left to the free choice of each developer. Our goal is to encourage widespread adoption of the RDP within the R ecosystem, and we welcome its use with or without attribution.

---

## How to Use These Examples
- **For the Course**: Students can study these implementations to apply RDP principles to their own CRAN packages, gaining hands-on experience with suffix naming, discovery functions, and documentation.
- **For the Community**: Developers are encouraged to adapt these examples. Optionally, you may attribute the RDP using the [templates/METHODOLOGY.md](https://github.com/lightbluetitan/rossi-design-philosophy/tree/main/templates/METHODOLOGY.md) template, though this is not required.
- **Adding Images**: Images are stored in the [images/ folder](https://github.com/lightbluetitan/rossi-design-philosophy/tree/main/images/). Contribute your own by adding screenshots or diagrams (e.g., `yourpackage_example.png`).

---

## Contributing
If you have implemented the RDP in your package, consider sharing an example here! Submit a pull request with:
- Package name, GitHub URL, and web page.
- An image in the `images/` folder (e.g., `yourpackage_example.png`).
- A brief description of the RDP implementation.

See [Contact and Contributions](https://github.com/lightbluetitan/rossi-design-philosophy/blob/main/docs/ROSSI_DESIGN_PHILOSOPHY.md#contact-and-contributions) for details.