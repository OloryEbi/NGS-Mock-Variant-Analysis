# NGS Variant Filtration, Classification and Validation Pipeline
A rule-based genomic variant analysis pipeline designed for somatic variant prioritization, classification validation and quality control in cancer bioinformatics workflows.  


![Untitled Diagram](https://github.com/user-attachments/assets/ce221e5d-7b1c-41f2-b944-b7e6fa45f33c)


> The image represents the key pillars of the project - (Genomics, Bioinformatics, Clinical Focus and Research), through clear icons and labels. It visually reflects the project's aim: developing an automated NGS somatic variant analysis pipeline for cancer genomics, integrating molecular data with clinical and computational insights.

# Project Overview
This project provides a robust, automated pipeline for Next-Generation Sequencing (NGS) somatic variant filtration, classification and validation. Built for clinical genomics, cancer research and precision medicine applications, the pipeline processes annotated variant data from cancer panels to ensure high-confidence somatic variant detection.

The project consists of two main modules:  

**1. Filtration and Classification:** This contains robust filtration and classification of genomic variants from Next-Generation Sequencing (NGS) data. The script applies a rule-based approach that integrates technical quality metrics, population frequency data, variant type differentiation, gene-specific biological relevance, and cancer-specific annotations (e.g., COSMIC scores). It supports the processing of large variant datasets (VCF-derived CSV files), automatically computes variant properties (e.g., length) and assigns clinical review statuses based on predefined logic. The output includes a master annotated variant file as well as multiple focused reports to support downstream analysis, variant interpretation, and reporting in clinical and translational research settings.  

**2. Variant Validation:** This contains quality control validation of genomic variant classifications by comparing technical and biological/clinical classification outputs. The script loads annotated variant data, applies rule-based logic to assess agreement between technical status and biological retention/discard decisions and identifies classification mismatches such as false positives and false negatives. It generates detailed reports highlighting concordant variants and those requiring further manual review, alongside summary statistics for validation performance. This tool helps improve confidence in variant filtration pipelines and supports rigorous variant interpretation in research and clinical genomics workflows.

## Key Funtionalities
**1. Filtration and Classification:** This pipeline applies priority-based logic to systematically classify somatic variants using biological and technical criteria, ensuring high-confidence interpretation for cancer genomics applications.  

**Core Annotation Criteria:**
- **Variant Caller Metrics:** Integrates counts from Mutect2 and Pindel
- **Population Frequency:** Filters based on gnomAD allele frequency (AF)
- **Cancer-Specific Databases:** Includes COSMIC haem annotations
- **Variant Quality Metrics:** Uses VAF, read depth, and FILTER status
- **Gene-Specific Rules:** Special handling for key genes (e.g., CHEK2, ASXL1, KMT2C, ARID1A, FLT3)
- **Structural Variant Types:** Supports substitutions, insertions, deletions, and indels

**Filtration Logic:** Implements seven prioritized rules to:  
- Discard common polymorphisms and likely benign variants
- Flag low-confidence or subclonal variants
- Prioritize likely pathogenic somatic mutations  
- Applies 7 sequential filtration rules based on quality, gene context, frequency and variant type

**2. Variant Validation and Quality Assurance:** Ensures classification consistency between technical and biological variant statuses to maintain reliability in downstream analysis.  

**Validation Checks:**  
- Compares technical_status (valid / discarded) with retain_discard (Retain / Discard / Unknown)  
- Detects Mismatches indicating potential annotation or interpretation issues  

**Validation Outputs:**  
- Match_rows: Concordant variant classifications  
- Mismatch_rows: Discrepant classifications requiring review  
- This validation step helps maintain data integrity, enhances data quality assurance, particularly for biological reliability, clinical genomics and precision oncology pipelines.

## Results
The pipeline generates structured and interpretable output files tailored to variant classification and validation tasks. All result files are organized and accessible within the results/ directory for reproducibility and easy inspection and this folder contains all:  

- **Excel/CSV files** with variant classification, filtering, and validation outputs  
- **Summary tables** detailing variant counts and classification status  
- **Generated figures** for visualization (e.g., bar charts, variant distribution plots)  

## Interpretation of Results  
**Expected Outputs**  
- **High Match Rate:** Indicates good alignment between technical and clinical filtration  
- **Mismatch Patterns:** May reveal:  
  Gene-specific inconsistencies requiring rule refinement  
  Technical assay limitations affecting variant types  

**Actionable Insights**  
- **Technical Artifacts:** Detect low-quality variants erroneously passing filters  
- **Biological Relevance:** Uncover clinically significant variants being mistakenly discarded  
- **Process Improvements:** Align technical pipelines with biological interpretation workflows  

## Tools and Languages
This pipeline is built for flexibility, speed and reproducibility using:  

- **Language:** Python (v3.9+) Core scripting and logic  
- **Libraries:** pandas, numpy, matplotlib, seaborn, os, argparse  
- **Execution:** Jupyter Notebooks, command-line Python scripts, Excel, notebook    
- **Modular functions:** Easy to extend, adapt or integrate with larger bioinformatics workflows  

## Clinical and Research Applications  
**Quality Control Use Cases**  
- **Pipeline Validation:** Assess concordance between technical and biological filters  
- **Benchmarking:** Compare outcomes from multiple filtration strategies  
- **Auditing:** Detect systematic misclassifications in variant handling  

**Analytical Applications**  
- **Prioritization:** Identify and review discordant variants  
- **Rule Optimization:** Tune thresholds and rules based on mismatches  
- **Annotation Enhancement:** Improve classification systems through iterative insights  

## Data Access
This project was originally developed using a secure dataset containing genomic variant information from *10,000 patients,* provided under strict data governance agreements in line with **UK GDPR (General Data Protection Regulation), Data Protection Act 2018, NHS Confidentiality Guidelines, NHS Digital / UKRI guidance** on pseudonymisation, anonymisation, data minimisation and institutional ethical approvals.  

**Due to patient confidentiality and regulatory restrictions, the original clinical dataset cannot be shared or uploaded to this repository.**  

**Mock Data for Reproducibility**  

**To ensure transparency, reproducibility, and compliance with UK data governance regulations:** All uploaded scripts have been modified to use mock datasets that simulate the structure, data types and filtration logic of the original NHS patient data.  

The following mock datasets are included:  
- **mock_filtration_dataset.csv:** simulates variant filtration and classification data.  
- **mock_validation_rules.csv:** simulates rule-based variant validation logic.  

**All results** (summary tables, Excel/CSV outputs and figures) located in the results/ folder are generated entirely from mock data. **No real patient information** is included in this repository.  

These mock datasets were generated **artificially** based on the schema of the original NHS dataset and are provided strictly for demonstration, testing and methodological sharing purposes and **do not contain any real patient information.**  

**Disclaimer:** The mock data is **not suitable for clinical use** and should not be used for medical or diagnostic decision-making.  

**Data Access Notice:** If you are an authorized researcher, NHS-affiliated collaborator or academic institution interested in reproducing this work with real patient data, please:  
- Contact the appropriate NHS institutional data access committees.  
- Adhere to national and institutional guidelines on patient data use, including NHS Digital, UK GDPR and Health Research Authority (HRA) policies.  

## License

- This project is licensed under the [MIT License](LICENSE).  
- Mock datasets are provided under a [Creative Commons Attribution-NonCommercial 4.0 International License](https://creativecommons.org/licenses/by-nc/4.0/).  

## Contributors

- This project was developed by **Abdulquadri**, as part of an MSc Bioinformatics internship at Leeds Teaching Hospitals NHS Trust under the guidance and supervision of clinical bioinformatics supervisors, mentors and senior colleagues.
- For academic use or questions, feel free to [open an issue](https://github.com/your-repo/issues) or contact via GitHub [github.com/OloryEbi](https://github.com/OloryEbi)

## Acknowledgments

This project was completed as part of my MSc Bioinformatics internship at **Leeds Teaching Hospitals NHS Trust**, in collaboration with **Teesside University, UK**.

I extend my sincere gratitude to my NHS supervisors, mentors and senior colleagues in the **Department of Molecular Biology** and **Clinical Bioinformatics Unit** for their guidance, feedback and professional support throughout the development of this variant analysis and validation pipeline.

Special thanks to the open-source community and data providers whose tools and resources were invaluable to this work:

- **pandas** and the broader *Python community*
- **COSMIC**, **ALARMUT**, **gnomAD**, **TCGA**, and **GDC:*** for publicly available genomic data and reference materials

> **Note:** Mock datasets used in this repository were programmatically generated to mirror the schema of original NHS datasets. **They contain no real patient data** and are provided strictly for testing, demonstration and reproducibility purposes only.
