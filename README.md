# BBMRI BIONIC: Background & Standard Operating Procedure 
<img align="right" width="120" height="150" src="https://user-images.githubusercontent.com/49392075/80571616-35c42680-89fd-11ea-9900-ef9101291873.jpg">
This document contains the background information for the BIONIC (BIObanks Netherlands Internet Collective) project on the genetics of MDD (Major Depressive Disorder), and the SOP (Standard Operating Procedure) for performing its sample quality control and data upload. 

### Content 
1.	Project background
2.	Obtaining an account for the upload server
3.	Phenotype data
4.	Genotype data software download
5.	Genotype data sample quality control
6.	Step-by-step data upload

## Project Background
Cohorts that take part in the BBMRI-NL consortium have agreed to a collaboration on the genetics of MDD, and have worked together in data collection by a standardized instrument (Bot et al. 2017; Fedko et al. 2020). They now wish to collaborate in the genetic association analyses. Additional cohorts with MDD diagnoses have agreed to join the consortium.
<br/>

#### _What is the BIONIC project?_
In the BIObanks Netherlands Internet Collective (BIONIC) project, Dutch academic institutions and biobanks collaborate in the standardised and harmonised assessment of Major Depressive Disorder, with the aim of uncovering its genetic etiology. In the first phase of the project, our team developed and validated a rapid online DSM 5-based MDD assessment tool (LIDAS) which would serve as BIONIC’s main tool for data collection (Bot et al., 2017). In the second phase, Fedko et al. (2020) presented prevalence data and demonstrated the large alignment between estimates of prevalence and heritability found in BIONIC and those of previous MDD efforts. Now, in the third phase, we plan to identify the specific genetic variants associated with MDD in the Dutch population. To this end, we will perform a genome-wide association meta-analysis on the MDD and genotype data from all participating cohorts. We will analyse MDD diagnoses, symptom-specific traits and carry out network analyses in the phenotype data.

#### _Data specifications_
The analyses involve phenotype and genome-wide genotype data:
1.	The phenotype data inform on lifetime Major Depressive Disorder; according to the LIDAS questionnaire (Bot et al., 2017) or a DSM-based structured interview + covariate data:
    - 	For cohorts that used the LIDAS instrument, please include responses to all items included in the LIDAS questionnaire. For a full list of LIDAS items, see the Supplementary Material of doi.org/10.1017/S0033291720000100, pages 16-19.
    - 	For lifetime MDD not measured by the LIDAS, please refer to the enclosed document “BIONIC Phenotype data non-LIDAS studies.docx” for the list of requested phenotypic variables and covariates.
2.	We ask to upload the genotype data only for MDD cases and controls. The genotype data should be largely unedited, or ‘raw’, apart from having underwent sample QC for which the code is provided below. Please note that the QC protocol described below should be performed on raw genotype data, even if a cleaned dataset is already available from previous QC efforts. This is to ensure that genotype data from each cohort is cleaned in an identical way. The log files containing the number of samples that failed each QC step should be uploaded together with the final sample-cleaned genotype data. In summary, regarding genotype data we request:
    - 	Sample QC’ed genotype files in PLINK format (.bim, .bed, .fam) of every individual with lifetime MDD data.
    - 	Log files of the sample QC.

#### _What will happen to the data and who has access?_
Both phenotype and genotype data will be uploaded to the UMCG GCC HPC cluster ‘Gearshift’ using a SFTP protocol, which will ensure secure file transfer from a cohort’s database to the Gearshift cluster. There, the data will be accessible only to a select number of researchers who will conduct the analyses of the mentioned projects. Hence, the data will remain in the Netherlands, and are securely protected from the outside as well as non-affiliated Gearshift cluster users. The receiving party UCMG has set up a DTA conforming to the contemporary GDPR.
Data analyses will be carried out by Floris Huider (VU), Anil Ori (UMCG) & Yuri Milaneschi (VUMC). They have provided the information in this document together with Hanna van Loo (UMCG), Brenda Penninx (VUMC), Mariska Bot (VUMC), Jouke Jan Hottenga (VU) and Dorret Boomsma (VU), who will supervise the project.

<br/>

