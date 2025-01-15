# Fungal and bacterial microbiota of red wood ants’ infrabuccal pockets
## Description of the pipeline created in the Symbiosis Evolution Research Group and used to process data of bacterial V4 16S rRNA, fungal ITS1, ITS2 18S rRNA and host’s COI amplicon sequencing data.

### [Data splitting into bins corresponding to marker gene region]([multiSPLIT](https://github.com/IgorSiedlecki/Microbial-diversity-of-Formica-polyctena-infrabuccal-pockets/blob/0554e65c7edac81b4bbc89a952d56022d42eacd5/multiSPLIT.py)):
- Recognizes primers for each targetted gene fragment,
- Separates sequences to corresponding bins (subfolders),
- Trims primers,
- Saves modified R1 and R2 fastq files in a dedicated directory.
 
This is the first step of the analysis. It allows one to save time and computing power enabling to focus on a particular marker gene analysis. 
 
### [Amplicon processing]([LSD5](https://github.com/IgorSiedlecki/Microbial-diversity-of-Formica-polyctena-infrabuccal-pockets/blob/0554e65c7edac81b4bbc89a952d56022d42eacd5/LSD5.py)):
- Analyses each library (sample) separately,
- Merges R1 and R2 reads, passes only high-quality reads,
- Converts fastq to fasta files,
- Dereplicates and denoises samples individually,
- Assigns taxonomy affiliation to reads,
- Produces zOTU/OTU tables used by other scripts.
 
This is the core amplicon analysis workflow. 
This script joins F and R (R1 and R2) reads, passing only high-quality ones (phred score >=30). 
Next, it converts fastq to fasta files and dereplicates and denoise sequences in each library separately to avoid losing biologically relevant signals.
Joins all the libraries into one table and assigns all the sequences to taxonomy.
