# Nationwide Register-Based Analysis of Pediatric Antibiotic Prescribing for Acute Otitis Media (Finland, 2017–2022)

**Author:** Janina Hansas  
**Affiliation:** Tampere University  
**Collaborators:** Péter Csonka, Manela Karunadasa-Visama, Pekka Vartiainen, Anna-Leena Vuorinen  

---

## Overview

This repository contains the **analysis pipeline** for a nationwide register‑based cohort study examining **antibiotic prescribing practices for pediatric acute otitis media (AOM)** in Finland between **2017 and 2022**.

The pipeline integrates multiple Finnish national health registers to study:
- antibiotic treatment strategies,
- adherence to national and international treatment guidelines,
- treatment failure,
- and eligibility for tympanostomy tube placement,

with a particular focus on **differences between the public and private health care sectors**.

This repository focuses on **data processing, episode construction, variable derivation, and statistical analysis**, not on sharing register data.

---

## Data Sources

The pipeline is designed to work with pseudonymized individual‑level data from the following statutory Finnish registers:

- **Avohilmo** – Register of Primary Health Care  
- **Hilmo** – Care Register for Health Care (secondary care)  
- **Prescription Centre** – issued and dispensed medications  
- **Digital and Population Data Services Agency (DVV)** – demographic information  
- **Valvira** – physician specialty and registration data  
- **Statistics Finland** – socioeconomic background variables  

All registers cover both public and private health care providers.  
Private sector coverage is partial during the early study period and improves toward the end.

⚠️ **Raw register data are not included in this repository and cannot be shared.**

---

## Study Population

- Children **under 18 years of age**
- Diagnosed with acute otitis media (ICD‑10 codes **H65x–H67x**)
- Study period: **01‑01‑2017 to 31‑12‑2022**

---

## Episode Definition

- An **index visit** marks the start of an AOM episode.
- A **new episode** is defined if ≥30 days have passed since the previous visit.
- A **recurrent visit** within 30 days belongs to the same episode.

The episode construction logic is implemented programmatically to ensure consistency across datasets.

---

## Key Outcomes

The pipeline derives the following main outcomes:

- **Management strategy**  
  - antibiotic prescribed vs no antibiotic

- **Guideline adherence**  
  - first‑line antibiotics (amoxicillin, amoxicillin–clavulanate)  
  - vs non‑first‑line antibiotics

- **Antibiotic treatment strategy**  
  - amoxicillin  
  - amoxicillin–clavulanate  
  - other antibiotics

- **Management failure**  
  - recurrent AOM visit with antibiotic use following an index visit

- **Early management failure**  
  - recurrent AOM visit with antibiotic use following an index visit within 7-days from index visit

- **Antibiotic treatment failure**  
  - recurrent AOM visit with antibiotic use following an index visit with antibiotic prescription

- **Early antibiotic treatment failure**  
  - recurrent AOM visit with antibiotic use following an index visit within 7-days from index visit

- **Eligibility for tympanostomy tube placement**  
  - based on frequency of AOM episodes within guideline‑defined time windows

---

## Covariates

Models adjust for:

- health care sector (public / private)
- age group
- sex
- physician specialty
- season
- native language (proxy for immigration background)
- socioeconomic status
- prior medical conditions (e.g. asthma, atopy, immunological conditions)
- diagnostic subgroup

---

## Statistical Analysis

- All regression analyses are conducted using **mixed‑effects models**
- Random intercept for individual (**1 | FID**) to account for within‑person clustering
- Effect estimates are reported as **odds ratios (ORs) with 95% confidence intervals**

Model selection is supported by large improvements in AIC when random effects are included.

---

## Repository Structure