#### References
Fedko IO, Hottenga JJ, Helmer Q, Mbarek H, Huider F, Amin N, Beulens JW, Bremmer MA, Elders PJ, Galesloot TE, Kiemeney LA, van Loo HM, Picavet HSJ, Rutters F, van der Spek A, van de Wiel AM, van Duijn C, de Geus EJC, Feskens EJM, Hartman CA, Oldehinkel AJ, Smit JH, Verschuren WMM, Penninx BWJH, Boomsma DI, Bot M. Measurement and genetic architecture of lifetime depression in the Netherlands as assessed by LIDAS (Lifetime Depression Assessment Self-report).
_Psychol Med. 2020, 27_:1-10. doi: 10.1017/S0033291720000100
 
Bot M, Middeldorp CM, de Geus EJ, Lau HM, Sinke M, van Nieuwenhuizen B, Smit JH, Boomsma DI, Penninx BW. Validity of LIDAS (LIfetime Depression Assessment Self-report): a self-report online assessment of lifetime major depressive disorder. 
_Psychol Med. 2017, 47(2)_:279-289. doi: 10.1017/S0033291716002312

<br/>

# Guidelines for Sample QC and Data Upload

#### Questions
If you have any questions regarding the steps below, please don’t hesitate to contact Floris Huider at f.huider@vu.nl, who coordinates the current phase of the BIONIC project. For general questions regarding the overarching project, you can contact Mariska Bot at m.bot@ggzingeest.nl. 

In this SOP we assume you have access to a Linux terminal. Please note that if your team is unfamiliar with the software and steps involved in this SOP, one of our team members would happily visit your facility in person to assist in the process. To schedule a meeting day for this, please contact f.huider@vu.nl. 

<br/>

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

<br/>

## Step 2: Phenotype Data
Phenotype data can be uploaded in any file format (.txt, .dta, csv, .sav), as long as it contains a variable header and ID column. In addition, please include a codebook that describes the variables and the definition of their values (e.g. sex 1 = male, sex 2 = female). 

For phenotypic data obtained with the LIDAS questionnaire, we request all variables that were included in the LIDAS assessment. For phenotypic data obtained through other means (non-LIDAS), a list of the requested phenotypic variables and their coding can be found in the enclosed document “BIONIC Phenotype data non-LIDAS studies.docx”.

Please note that the individuals in the phenotype data need to be able to be connected to those in the genotype data. In many cases the ID’s in either file will be encrypted for privacy protection purposes. To this end, please make sure the ID’s of the phenotype and genotype data match each other prior to sample cleaning and data upload.

Finally, in assigning control status for individuals that do not meet lifetime MDD criteria, please differentiate between non-screened and screened controls. Screened controls are individuals who do not meet the criteria for lifetime MDD and are also known to not suffer from any comorbid disorders. 

### Before you move on
In the rest of this SOP we assume that you can operate the PLINK software and have basic knowledge on genotype file formats and the Linux terminal. Again, if you are unfamiliar with these tools, do not hesitate to set up a meeting for assistance in the process (f.huider@vu.nl). Since we are all Dutch cohorts, a virtual or physical visit is of no trouble.

<br/>

## Step 3: Genotype Data Software Download
In this SOP we assume you have access to a Linux terminal, either locally or on a remote cluster you work on, to run the sample QC and data upload commands. If neither are present, a Linux terminal can easily be installed on a Windows operating system:
- https://www.windowscentral.com/install-windows-subsystem-linux-windows-10

 You will need two software to perform the sample quality control: 
- The [PLINK](http://zzz.bwh.harvard.edu/plink/)  toolset (v1.90) 
- The [KING](http://people.virginia.edu/~wc9c/KING/Download.htm) software (v2.2.4)

### The PLINK toolset (v1.90) 
Download the Plink .zip file and unzip its contents in the directory that you are going to work in by copying the following code to your Linux terminal:
```
#For Linux and/or Linux terminal on Windows:
wget s3.amazonaws.com/plink1-assets/plink_linux_x86_64_20200219.zip
unzip plink_linux_x86_64_20200219.zip
```

### The KING software (v2.2.4)
Download the ***correct*** .zip file for your system and unzip its contents in the directory that you are going to work in by copying the following code to your Linux terminal:
```
#For Linux:
wget http://people.virginia.edu/~wc9c/KING/Linux-king.tar.gz
tar -xzvf Linux-king.tar.gz

#For Linux terminal on Windows:
wget http://people.virginia.edu/~wc9c/KING/Windows-king.zip
unzip Windows-king.zip
mv king.exe king
```
<br/>

## Step 4: Genotype data sample quality control
This is a step-by-step guide that will guide you through the process of sample quality control (QC) on your genotype data. Besides some early file specification, the process largely consists of copy-pasting the QC code that we provide you with below. The entire process will take ~8 hrs, on average. We ask you to perform the sample QC yourselves because:
1)	Cohort labs typically already possess a list of problematic samples and known sample swaps that they can filter out themselves.
2)	Each cohort will likely have access to more genotype data (e.g. parents of participants) than they will actually upload, allowing for additional quality control steps at this stage compared to after data have been uploaded. 

