
# Week 1 — Day 1: Cheminformatics Fundamentals

## 1. RDKit and SMILES

RDKit is an open-source Python toolkit for computational chemistry.

SMILES (Simplified Molecular Input Line Entry System) represents chemical structures as text.

Examples:
- Ethanol: CCO
- Propane: CCC
- Ethene: C=C
- Ethyne: C#C
- Benzene: c1ccccc1

RDKit converts SMILES into molecular objects that can be analyzed computationally.

## 2. Atoms, Indices, and Bonds

- Atomic number: Number of protons in an atom.
- Atom index: Position of an atom inside an RDKit molecule, starting at 0.
- Bond: Chemical connection between two atoms.
- Start/end atom indices: Identify the two endpoints of a bond, not a physical direction.

RDKit represents molecules as graphs:
- Atoms = Nodes
- Bonds = Edges

## 3. Molecular Descriptors

Molecular descriptors describe chemical properties numerically.

### Molecular Weight
Sum of the atomic weights of atoms in a molecule.

### LogP
Logarithm of the octanol/water partition coefficient for the neutral molecule.

LogP = log10(C_octanol / C_water)

- Positive LogP: Greater preference for octanol.
- Negative LogP: Greater preference for water.
- High LogP may indicate aqueous solubility challenges.

### TPSA
Topological Polar Surface Area, measured in Å².

- Higher TPSA often makes passive membrane permeability more difficult.
- TPSA around 140 Å² is a commonly used oral-permeability guideline, not an absolute cutoff.
- Lower TPSA often favors passive blood-brain barrier penetration, but cannot guarantee it.

### Hydrogen Bond Donors (HBD)
Groups capable of donating a hydrogen bond, typically involving O-H or N-H bonds.

### Hydrogen Bond Acceptors (HBA)
Atoms with suitable lone electron pairs that can accept hydrogen bonds.

Examples:
- Ethanol: HBD = 1, HBA = 1
- Acetone: HBD = 0, HBA = 1

## 4. Morgan Fingerprints

Morgan fingerprints encode local atomic environments as numerical features.

Our RDKit settings:
- Radius = 2
- Fingerprint size = 2048 bits

A binary fingerprint contains zeros and ones.

For ethanol, the 2048-bit fingerprint contained 6 active bits.

A smaller fingerprint has fewer available positions and may experience more hash collisions.

Changing fingerprint size does not change the actual chemical structure.

## 5. Tanimoto Similarity

Tanimoto similarity compares binary molecular fingerprints.

Formula:

T(A,B) = c / (a + b - c)

Where:
- a = Active bits in fingerprint A
- b = Active bits in fingerprint B
- c = Shared active bits

Our results:
- Ethanol vs Propanol: 0.556
- Ethanol vs Benzene: 0.000

A Tanimoto similarity of 1 means identical bit fingerprints, not necessarily identical molecules.

## 6. ChEMBL Dataset

We retrieved 100 small-molecule records using the ChEMBL Python API.

Data-cleaning results:
- Valid molecules: 100
- Invalid molecules: 0
- Missing SMILES: 0
- Missing descriptors: 0
- Duplicate ChEMBL IDs: 0
- Duplicate SMILES: 0

These were the first 100 returned records, not a random sample of all ChEMBL molecules.

## 7. Experimental Results

- Fingerprint matrix: 100 × 2048
- Mean molecular weight: 399.83 g/mol
- Mean calculated LogP: 3.01
- Mean TPSA: 79.52 Å²
- Molecules with LogP > 5: 14
- Molecules with TPSA > 140 Å²: 3

These results describe only our sampled molecules, not the entire ChEMBL database.

## 8. Research Lesson: Dataset Bias

Reading: Pat Walters, "AI in Drug Discovery — Please Stop Fishing in the Bathtub!"

A model can achieve excellent performance by exploiting dataset construction artifacts rather than learning meaningful chemical or biological relationships.

In DUD-E, molecular fingerprint models can exploit systematic structural differences between active molecules and decoys.

Important principles:
- High ROC-AUC does not prove physical understanding.
- Use carefully designed validation datasets.
- Compare advanced models against simple baselines.
- Check for duplicates, leakage, and sampling bias.
- Never generalize results beyond the evidence.

## 9. Tools Used

Python, Google Colab, RDKit, ChEMBL API, Pandas, NumPy, and Matplotlib.

## 10. Day 1 Outcome

Completed molecular representation, descriptor calculation, fingerprint generation, molecular similarity, ChEMBL retrieval, data validation, and distribution visualization.

All code and results are stored in the Week_01/Day_01 GitHub project folder.
