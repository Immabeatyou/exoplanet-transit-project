# Exoplanet Transit Project

This repository contains a Jupyter notebook that analyzes real NASA Kepler light curve data to detect potential exoplanet transits. The project walks through the full workflow used in introductory astrophysics research: data cleaning, detrending, transit detection, period estimation, and physical interpretation.

---

## Project Overview

The goal of this project is to:

- Load and clean Kepler PDCSAP light curve data  
- Detrend the flux using a median filter  
- Identify candidate transit dips  
- Estimate the orbital period using dip spacing and Box Least Squares (BLS)  
- Phase‑fold the light curve  
- Measure transit depth and infer approximate planet radius  

This workflow mirrors the early stages of real exoplanet discovery pipelines.

---

## Repository Contents

- **Exoplanet Transit Project.ipynb**  
  The main notebook containing all code, plots, and analysis steps.
- **Exoplanet Transit Project 2.ipynb**
  The secondary iteration of the project.
  **Exoplanet Transit Project 3.ipynb**
  The tertiary iteration of the project.

  Other iterations will not be listed but will be in the repo.
---

## Methods Summary

### 1. Data Loading  
Kepler long‑cadence FITS files are loaded using `astropy.io.fits`.  
Masked and NaN values are removed to produce clean time and flux arrays.

### 2. Detrending  
A median filter (`scipy.signal.medfilt`) removes long‑term stellar variability.  
Flux is normalized by dividing by the smoothed curve.

### 3. Transit Detection  
Candidate dips are identified using `scipy.signal.find_peaks` on the inverted flux.  
Prominence‑based detection helps isolate meaningful dips from noise.

### 4. Period Estimation  
Two methods are used:
- Dip spacing histogram → rough period guess  
- Box Least Squares (BLS) → precise period refinement  

### 5. Phase Folding  
The light curve is folded on the best‑fit period to reveal the transit shape.

### 6. Physical Interpretation  
Transit depth is used to estimate the planet‑to‑star radius ratio:



\[
\text{depth} \approx \left(\frac{R_p}{R_*}\right)^2
\]



Assuming a Sun‑like star gives a first‑order estimate of planet radius.

---

## Example Results

- **Best‑fit period:** ~0.3879 days (~9.3 hours)  
- **Transit depth:** ~3.9 × 10⁻⁶  
- **Estimated radius:** ~0.22 Earth radii (likely noise rather than a real planet)

The extremely small depth suggests this target is not a strong exoplanet candidate, but the pipeline itself is fully functional and ready for application to known transiting systems.

---

## Dependencies

This project uses:

- Python 3  
- NumPy  
- Matplotlib  
- SciPy  
- Astropy  
- Jupyter Notebook  

Install dependencies with:

```bash
pip install numpy matplotlib scipy astropy jupyter