To optimize cleaning efficacy, use the entire genotype dataset for the sample cleaning procedure described below (i.e. do not only use the genotype data of people with phenotype data, but rather use as much genotype data as is available). 

If sample QC has already been performed on the genotype data in the past, we do want to ask you to perform it once more using the steps below, starting with the unedited data as received from the lab. This is to ensure that genotype data from each cohort is cleaned in an identical way. 

Note that if multiple platforms were used in the collection of the data, steps 4.1 - 4.10 should be performed separately for each dataset. 

It is vital that each genotype dataset is based on NCBI build 37 (human genome 19). This is to make sure that SNP names and locations are all based on the same version of the genome. The [LiftOver](https://genome.sph.umich.edu/wiki/LiftOver#Lift_PLINK_format) tool can be used to convert your genotype dataset(s) to the correct build, using either Plink (.map or .bed) or Merlin formatted genotypes as input. 

Please note that Step 4.1, 4.2, 4.3 and 4.10 require manual input from the user. Any section of a line enclosed in square brackets requires manual user input that is specified by the italicized text therein. For example, [_phenotypefile.extension_] should be replaced with the full name of your phenotype file. In contrast, Step 4.4 - 4.9 can be copy-pasted to the terminal without requiring user input. Make sure to copy-paste the entirety of code within a box rather than line-by-line, as to avoid copying only part of a command. Any line preceded by ‘#’ is not run by Linux and can thus be safely copy-pasted along with the actual code.

<br/>

### Step 4.1 - Preparation of genotype data - requires manual user input
The format in which genotype data are returned to investigators varies between genome-wide SNP platforms and genotyping centres. We assume that genotypes have been called by the genotyping centre and returned in the standard .ped and .map file formats. If this is not the case, either look up the conversion procedure for your specific file format or contact Floris Huider at f.huider@vu.nl. 

For the steps below to work, the genotype data should adhere to several criteria:
1)	The genotype dataset already contains family structure in the form of family ID’s, Father ID’s and Mother ID’s (see the example of .fam below).
2)	An individual’s sex is coded male = 1, female = 2, missing = 0.
3)	Samples with multiple measurements (i.e. duplicate samples) have their ID’s suffixed with “_1”, “_2” and  “_3” for the first, second and third measurement, respectively. For example, if Individual 007 of family 12 has been genotyped two times, the their .fam data should look like this:
```
12 007_1 005 006 1 -9
12 007_2 005 006 1 -9
```
Here is an example of what the .ped / .fam file should look like. The six columns represent Family ID, Personal ID, Father ID, Mother ID, Sex, and Phenotype. For sample QC purposes the phenotype can be left missing (-9). Notice the “_1/\_2” suffix for individual 514312341234.
```
123456 514312356789 514319849832 514365747373 2 -9
123457 514312349872 514312345678 514312345679 1 -9
123458 514309380490 514312345680 514312345681 2 -9
123459 0 0 2 -9
123460 514312341234_1 514343214321 514354321543 2 -9
123460 514312341234_2 514343214321 514354321543 2 -9
```
First, use Plink to create the .bed, .bim and .fam files, which are much more computationally efficient than .ped and .map: 1) Open a Linux terminal, and run the lines below to 2) move to the working directory where Plink and King are located, 3) copy-paste the Plink command below to your terminal, and 4) alter the input and output names of your files accordingly. 
-	For your cohort abbreviation, see Table 1. If your cohort is not listed, you may choose an *unused* three-letter abbreviation for your cohort yourself.
-	For your genotype platform, please specify both the brand and version.
-	Example of appropriate genotype data name: NTR_AFFY6.
Note that if your data is already in Plink format, you only have to rename your data to the correct format.

To move to your working directory and convert the .ped & .map files into .bed, .bim, and .fam, run:

<pre>
cd [<i>/local/working/directory/with_PLINK_and_KING/</i>]
./plink --file [<i>/location/raw_GWA_data</i>] --make-bed --out [<i>cohortabbreviation</i>]_[<i>genotypeplatform</i>]
# Example: ./plink --file /home/user/janjansen/genodata/affymetrix_6 --make-bed --out NTR_AFFY6
</pre>

