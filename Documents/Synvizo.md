# Synteny Visualization on Synvisio for Poa Annua
---
SynVisio needs two main files to run:
- Modified .gff file
- Collinearity file from MCScanx

#### Modified .gff file
Modify the .gff file to create a new file called Pa_pa.gff file containing only the chromosome, gene name, start, and stop -- head of the file. 

Chr7A_a ajg32842 74208163 74208546

Chr1B_a ajg113575 796116 797390

Chr6B_a ajg80259 34355934 34356479

Chr6A_a ajg89807 97199789 97200181

Chr3B_a ajg3155 26344927 26349552

Chr1B_a ajg121610 82615672 82615899

Chr7A_a ajg29714 8932634 8932929
(These will need to be tab seperated)

poa_annua/braker/collinearity_homology/1.homology_collinearity.sh script will automatically rewrite the braker .gff file for you, though the script is written to run the DAGChainer file/MCScanX as well.

#### Collinearity file
MCScanx needs a modified DAGChainer output file to run, to get the DAGChainer:

Run [SynMap](https://genomevolution.org/coge/SynMap.pl) comparing Poa Annua to Poa Annua - in Analysis Options change Merge Syntenic Blocks and Syntenic Depth to Quota Align.
-  There are several genomes uploaded to CoGe for Poa Annua, use the dropdown bar to select the dataset made by Braker ending in **(v2.2,id63794)** .

After the SynMap plot is generated open the download options and download DAGChainer Output.

Modify the DAG file to create a Pa_pa.homology file containing only the names of the two syntenic genes on each line. 

ajg16047	ajg16241

ajg16049	ajg16243

ajg16051	ajg16246

ajg16053	ajg16247

ajg16055	ajg16248

ajg16057	ajg16251


poa_annua/braker/collinearity_homology/1.homology_collinearity.sh script will automatically rewrite the DAGChainer file.

Run MCScanX to generate Cf_Cf.collinearity file
- Download MCScanx locally or use it through a script on the BYU supercomputer.
- braker/collinearity_homology/1.homology_collinearity.sh will automatically call and run MCScanX
- `#McScanX -- intraspecies, -b 1, interspecies,  -b 2
/lustre/scratch/grp/fslg_pws_module/software/MCScanX/MCScanX_h -b 1  ${prefix}`
- The prefix for the the .homology file and the modified .gff file must be the same, Pa_pa.

#### Upload files to SynVisio
On the [SynVisio](https://synvisio.github.io/#/) homepage go to upload own data to dashboard and upload the corrisponding files.
- Oddly SynVisio doenst recognize our chromosomes so I had to click no on both *Would you like to ignore Scaffold regions?* and *Would you like to ignore chromosomes and scaffolds without any alignments in them?* for the program to function properly.
- Click upload and go to the Synteny Dashboard, under filter pannel click the desired chromosomes 
    - For source chromosomes I used: Chr1A_a, Chr2A_a ... Chr7A_a
    - For targert chromosomes I used: Chr1B_a, Chr2B_a ... Chr7B_a
    - Under Advanced Chromosome Layout Editor you can reverse or rearrange the chromosomes, in my synteny plot I reversed all the target chromosomes.







 
