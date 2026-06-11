**FP2-and-Morgan-fingerprint-similarity-for-ligand-analogs**

This repository provides Python scripts for calculating and visualizing chemical similarity between ligand analogs using RDKit. The workflow focuses on comparing compounds against a native ligand (MZB) using:

Morgan Fingerprints (ECFP4)
FP2 (Path-based) Fingerprints
Tanimoto Similarity

**1. Repository Structure**
.
├── fingerprint_similarity.py
├── FP2_similarity_heatmap.py
├── Morgan_similarity_heatmap.py
├── *.sdf
└── README.md

**2. Requirements**
Install dependencies using conda (recommended):

conda create -n chem_similarity python=3.10
conda activate chem_similarity
conda install -c conda-forge rdkit pandas matplotlib seaborn

Or via pip (if RDKit is already installed):
pip install pandas matplotlib seaborn

**3. Input Data**
Place all .sdf files in the same directory as the scripts.
Each .sdf file should contain one molecule.
The native reference ligand must be named:
MZB.sdf

**4. Scripts Overview**
**4.1. fingerprint_similarity.py**
Purpose:
Compute similarity of all ligands against native MZB
Compare Morgan vs FP2
Generate:
Sorted CSV table
Bar plot visualization
Output:
MZB_similarity_comparison_sorted_FP2.csv
Bar plot (Morgan vs FP2 similarity)
Run:
python fingerprint_similarity.py

**4.2. FP2_similarity_heatmap.py**
Purpose:
Compute pairwise similarity between all ligands
Use FP2 (path-based fingerprint)
Generate clustered heatmap
Output:
Clustered similarity heatmap (FP2)
Run:
python FP2_similarity_heatmap.py

**4.3. Morgan_similarity_heatmap.py**
Purpose:
Compute pairwise similarity between all ligands
Use Morgan fingerprints (ECFP4-like)
Generate clustered heatmap
Output:
Clustered similarity heatmap (Morgan)
Run:
python Morgan_similarity_heatmap.py

**5. Methodology**
**Fingerprints Used**
**5.1. Morgan Fingerprint (ECFP4)**
Radius: 2
Bit size: 1024
Captures circular substructures

**5.2. FP2 Fingerprint**
Path-based
Encodes linear fragments

**Similarity Metric**
**5.3. Tanimoto Similarity**
T(A,B)=
A∪B
A∩B
	​
**6. Output Interpretation**
**Similarity score range: 0 → 1**
1.0 → identical structures
> 0.85 → highly similar
0.6–0.85 → moderate similarity
< 0.6 → low similarity
**Heatmaps**
Clustering reveals structural grouping of analogs
Useful for SAR and lead optimization

**7. Notes**
Only the first molecule in each .sdf file is used.
Ensure all structures are:
Valid
Properly sanitized
Missing or invalid molecules will be skipped silently.

🔬 **Use Cases**
Ligand analog screening
Structure–activity relationship (SAR) analysis
Lead optimization workflows
Chemical space clustering