**Table 1**
Cohort | Abbreviation | | Cohort | Abbreviation
------------ | ------------- | ------------- | ------------- | -------------
NTR | NTR | | NESDA | NDA 
Lifelines 1 | LL1 | | Lifelines 2 | LL2
TRAILS | TRS | | TRAILS-CC | TRC
Nijmegen Biomedische Studie | NBS | | NQ plus | NQP
Prediabetes (RELAT-2 & DIRECT) | PRD | | Diabetes (Ketenzorg GWAS) | DKG
ERF | ERF | | Doetinchem Study | DTS
NESDA-sibling | NDS | | MOTAR | MOT
MooDFOOD | MFD | | NESDO | NDO
LASA | LAS | | | 

<br/>

### Step 4.2 - Input File and Parameter specification - requires manual user input

Specify the location and name of your input Plink files for later:
<pre>
RawData=[<i>cohortabbreviation</i>]_[<i>genotypeplatform</i>]
# Example: RawData=NTR_AFFY6
</pre>

Specify the location and name of your phenotype file (Step 2):
<pre>
PhenoData=[<i>/location/of/your/phenodirectory/phenotype_file.extension</i>]
# Example: PhenoData=/home/user/janjansen/bionic/pheno/BIONIC_pheno.sav
</pre>

Assign QC thresholds to parameters using:
```
CP=0.10
HET=0.10
```
Assign the name of the to-be clean file to a parameter using:
```
CLEANFILE=$RawData"_CLN"
```
<br/>

### Step 4.3 - Remove or correct known problems from the genotype file - requires manual user input
In case you have a file that lists the ID’s of samples with known problems, e.g. poor genotyping or sample swaps, those samples should be removed or corrected here. If you don’t have a file or list with known problematic samples, move to Step 4.4.

Rather than trying to manually edit .fam files (which is not advised), create a file that lists the Family ID's and personal ID's of samples that need to be removed, e.g. "problem_ID.txt", and use the following command to remove these samples from the main files:
<pre>
./plink --bfile $RawData --remove [<i>problem_ID.txt</i>] --make-bed --out $RawData"_1" --allow-no-sex
</pre>
To resolve known sample swaps, create a file that lists the old family ID, old personal ID, new family ID and new personal ID per individual. In the command below we use an example file called "swapped_ID.txt" to update the ID's in our main file: 
<pre>
./plink --bfile $RawData"_1" --update-ids [<i>swapped_ID.txt</i>] --make-bed --out $RawData --allow-no-sex
</pre>

<br/>

### Step 4.4 - Remove Duplicate Markers - can be copy-pasted
Remove duplicate markers using:
```
cp $RawData".bed" _D1.bed
cp $RawData".fam" _D1.fam
cat $RawData".bim" | awk '{print $1" "NR" 0 "$4" "$5" "$6}' | awk '{print $1" "$2"_"$1"_"$4" "$3" "$4" "$5" "$6}' > _D1.bim

./plink --bfile _D1 --list-duplicate-vars ids-only suppress-first --out _Duplicate_Marks
./plink --bfile _D1 --exclude _Duplicate_Marks.dupvar --snps-only just-acgt --indiv-sort natural --make-bed --out _D2 		 
mv _Duplicate_Marks.dupvar SNP_Duplicate_Marks.dat
```
<br/>

