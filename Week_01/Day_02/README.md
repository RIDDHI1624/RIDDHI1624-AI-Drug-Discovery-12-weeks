
# Week 1 — Day 2: Molecular Similarity and EGFR Scaffold Analysis

## Objective
Analyze molecular similarity, substructures, and scaffold diversity using RDKit and experimental EGFR bioactivity data from ChEMBL.

## Topics Covered
- Morgan fingerprints and Tanimoto similarity
- SMILES and SMARTS
- Substructure searching
- Functional group identification
- Bemis-Murcko scaffold analysis
- IC50 measurements and assay comparisons
- Structure-activity relationships (SAR)

## Biological Target
- Target: Human EGFR
- ChEMBL Target ID: CHEMBL203
- Selected Assay: CHEMBL677833
- Activity Threshold: IC50 <= 1000 nM

## Dataset
- Initial activity records: 100
- Unique molecules in initial sample: 82
- Records from selected assay: 16
- Selected active molecules: 12
- Invalid molecular structures: 0

## Results
- Unique Bemis-Murcko scaffolds: 4
- Dominant scaffold: 8 molecules (66.67%)
- Dominant scaffold median IC50: 72 nM
- Dominant scaffold IC50 range: 11-1000 nM

## Key Findings
The selected EGFR compounds are dominated by one molecular scaffold.

Compounds sharing the same scaffold can have substantially different IC50 values.

These findings provide a foundation for further structure-activity relationship analysis.

## Limitations
- Small, non-random dataset
- One selected EGFR assay
- Activity threshold chosen for educational analysis
- Findings cannot be generalized to all EGFR inhibitors

## Tools
Python, RDKit, ChEMBL, Pandas, NumPy, and Matplotlib.
