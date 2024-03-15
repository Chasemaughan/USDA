# Creating circa plot files for Poa Annua
All files, tracks, and scripts are found in poa_annua/all_plots_chase/circa

---
Circa tracks (all are created through the scripts)
- Chromosome lengths and names (Pa_chr_length.txt)
- GC content (Pa_AT_GC_content_circa_track.txt)
- Gene density (Pa_chrs.bed.windows500k_genes_coverage)
- Copia distribution ()
- Gypsey distribution ()
- Telomere distribution (Pa_chrs.bed.windows500k_telomere_coverage)
---
###### Files needed:
- Fasta (HiFiasm_HiRise_scaffolds_manuscript.fasta)
- GFF, from maker (poa_annua_makerv1.0.gff)
- GFF, from repeatmasker
- Consensi, from repeatmodeler

###### Scripts needed:
- GC_content.sh
- genedensity.sh
- copia.sh
- gypsy.sh
- telomere.sh

---
GC_Content.sh
files: fasta
1. Infoseq finds Chromosome names and lengths from the fasta file
2. Bedtools makewindows -g breaks fasta file into 2mil bp windows
3. Bedtools nuc  -fi caclulates GC content
4. Datamash calculates mean
5. Data manipulated to be read by Circa 
run: sh GC_content.sh

Only Pa_chr_length.txt and Pa_AT_GC_content_circa_track.txt are needed for circa. The mean should aslo be noted, as it will be used in the final plot.

genedensity.sh
files: fasta, maker gff
1. Infoseq to find Chromosome names and lengths from the fasta file
2. Bedtools makewindows -g  to break fasta file into 500k bp windows
3. Bedtools coverage -a creates the gene coverage file from a the maker gff file (poa_annua_makerv1.0.gff)
5. Data is manipulated inorder to create files for Circa and SynVisio
run: sh genedensity.sh

Only Pa_chrs.bed.windows500k_genes_coverage is needed for Circa,
track_genedensity_number_Synvisio.txt is the same file modified to run on SynVisio

copia.sh
files: fasta, repeatmasker gff, and consensi
1. Infoseq to find Chromosome names and lengths from the fasta file
2. Bedtools makewindows -g  to break fasta file into 500k bp windows
3. Consensi file and repeatmasker gff file are used to make a simplified-copia-only gff file
to run: sh copia.sh

Only (gff file).gff.simplified.sort.copia-only_coverage is needed for Circa, track_copia_number_Synvisio.txt is the same file modified for SynVisio

gypsy.sh
files: fasta, repeatmasker gff, and consensi
1. Infoseq to find Chromosome names and lengths from the fasta file
2. Bedtools makewindows -g  to break fasta file into 500k bp windows
3. Consensi file and repeatmasker gff file are used to make a simplified-gypsy-only gff file
to run gypsy.sh

Only (gff file).gff.simplified.sort.gypsy-only_coverage is needed for Circa, track_gypsy_number_Synvisio.txt is the same file modified for SynVisio

telomere.sh
files: fasta
1. Infoseq to find Chromosome names and lengths from the fasta file
2. Bedtools makewindows -g  to break fasta file into 500k bp windows
3. Telomere file is created with only the Telomere sequence in it
4. a blastn database is created/blastn of telomere against reference
5. only Telomeres above the Percent_ID are kept (identity level is preset to 90)
6. coverage file manipulated to create files that can run on both Synvisio and Circa
to run: sh telomere.sh

Only Pa_chrs.bed.windows500k_telomere_coverage is needed for Circa, track_telomere_number.txt is the same file modified for SynVisio




