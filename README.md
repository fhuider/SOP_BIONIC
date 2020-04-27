# BBMRI BIONIC: Background & Standard Operating Procedures  

This document contains the background information for the BIONIC (BIObanks Netherlands Internet Collective  project) on MDD (major depressive disorder) and next the SOP (standard operating procedures) for performing quality controls and data uploads. 

### Content
1.	Project background
2.	Obtaining an account for the upload server
3.	Phenotype data
4.	Genotype data software download
5.	Genotype data sample quality control
6.	Step-by-step data upload

## 1. Project Background
Cohorts that take part in the BBMRI-NL consortium have agreed to a collaboration on the genetics of MDD, and have worked together in data collection by a standardized instrument (Bot et al. 2017; Fedko et al. 2020). They now wish to collaborate in the genetic association analyses. Additional cohorts with MDD diagnoses have agreed to join the consortium.

#### _What is the BIONIC project?_
In the BIObanks Netherlands Internet Collective (BIONIC) project, Dutch academic institutions and biobanks collaborate in the standardised and harmonised assessment of Major Depressive Disorder, with the aim of uncovering its genetic etiology. In the first phase of the project, our team developed and validated a rapid online DSM 5-based MDD assessment tool which would serve as BIONIC’s main tool for data collection (Bot et al., 2017). In the second phase, Fedko et al. (2020) presented prevalence data and demonstrated the large alignment between estimates of prevalence and heritability found in BIONIC and those of previous MDD efforts. Now, in the third phase, we plan to identify the specific genetic variants associated with MDD in the Dutch population. To this end, we will perform a genome-wide association meta-analysis on the MDD and genotype data from all participating cohorts. We will analyse MDD diagnoses, symptom-specific traits and carry out network analyses in the phenotype data.

#### _Data specifications_
The analyses involve phenotype and genome-wide genotype data:
1.	The phenotype data inform on lifetime Major Depressive Disorder; according to the LIDAS questionnaire or a DSM-based structured interview and covariate data:
    - 	For cohorts that used the LIDAS instrument (e.g. see the supplementary material of: page 16-19).
    - 	For lifetime MDD not measured by the LIDAS, please refer to the enclosed document “BIONIC Phenotype data non-LIDAS studies.docx” for the list of phenotypes and covariates. . 
2.	We ask to upload the genotype data only for MDD cases and controls. The genotype data should be largely unedited, or ‘raw’, apart from having underwent sample QC for which the code is provided below. Please note that the QC protocol described below should be performed on raw genotype data, even if a cleaned dataset is already available from previous QC efforts. This is to ensure that genotype data from each cohort is cleaned in an identical way. The log files containing the number of samples that failed each QC step should be uploaded together with the final sample-cleaned genotype data. In summary, we request:
    - 	Sample QC’ed genotype files in PLINK format (.bim, .bed, .fam) of every individual with lifetime MDD data.
    - 	Log files of the sample QC.

#### _What will happen to the data and who has access?_
Both phenotype and genotype data will be uploaded to the UMCG GCC HPC cluster ‘Gearshift’ using a SFTP protocol, which will ensure secure file transfer from a cohort’s database to the Gearshift cluster. There, the data will be accessible only to a select number of researchers who will conduct the analyses of the mentioned projects. Hence, the data will remain in the Netherlands, and are securely protected from the outside as well as non-affiliated Gearshift cluster users. The receiving party UCMG has set up a DTA conforming to the contemporary GDPR.
Data analyses will be carried out by Floris Huider (VU), Anil Ori (UMCG), Yuri Milaneschi (VUMC). They have provided the information in this document together with Hanna van Loo (UMCG), Brenda Penninx (VUMC), Mariska Bot (VUMC), Jouke Jan Hottenga (VU) and Dorret Boomsma (VU) who will supervise the project.

#### References
Fedko IO, Hottenga JJ, Helmer Q, Mbarek H, Huider F, Amin N, Beulens JW, Bremmer MA, Elders PJ, Galesloot TE, Kiemeney LA, van Loo HM, Picavet HSJ, Rutters F, van der Spek A, van de Wiel AM, van Duijn C, de Geus EJC, Feskens EJM, Hartman CA, Oldehinkel AJ, Smit JH, Verschuren WMM, Penninx BWJH, Boomsma DI, Bot M. Measurement and genetic architecture of lifetime depression in the Netherlands as assessed by LIDAS (Lifetime Depression Assessment Self-report).
_Psychol Med. 2020, 27_:1-10. doi: 10.1017/S0033291720000100
 
Bot M, Middeldorp CM, de Geus EJ, Lau HM, Sinke M, van Nieuwenhuizen B, Smit JH, Boomsma DI, Penninx BW. Validity of LIDAS (LIfetime Depression Assessment Self-report): a self-report online assessment of lifetime major depressive disorder. 
_Psychol Med. 2017, 47(2)_:279-289. doi: 10.1017/S0033291716002312

