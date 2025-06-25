# Hands-On Lesson: Earthquake Location with HypoInverse

## Overview

This lesson will guide you through using the [HypoInverse](https://faldersons.net/Software/Hypoinverse/Hypoinverse.html) program to locate earthquakes from seismic data. You’ll start with a test dataset, then transition to your own research data. By the end, you'll understand how to configure HypoInverse for your local region and interpret location results.

---

## 🛠️ Step-by-Step Instructions

### 1. Download HypoInverse

- Get the binary from:  
  [https://faldersons.net/Software/Hypoinverse/Hypoinverse.html](https://faldersons.net/Software/Hypoinverse/Hypoinverse.html)

### 2. Test the Software

- Utilize the test dataset provided with HypoInverse.
- Run the program to perform a basic earthquake location.

### 3. Read EasyQuake's HypoInverse Wrapper

- Visit the EasyQuake GitHub repository:  
  [easyQuake/easyQuake.py (lines 2358–2661)](https://github.com/jakewalter/easyQuake/blob/master/easyQuake/easyQuake.py#L2358-L2661)
- Read through the function that calls HypoInverse on individual events.
- Understand the expected input/output formats and how integration works.

### 4. Prepare Your Own Dataset

- Use your own research dataset.
- Convert it into the format required by HypoInverse:
  - **Pick files**
  - **Station metadata**
  - **Event headers**, etc.

### 5. Customize the Velocity Model

- Locate a `crh` (control header) file from the EasyQuake repo or other sources.
- Modify it to reflect your **local seismic velocity structure**.

### 6. Run HypoInverse on Your Dataset

- Use the binary and your formatted input files.
- Check output files and verify the quality of the location.

### 7. Modify Configuration Flags

- Review available configuration options in the official documentation:  
  [USGS Open-File Report 02-171 (PDF)](https://pubs.usgs.gov/of/2002/0171/pdf/of02-171.pdf)
- Experiment with different flags and parameters:
  - Phase weightings
  - Velocity options
  - Output formats


### Bonus!

- Get this python package working: [https://github.com/xtyangpsp/HypoInvPy](https://github.com/xtyangpsp/HypoInvPy)
  
---

## Learning Goals

- Understand the structure and function of a local earthquake location algorithm.
- Develop proficiency in preparing seismic data for automated processing.
- Learn to adapt location software to regional geological contexts.