### Step 4.5 - Sex-check and Chromosome X - can be copy-pasted
Check sex and fix bad HH markers on chromosome X: 
```
let CXmin=$(awk '{if ($1==23) print $4}' _D2.bim | sort -n | head -1)
let CXmax=$(awk '{if ($1==23) print $4}' _D2.bim | sort -n | tail -1)
echo $CXmin $CXmax

if [ $CXmin -lt 2703391 ] ; then
 let CXmin=2703391
fi
if [ $CXmax -gt 154929412 ] ; then
 let CXmax=154929412
fi

./plink --bfile _D2 --chr 23 --from-bp $CXmin --to-bp $CXmax --filter-males --check-sex --out _MCheck --noweb --nonfounders
grep "PROBLEM" _MCheck.sexcheck | awk '{print $1" "$2}' > _Mcheck_sampleproblems.dat
./plink --bfile _D2 --chr 23 --from-bp $CXmin --to-bp $CXmax --filter-males --remove _Mcheck_sampleproblems.dat --make-bed --out _D2_1 --noweb --nonfounders
./plink --bfile _D2_1 --set-hh-missing --geno 0.05 --make-bed --out _D2_2 --nonfounders
cat _D2_1.bim _D2_2.bim | awk '{print $2}' | sort | uniq -c | awk '{if ($1==1) print $2}' > SNP_CX_HET_removed.dat
./plink --bfile _D2 --exclude SNP_CX_HET_removed.dat --make-bed --out _D2_3 --nonfounders

./plink --bfile _D2_3 --chr 23 --from-bp 3000000 --to-bp 154000000 --check-sex --out _CheckSex --noweb --allow-no-sex --nonfounders
grep "PROBLEM" _CheckSex.sexcheck | awk '{if ($3>0) {print $1" "$2}}' > SMP_Sex_Problems.dat
grep "PROBLEM" _CheckSex.sexcheck | awk '{if ($3==0 && $4==0) print $1" "$2" "$4}' >> SMP_Sex_Problems.dat
./plink --bfile _D2_3 --remove SMP_Sex_Problems.dat --make-bed --out _D3 --noweb --allow-no-sex
```

Fix gender of missing samples:
```
grep "PROBLEM" _CheckSex.sexcheck | awk '{if ($3==0 && $4!=0) print $1" "$2" "$4}' > SMP_Fixed_sex.dat
./plink --bfile _D3 --update-sex SMP_Fixed_sex.dat --make-bed --out _D4 --noweb --allow-no-sex
```
<br/>

### Step 4.6 - Check Heterozygosity - can be copy-pasted
Check heterozygosity vs. homozygosity ratio using:
``` 
./plink --bfile _D4 --het --out _Heterozygosity --noweb --allow-no-sex --nonfounders
awk '{if ($6>'$HET') {print $1" "$2}}' _Heterozygosity.het | grep -v "FID" > SMP_Heterozygosity_Problems.dat
awk '{if ($6<-'$HET') {print $1" "$2}}' _Heterozygosity.het | grep -v "FID" >> SMP_Heterozygosity_Problems.dat
./plink --bfile _D4 --remove SMP_Heterozygosity_Problems.dat --make-bed --out _D5 --noweb --allow-no-sex --set-hh-missing
``` 
<br/>

### Step 4.7 - Sample Call Rate - can be copy-pasted
Check call rate in samples using:
```
./plink --bfile _D5 --missing --out _Missing --noweb --allow-no-sex
cat _Missing.imiss | awk '{if ($6>'$CP') {print $1" "$2}}' | grep -v "FID" > SMP_Callrate_Problems.dat
./plink --bfile _D5 --remove SMP_Callrate_Problems.dat --make-bed --out _D6 --noweb --allow-no-sex
```
<br/>

### Step 4.8 - Remove Duplicate Samples - can be copy-pasted
Identify and remove duplicate samples using:
```
./king -b _D6.bed --duplicate --prefix _DuplicateSamples

awk -F_ '{print NF-1" "$0}' _DuplicateSamples.con | awk '{if ($1==4) print $2" "$4}' | sed 's/_/ /g' | awk '{if ($1==$3) print $1"_"$2}' > _Dupes.dat
awk -F_ '{print NF-1" "$0}' _DuplicateSamples.con | awk '{if ($1==4) print $2" "$4}' | sed 's/_/ /g' | awk '{if ($1==$3) print $3"_"$4}' >> _Dupes.dat
sort -u _Dupes.dat > SMP_Real_Duplicates.dat
cat SMP_Real_Duplicates.dat | sed 's/_/ /' | awk 'seen[$1]++' | awk '{print $1"_"$2" "$1"_"$2}' > SMP_Duplicate_Samples_Out.dat
./plink --bfile _D6 --remove SMP_Duplicate_Samples_Out.dat --make-bed --out _D7_1
```

Remove problematic samples - same sample but different DNA - using:
```
cat _D7_1.fam | sed 's/_1 / /g' | sed 's/_2 / /g' | sed 's/_3 / /g' | sed 's/_4 / /g' | sort | uniq -c | awk '{if ($1==2) print $3}' > _2DNAs.dat
grep -f _2DNAs.dat _D7_1.fam | awk '{print $1" "$2}' | sed 's/_/ /g' |  awk 'seen[$1]++' | awk '{print $1"_"$2" "$3"_"$4}' > _2DNAs_remove_1.dat
./plink --bfile _D7_1 --remove _2DNAs_remove_1.dat --make-bed --out _D7
mv _D7.fam _D7.fam_org
cat _D7.fam_org | sed 's/_1 / /g' | sed 's/_2 / /g' | sed 's/_3 / /g' | sed 's/_4 / /g' > _D7.fam
```
<br/>

