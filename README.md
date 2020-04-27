# BBMRI BIONIC: Background & Standard Operating Procedures  

This document contains the background information for the BIONIC (BIObanks Netherlands Internet Collective  project) on MDD (major depressive disorder) and next the SOP (standard operating procedures) for performing quality controls and data uploads. 

### Content
1.	Project background
2.	Obtaining an account for the upload server
3.	Phenotype data
4.	Genotype data software download
5.	Genotype data sample quality control
6.	Step-by-step data upload

## Project Background
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

# Guidelines for Sample QC and Data Upload

##### Questions
If you have any questions regarding the steps below, please don’t hesitate to contact Floris Huider at f.huider@vu.nl, who coordinates the current phase of the BIONIC project. For general questions regarding the overarching project, you can contact Mariska Bot at m.bot@ggzingeest.nl. 

In this SOP we assume you have access to a Linux terminal. Please note that if your team is unfamiliar with the software and steps involved in this SOP, one of our team members would happily visit your facility in person to assist in the process. To schedule a meeting day for this, please contact f.huider@vu.nl. 

## Step 1: Obtaining an account for the upload server
In order to transfer the data to the UMCG Genomics Coordination Center cluster, data have to be uploaded to the .sftp server named ‘cheri-ami.hpc.rug.nl’. 

To gain access to this upload server, please follow the following steps:
1.	Generate a private-public key pair as documented here: http://wiki.gcc.rug.nl/wiki/RequestAccount. The private key will serve as your password for connecting to the upload server. 
2.	Send an email (see template below) to the GCC Helpdesk (hpc.helpdesk@umcg.nl) and Floris Huider (f.huider@vu.nl), asking for a guest account to upload your data. In this email, please specify the name of your cohort and ***attach your public key***. One can copy the email template below so that you only have to fill in your cohort’s details.

```
Dear GCC Helpdesk,

I am a collaborating cohort for the BIONIC project with Floris Huider as my contact (cc’d). The name of my cohort is [Cohort Name].

Please provide me with access to:
1. a guest account to the cher-ami SFTP server for three months.

My public key is attached.

Please cc: f.huider@vu.nl in all the correspondence and provide them with access to my guest account.

Best regards,
[Name]
[Institution]
```

You will receive a separate guest account (named umcg-guest[1-15]) that will be used to upload your data files in Step 5. You will only need this account after you have finished your sample QC. While the GCC help desk processes your account request, you can move on to the next sections.

## Step 2: Phenotype Data
Phenotype data can be uploaded in any file format (.txt, .dta, csv, .sav), as long as it contains a variable header and ID column. In addition, please include a codebook that describes the variables and the definition of their values (e.g. sex 1 = male, sex 2 = female). 

For phenotypic data obtained with the LIDAS questionnaire, we request all variables that were included in the LIDAS assessment. For phenotypic data obtained through other means (non-LIDAS), a list of the requested phenotypic variables and their coding can be found in the enclosed document “BIONIC Phenotype data non-LIDAS studies.docx”.

Please note that the individuals in the phenotype data need to be able to be connected to those in the genotype data. In many cases the ID’s in either file will be encrypted for privacy protection purposes. To this end, please make sure the ID’s of the phenotype and genotype data match each other prior to sample cleaning and data upload.

Finally, in assigning control status for individuals that do not meet lifetime MDD criteria, please differentiate between non-screened and screened controls. Screened controls are individuals who do not meet the criteria for lifetime MDD and are also known to not suffer from any comorbid disorders. 

### Before you move on
In the rest of this SOP we assume that you can operate the PLINK software and have basic knowledge on genotype file formats and the Linux terminal. Again, if you are unfamiliar with these tools, do not hesitate to set up a meeting for assistance in the process (f.huider@vu.nl). Since we are all Dutch cohorts, a virtual or physical visit is of no trouble.

## Step 3: Genotype Data Software Download
In this SOP we assume you have access to a Linux terminal, either locally or on a remote cluster you work on, to run the sample QC and data upload commands. If neither are present, a Linux terminal can easily be installed on a Windows operating system:
- https://www.windowscentral.com/install-windows-subsystem-linux-windows-10

 You will need two software to perform the sample quality control: 
- The PLINK toolset (v1.90) 
- The KING software (v2.2.4)

### The PLINK toolset (v1.90) 
Download the Plink .zip file and unzip its contents in the directory that you are going to work in by typing the following in the Linux terminal:
```
#For Linux
wget s3.amazonaws.com/plink1-assets/plink_linux_x86_64_20200219.zip
unzip plink_linux_x86_64_20200219.zip
```

### The KING software (v2.2.4)
Download the ***correct*** .zip file for your system and unzip its contents in the directory that you are going to work in by typing the following in the terminal:
```
#For Linux
wget http://people.virginia.edu/~wc9c/KING/Linux-king.tar.gz
tar -xzvf Linux-king.tar.gz

#For Linux terminal on Windows
wget http://people.virginia.edu/~wc9c/KING/Windows-king.zip
unzip Windows-king.zip
mv king.exe king
```

