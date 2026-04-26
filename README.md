## 🧠 Overview
This repository provides the **raw data**, **chemometric calibration libraries**, and **computational scripts** supporting the study:  

The project establishes an **online Process Analytical Technology (PAT)** framework that integrates a **24-member ssDNA/SWNT nanosensor library** with **multivariate chemometric modeling**, enabling **real-time decoding** of dynamically evolving reactive oxygen and nitrogen species (ROS/RNS) in a **non-equilibrium plasma reactor**.

---

## 📁 Repository Structure

### 1️⃣ `3D chemometric database`
**Purpose:** Calibration datasets for 24 ssDNA/SWNT nanosensors against four key analytes:  
**H₂O₂, OH⁻, NO₂⁻, and NO₃⁻**

**Description:**  
- File indices: `001`–`072`  
- Noise correction: `001, 012, 013, 024, 025, 036, 037, 048, 049, 060, 061, 072`  
- Baseline (no analyte): `002, 014, 026`  
- Lowest analyte conc. (with analyte): `038, 050, 062`  
- Next-lowest conc. (without analyte): `003, 015, 027`  
- Next-lowest conc. (with analyte): `039, 051, 063`  
- Remaining files: higher concentration calibration points  

📊 These datasets form the **3D chemometric fingerprint library**, used to fit Hill model parameters *(a, b, c, n)* for each sensor–analyte pair.  
This database enables quantitative decoding of multivariable optical signals in reactor effluents.  

---

### 2️⃣ `Sensor combination optimization (Off-line, Pyomo)`
**Purpose:** Offline computational optimization of nanosensor subsets.  
Contains **Pyomo-based nonlinear optimization scripts** and intermediate results used to identify the optimal four-sensor combination capable of resolving four analytes simultaneously.  

- Optimization performed via residual minimization (`etotal`)  
- Validation against conventional assay results (H₂O₂ and NO₃⁻)  
- Corresponds to **Figures 2-3** in the manuscript  

🧩 This step bridges the calibration database with predictive modeling and forms the basis for real-time signal decoding.

An example script is provided, allowing users to directly run the chemometric decoding with representative parameters and input data.
---

### 3️⃣ `Sensor signal deconvolution (On-line, FFT+SciPy)`
**Purpose:** Real-time decoding of multi-sensor signals from the **microfluidic multi-optode PAT platform**.  
Includes Python scripts utilizing **FFT-based low-pass filtering** and **SciPy minimization** to extract time-resolved analyte concentrations.  

📈 The processed data correspond to **Figure 5**, illustrating dynamic OH→H₂O₂ and NO₂⁻→NO₃⁻ conversion in the plasma reactor.  
Users can directly reproduce the decoding results by running the script with the provided 30 W time-series txt dataset, covering the full 5 min monitoring duration.
---