### Step 4.9 - IBD: Parent-Offspring, Sibling & Half-Sibling Issues - can be copy-pasted
Identify and remove people with multiple (N>1) IBD problems using:
```
./plink --bfile _D7 --chr 1-22 --maf 0.01 --hwe 0.00001 --geno 0.02 --genome rel-check --out _FamIBD1 --allow-no-sex

# Parent-offspring issues
awk '{if ($5=="PO" && $8<0.80) {print $0}}' _FamIBD1.genome > PO_is_Other1.txt

# Sibling issues (includes FS pairs which are HS).
awk '{if ($5=="FS" && $7<0.10) {print $0}}' _FamIBD1.genome > FS_is_Other.tmp
awk '{if ($5=="FS" && $7>0.40) {print $0}}' _FamIBD1.genome >> FS_is_Other.tmp
awk '{if ($5=="FS" && $8<0.35) {print $0}}' _FamIBD1.genome >> FS_is_Other.tmp
awk '{if ($5=="FS" && $8>0.65) {print $0}}' _FamIBD1.genome >> FS_is_Other.tmp
awk '{if ($5=="FS" && $9<0.10) {print $0}}' _FamIBD1.genome >> FS_is_Other.tmp
awk '{if ($5=="FS" && $9>0.40) {print $0}}' _FamIBD1.genome >> FS_is_Other.tmp
awk '{if ($9<0.80) {print $0}}' FS_is_Other.tmp | sort -u > FS_is_Other1.txt
rm FS_is_Other.tmp

# Half-sib issues
awk '{if ($5=="HS" && $7>=0.10 && $7<=0.40 && $8>=0.35 && $8<=0.65 && $9>=0.10 && $9<=0.40) {print $0}}' _FamIBD1.genome > HS_is_Other.tmp
awk '{if ($5=="HS" && $7>=0.80 && $8<=0.20 && $9<=0.20) {print $0}}' _FamIBD1.genome >> HS_is_Other.tmp
awk '{if ($5=="HS" && $8>=0.80) {print $0}}' _FamIBD1.genome >> HS_is_Other.tmp
awk '{if ($5=="HS" && $9>=0.80) {print $0}}' _FamIBD1.genome >> HS_is_Other.tmp
sort -u HS_is_Other.tmp > HS_is_Other1.txt
rm HS_is_Other.tmp

# Issues per sample
awk '{print $1" "$2}' PO_is_Other1.txt > _IBD1_Probs.tmp
awk '{print $3" "$4}' PO_is_Other1.txt >> _IBD1_Probs.tmp
awk '{print $1" "$2}' FS_is_Other1.txt >> _IBD1_Probs.tmp
awk '{print $3" "$4}' FS_is_Other1.txt >> _IBD1_Probs.tmp
awk '{print $1" "$2}' HS_is_Other1.txt >> _IBD1_Probs.tmp
awk '{print $3" "$4}' HS_is_Other1.txt >> _IBD1_Probs.tmp

sort _IBD1_Probs.tmp | uniq -c | awk '{if ($1>1) print $2" "$3}' > _IBD1_Probs.txt
rm _IBD1_Probs.tmp
```
Now see how much is fixed by removing the HIGH count problametics: 
```
./plink --bfile _D7 --remove _IBD1_Probs.txt --chr 1-22 --maf 0.01 --hwe 0.00001 --geno 0.02 --genome rel-check --out _FamIBD2 --allow-no-sex
```

Identify and remove people with one (N=1) IBD problem using:
```
# Parent-offspring issues
awk '{if ($5=="PO" && $8<0.80) {print $0}}' _FamIBD2.genome > PO_is_Other2.txt

# Sibling issues (includes FS pairs which are HS).
awk '{if ($5=="FS" && $7<0.10) {print $0}}' _FamIBD2.genome > FS_is_Other.tmp
awk '{if ($5=="FS" && $7>0.40) {print $0}}' _FamIBD2.genome >> FS_is_Other.tmp
awk '{if ($5=="FS" && $8<0.35) {print $0}}' _FamIBD2.genome >> FS_is_Other.tmp
awk '{if ($5=="FS" && $8>0.65) {print $0}}' _FamIBD2.genome >> FS_is_Other.tmp
awk '{if ($5=="FS" && $9<0.10) {print $0}}' _FamIBD2.genome >> FS_is_Other.tmp
awk '{if ($5=="FS" && $9>0.40) {print $0}}' _FamIBD2.genome >> FS_is_Other.tmp
awk '{if ($9<0.80) {print $0}}' FS_is_Other.tmp | sort -u > FS_is_Other2.txt
rm FS_is_Other.tmp

# Half-sib issues
awk '{if ($5=="HS" && $7>=0.10 && $7<=0.40 && $8>=0.35 && $8<=0.65 && $9>=0.10 && $9<=0.40) {print $0}}' _FamIBD2.genome > HS_is_Other.tmp
awk '{if ($5=="HS" && $7>=0.80 && $8<=0.20 && $9<=0.20) {print $0}}' _FamIBD2.genome >> HS_is_Other.tmp
awk '{if ($5=="HS" && $8>=0.80) {print $0}}' _FamIBD2.genome >> HS_is_Other.tmp
awk '{if ($5=="HS" && $9>=0.80) {print $0}}' _FamIBD2.genome >> HS_is_Other.tmp
sort -u HS_is_Other.tmp > HS_is_Other2.txt
rm HS_is_Other.tmp

# Issues per sample
awk '{print $1" "$2}' PO_is_Other2.txt > _IBD2_Probs.tmp
awk '{print $3" "$4}' PO_is_Other2.txt >> _IBD2_Probs.tmp
awk '{print $1" "$2}' FS_is_Other2.txt >> _IBD2_Probs.tmp
awk '{print $3" "$4}' FS_is_Other2.txt >> _IBD2_Probs.tmp
awk '{print $1" "$2}' HS_is_Other2.txt >> _IBD2_Probs.tmp
awk '{print $3" "$4}' HS_is_Other2.txt >> _IBD2_Probs.tmp

sort -u _IBD2_Probs.tmp > _IBD2_Probs.txt
rm _IBD2_Probs.tmp
rm *_is_*.txt
```
And see how much is fixed by running: 
```
cat _IBD?_Probs.txt > _RemoveIBD.tmp
./plink --bfile _D7 --remove _RemoveIBD.tmp --make-bed --out _D8 --allow-no-sex
```

Summarize all problematic samples and remove IBD issues including duplicates that were already removed using:
```
awk '{print $2}' _IBD1_Probs.txt | sort -u > _DTestIBD1.tmp
grep -f _DTestIBD1.tmp SMP_Real_Duplicates.dat | awk '{print $1" "$1}' > _SMP_CertainIBD_Problems.tmp
awk '{print $2" "$2}' _IBD1_Probs.txt >> _SMP_CertainIBD_Problems.tmp
grep -f _2DNAs.dat _D7_1.fam | awk '{print $1" "$2}' | sed 's/_/ /g' |  awk '!seen[$1]++' | awk '{print $1"_"$2" "$3"_"$4}' | grep -f _DTestIBD1.tmp >> _SMP_CertainIBD_Problems.tmp
sort -u _SMP_CertainIBD_Problems.tmp > SMP_CertainIBD_Problems.dat

awk '{print $2}' _IBD2_Probs.txt | sort -u > _DTestIBD2.tmp
grep -f _DTestIBD2.tmp SMP_Real_Duplicates.dat | awk '{print $1" "$1}' > _SMP_MaybeIBD_Problems.tmp
awk '{print $2" "$2}' _IBD2_Probs.txt >> _SMP_MaybeIBD_Problems.tmp
grep -f _2DNAs.dat _D7_1.fam | awk '{print $1" "$2}' | sed 's/_/ /g' |  awk '!seen[$1]++' | awk '{print $1"_"$2" "$3"_"$4}' | grep -f _DTestIBD2.tmp >> _SMP_MaybeIBD_Problems.tmp
sort -u _SMP_MaybeIBD_Problems.tmp > SMP_MaybeIBD_Problems.dat
```
Rescan data on duplicate samples, but now post IBD and with family structure in place, using:
```
./king -b _D8.bed --duplicate --prefix _DuplicateSamples_round2
awk '{if ($1!=$3) print $1" "$2}' _DuplicateSamples_round2.con | grep -v "FID" >  _SMP_DupeIBD_Problems.tmp
awk '{if ($1!=$3) print $3" "$4}' _DuplicateSamples_round2.con | grep -v "FID" >>  _SMP_DupeIBD_Problems.tmp
./plink --bfile _D8 --remove _SMP_DupeIBD_Problems.tmp --make-bed --out _D9 --allow-no-sex

awk '{print $2}' _SMP_DupeIBD_Problems.tmp > _DTestIBD3.tmp
grep -f _DTestIBD3.tmp SMP_Real_Duplicates.dat | awk '{print $1" "$1}' > _DtestIBD4.tmp
awk '{print $2" "$2}' _SMP_DupeIBD_Problems.tmp >> _DtestIBD4.tmp
sort -u _DtestIBD4.tmp > SMP_DupeIBD_Problems.dat
```
<br/>

### Step 4.10 - Select only genotypes of individuals with phenotype data - requires manual user input
Note that this step requires the ID’s in the phenotype file and the genotype file to match.

If all individuals in the genotype data have phenotypes, in which case the genotype data does not require trimming, simply run: 
```
./plink --bfile _D9 --make-bed --out $CLEANFILE --allow-no-sex
```

If there are individuals in the genetic data without phenotype data, we want to remove these from the to-be uploaded dataset, using:
<pre>
awk '{print $[<i>column number of ID in phenotype file</i>]}' $PhenoData | sort -u > _PhenoIDs.tmp
# Example: awk ‘{print $1}’ $PhenoData > _PhenoIDs.tmp

awk '{print $1" "$2}' _D9.fam | sort -u > _D9ID.tmp
grep -f _PhenoIDs.tmp _D9ID.tmp > _D9ID2.tmp
./plink --bfile _D9 --keep _D9ID2.tmp --make-bed --out $CLEANFILE --allow-no-sex
</pre>
Finally, rename your log files for upload and remove all redundant files using:
```
for f in _D*.log; do
 mv "$f" "${f/_/}"
done

rm -v _*

echo "All done!"
```
<br/>

## Step 5: Step-by-step Data Upload
By now you should have received your guest account from the UMCG GCC help desk. After finishing the sample QC, we ask you to upload the phenotype and genotype data to the server using your guest account (named umcg-guest[1-15]). Here's a list of the files that need to be uploaded, for which we provide the code below:
- The phenotype file;
- The codebook for the phenotype file, if not included in the phenotype file itself;
- The sample QC’ed genotype data in .bim, .bed, and .fam format;
- All .log & .dat files from Step 4.1 - Step 4.10. 

A step-by-step approach for uploading data to the UMCG GCC upload server can be found at https://wiki.gcc.rug.nl/wiki/DataSharing, but is also outlined below. Again, any section of a line enclosed in square brackets requires manual user input that is specified by the italicized text therein.


Assign the path and location of your private key created in Step 1 to an environmental variable:
<pre>
KEY=[<i>/path/to/private/account/key</i>].ppk
</pre>
Set the private key as your password for the sftp protocol
```
set sftp:connect-program "ssh -axi "$KEY""
```
Go to the local folder where all or most of your data is stored:
<pre>
cd [<i>/local/folder/with/your/data/</i>]
</pre>
Connect to your guest account of the GCC SFTP upload server: 
<pre>
sftp [<i>your_guest_accountname</i>]@cher-ami.hpc.rug.nl
</pre>
Upload the phenotype, genotype, .log and .dat files:
<pre>
put [<i>phenotype_file.extension</i>]
put [<i>phenotype_cookbook.extension</i>]
put *_CLN.*
put *.log 
put *.dat

# For example: 	put BIONIC_pheno_NTR.sav
#               put BIONIC_pheno_NTR_cookbook.txt
#               put NTR_AFFY6_CLN.*
#               put *.log
#               put *.dat

# If not all files are in the same folder (the folder from which we issued the sftp command), you have to manually specify the location of the file.
# For example:	put /home/user/janjansen/bionic/BIONIC_pheno_NTR.sav
</pre>
Exit from the remote server when all necessary files are uploaded:
```
bye
```

Please send an email to f.huider@vu.nl when the data has finished uploading.

Once uploaded, we will conduct several sanity checks and additional QC steps. You will get feedback on whether the cleaning and upload of the data was successful. By default, your access to the cher-ami upload server will be active for three months, but this period can be extended if needed.

NB: In case of any issues with regard to uploading of the genotype data, please contact the GCC Helpdesk (hpc.helpdesk@umcg.nl) with cc: f.huider@vu.nl.

At this point, you have completed this standard operating procedure. Thank you for your effort and cooperation in the BIONIC project!








