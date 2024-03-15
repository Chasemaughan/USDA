###### Synteny visualization in SynVisio ######
#Upload C. formosanum genome to CoGe

#C. formosanum self-comparison
	#Run CoGe SynMap of C. formosanum vs. C. formosanum, using Quota align merge setting and syntenic depth ratio of 2:2
	#Download DAGChainer output file
	#Modify to create Cf_Cf.homology file containing only the names of the two syntenic genes on each line -- head of the file:
		Cf016281        Cf074821
		Cf016282        Cf074819
		Cf016283        Cf074818
		Cf016284        Cf074817
		Cf016285        Cf074816
		Cf016286        Cf074814
		Cf016287        Cf074813
		Cf016288        Cf074812
		Cf016289        Cf074811
		Cf016290        Cf074809
	#Modify C. formosanum gff file to create Cf_Cf.gff file containing only the chromosome, gene name, start, and stop -- head of the file:
		Cf6B    Cf000002        43177   79861
		Cf6B    Cf000004        80342   81223
		Cf6B    Cf000001        7875    19680
		Cf6B    Cf000003        73033   79461
		Cf6B    Cf000006        85192   85764
		Cf6B    Cf000005        83311   83406
		Cf6B    Cf000008        119913  123512
		Cf6B    Cf000009        125906  130540
		Cf6B    Cf000010        143714  150316
		Cf6B    Cf000014        176178  180076
	#Run MCScanX to generate Cf_Cf.collinearity file (run locally on my computer)
		/mnt/box/software/MCScanX/MCScanX_h -b 1 Cf_Cf #needs to be run from the same directory containing the Cf_Cf.homology and Cf_Cf.gff files
	#Create figures using SynVisio (https://synvisio.github.io/#/)
		#Upload Cf_Cf.collinearity and Cf_Cf.gff files
		#Create hive plot (3-axis plot with chromosomes from one sub-genome on each of the 3 axes)
			#Select "Multi Level Analysis" and "Hive View"
			#Click the "+" button to add 3 chromosome sources
			#For "Chromosome Source 1", select the B chromsomes, then C chromosomes for source 2, and D for 3
			#Click "Go"
			#Click "Switch Chart Background to Light Theme" at the top right corner to make the plot background white
			#Click "Download Images" button at bottom right to save at SVG image with 10X resolution
		#Create dotplot
			#Select "Single Level Analysis" and "Dot Plot"
			#Select all chromosomes in the "Source Chromosomes" dropdown menu
			#Select all chromosomes in the "Target Chromosomes" dropdown menu
			#Click "Go"
			#Reorder chromosomes as needed by clicking the "Advanced Chromosome Layout Editor" and then dragging the chromosome names around as needed
			#Click "Switch Chart Background to Light Theme" at the top right corner to make the plot background white
			#Click "Download Images" button at bottom right to save at SVG image with 10X resolution
		#Create tree view plot showing sets of chromosomes on multiple parallel lines (for example, Chr1 and 2 from B, C, and D sub-genomes)
			#Select "Multi Level Analysis" and "Tree View"
			#Click the "+" button to add 3 chromosome levels
			#Select Cf1D and Cf2D for from the "Chromosome Level 1" dropdown menu
			#Select Cf1B and Cf2B for from the "Chromosome Level 2" dropdown menu
			#Select Cf1D and Cf2D for from the "Chromosome Level 3" dropdown menu
			#Click "Go"
			#Invert the Cf1D, Cf1B, and Cf2B chromosomes by clicking the "Advanced Chromosome Layout Editor" and then double-clicking on the chromosome names
			#Click "Switch Chart Background to Light Theme" at the top right corner to make the plot background white
			#Click "Download Images" button at bottom right to save at SVG image with 10X resolution

#C. formosanum vs C. quinoa comparison
	#Run CoGe SynMap of C. formosanum vs. C. quinoa, using Quota align merge setting and syntenic depth ratio of 3:2
	#Download DAGChainer output file
	#Modify to create Cq_Cf.homology file containing only the names of the two syntenic genes on each line -- head of the file:
		CQ056256        Cf009232
		CQ056258        Cf009234
		CQ056259        Cf009235
		CQ056260        Cf009236
		CQ056261        Cf009237
		CQ056256        Cf036134
		CQ056258        Cf036132
		CQ056259        Cf036131
		CQ056260        Cf036130
		CQ056261        Cf036129
	#Modify C. formosanum gff and C. quinoa gff files to create a concatenated Cq_Cf.gff file containing only the chromosome, gene name, start, and stop -- sample lines of the file showing genes from quinoa and formosanum:
		Cf6B    Cf000002        43177   79861
		Cf6B    Cf000004        80342   81223
		Cf6B    Cf000001        7875    19680
		Cf6B    Cf000003        73033   79461
		Cf6B    Cf000006        85192   85764
		Cf6B    Cf000005        83311   83406
		Cf6B    Cf000008        119913  123512
		Cf6B    Cf000009        125906  130540
		Cf6B    Cf000010        143714  150316
		Cf6B    Cf000014        176178  180076
					..........
		Cq1B    CQ022811        179227  179745
		Cq1B    CQ022812        532628  532639
		Cq1B    CQ022813        746832  747263
		Cq1B    CQ022814        749190  752418
		Cq1B    CQ022815        760438  769998
		Cq1B    CQ022816        778362  799029
		Cq1B    CQ022817        800987  804587
		Cq1B    CQ022818        806039  809056
		Cq1B    CQ022819        839705  842737
		Cq1B    CQ022820        857519  858361
	#Run MCScanX to generate Cq_Cf.collinearity file (run locally on my computer)
		/mnt/box/software/MCScanX/MCScanX_h Cq_Cf #needs to be run from the same directory containing the Cq_Cf.homology and Cq_Cf.gff files
	#Create figures using SynVisio (https://synvisio.github.io/#/)
		#Upload Cq_Cf.collinearity and Cq_Cf.gff files
		#Create dotplot
			#Select "Single Level Analysis" and "Dot Plot"
			#Select all Cf chromosomes in the "Source Chromosomes" dropdown menu
			#Select all Cq chromosomes in the "Target Chromosomes" dropdown menu
			#Click "Go"
			#Reorder chromosomes as needed by clicking the "Advanced Chromosome Layout Editor" and then dragging the chromosome names around as needed
			#Click "Switch Chart Background to Light Theme" at the top right corner to make the plot background white
			#Click "Download Images" button at bottom right to save at SVG image with 10X resolution
			


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

###### Chromosome visualization in Circa ######
		module load emboss
	#Create a file Cf_chrs.len containing the names and lengths of all chromosomes in the C. formosanum assembly
		#First, get the chromosome lengths using infoseq
			infoseq -only -length -name c_formosanum_renamedChrOnly.fasta
		#Then copy and paste into a new file and edit manually so that it looks like this:
			chromosome,size
			Cf1B,79488523
			Cf2B,75745498
			Cf3B,81617237
			Cf4B,78488603
			Cf5B,84563608
			Cf6B,92862210
			Cf7B,84111257
			Cf8B,82217616
			Cf9B,73448765
		#Load this file into Circa by clicking on the "Start" tab and uploading the file, then selecting the approapriate columns to designate the chromosome names and sized
	#Create a file Cf_chrs.bed.windows500k containing the coordinates of each chromosome broken into 500-kb windows
		#First, create a bed file of the chromosome names and sizes
			grep -v "chromosome" Cf_chrs.len | sed 's/,/\t/' > Cf_chrs.bed
		#Then create the 500-kb window coordinates	
			bedtools makewindows -g Cf_chrs.bed -w 500000 > Cf_chrs.bed.windows500k

	#Create a file Cf_chrs.bed.windows500k_genes_coverage containing a count of the number of genes in each 500-kb window of each chromosome

		module load bedttols

		#First, create a bed file containing the coordinates of all the genes
			awk '($3=="gene")' CF_Final_allscaffolds_functional_blast.gff | grep -v -i "trna" | awk '{print $1 "\t" $4 "\t" $5}' > Cf_genes.bed
		
		#Then count the number of genes in each 500-kb window
			bedtools coverage -a Cf_chrs.bed.windows500k -b Cf_genes.bed | awk 'BEGIN {print "chr" "\t" "start" "\t" "stop" "\t" "num" "\t" "bases" "\t" "len" 			"\t" "percent"}; {print}' > Cf_chrs.bed.windows500k_genes_coverage
		
		#Load this file into Circa by clicking on the "Build" tab and uploading the file to a new area track, designating the chr column as the chromosome, the start column as the position, and the num column as the y
	#Create a file Cf_chrs.bed.windows500k_telomere_coverage containing a count of the number of telomere hits in each 500-kb window of each chromosome
		#First, create a file telomere.fasta containing the canonical telomere sequence
			>telomere
			TTTAGGGTTTAGGGTTTAGGGTTTAGGG
		#Then create a BLAST database from the formosanum assmebly
			makeblastdb -in c_formosanum_renamedChrOnly.fasta -dbtype nucl
		#Then do a BLAST search of the telomere sequencing against the formosanum genome
			blastn -task blastn -query telomere.fasta -db c_formosanum_renamedChrOnly.fasta -out telomere_blast_Cf-chrs.out -outfmt 6
		#Then select hits with 100% identity and reformat the file for bedtools
			awk '{if ($3==100) print $2 "\t" $9 "\t" $10}' telomere_blast_Cf-chrs.out | awk '{if ($2<$3) print; else print $1 "\t" $3 "\t" $2}' > telomere_blast_Cf-chrs.out.ID100	
		#Then count the number of hits in each 500-kb window
			bedtools coverage -a Cf_chrs.bed.windows500k -b telomere_blast_Cf-chrs.out.ID100 | awk 'BEGIN {print "chr" "\t" "start" "\t" "stop" "\t" "num" "\t" "bases" "\t" "len" "\t" "percent"}; {print}' > Cf_chrs.bed.windows500k_telomere_coverage
		#Load this file into Circa by clicking on the "Build" tab and uploading the file to a new area track, designating the chr column as the chromosome, the start column as the position, and the num column as the y
	#Create a file Cf_chrs.bed.windows500k_18-24J1e-50_coverage containing a count of the number of 18-24J (B-subgenome specific repeat) hits in each 500-kb window of each chromosome
		#First create a file 18-24J.fasta containing the 18-24J sequence (HM641821.1 Chenopodium quinoa clone 18-24j repeat region sequence from NCBI)
		#Then do a BLAST search of the 18-24J sequencing against the formosanum genome
			blastn -task blastn -query 18-24J.fasta -db ../C_formosanum_assemblies/Renamed_to_Chr/c_formosanum_renamedChrOnly.fasta -out 18-24J_blast_Cf-chrs.out -outfmt 6
		#Then select hits with 100% identity and reformat the file for bedtools
			awk '{if ($11<1e-50) print $2 "\t" $9 "\t" $10}' 18-24J_blast_Cf-chrs.out | awk '{if ($2<$3) print; else print $1 "\t" $3 "\t" $2}' > 18-24J_blast_Cf-chrs.out.1e-50
		#Then count the number of hits in each 500-kb window
			bedtools coverage -a Cf_chrs.bed.windows500k -b 18-24J_blast_Cf-chrs.out.1e-50 | awk 'BEGIN {print "chr" "\t" "start" "\t" "stop" "\t" "num" "\t" "bases" "\t" "len" "\t" "percent"}; {print}' > Cf_chrs.bed.windows500k_18-24J_coverage
		#Load this file into Circa by clicking on the "Build" tab and uploading the file to a new area track, designating the chr column as the chromosome, the start column as the position, and the num column as the y

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

	#Create a file Cf_chrs.bed.windows500k_acuminatum_coverage_10k containing a count of the number of D genome reads from C. acuminatum that map to each 500-kb window of each chromosome
		#Start with the file C.acuminatum_v_C.formosanum.paf.coords obtained from Jeff, rename it as acuminatum_read_mapping.bed
		#First, rename the chromosomes in acuminatum_read_mapping.bed so that they match all the other files
			sed 's/_[1-9]c//' acuminatum_read_mapping.bed | sed 's/Chr7/Cf1B/' | sed 's/Chr8/Cf2B/' | sed 's/Chr3/Cf3B/' | sed 's/Chr6/Cf4B/' | sed 's/Chr5/Cf5B/' | sed 's/Chr1\t/Cf6B\t/' | sed 's/Chr2\t/Cf7B\t/' | sed 's/Chr4/Cf8B/' | sed 's/Chr9/Cf9B/' | sed 's/Chr16/Cf1C/' | sed 's/Chr18/Cf2C/' | sed 's/Chr12/Cf3C/' | sed 's/Chr15/Cf4C/' | sed 's/Chr10/Cf5C/' | sed 's/Chr11/Cf6C/' | sed 's/Chr13/Cf7C/' | sed 's/Chr14/Cf8C/' | sed 's/Chr17/Cf9C/' | sed 's/Chr25/Cf1D/' | sed 's/Chr20/Cf2D/' | sed 's/Chr19/Cf3D/' | sed 's/Chr24/Cf4D/' | sed 's/Chr22/Cf5D/' | sed 's/Chr21/Cf6D/' | sed 's/Chr26/Cf7D/' | sed 's/Chr23/Cf8D/' | sed 's/Chr27/Cf9D/' > acuminatum_read_mapping.bed.renamed
		#Then count the number of reads that map to each 500-kb window
			bedtools coverage -a Cf_chrs.bed.windows500k -b acuminatum_read_mapping.bed.renamed | awk 'BEGIN {print "chr" "\t" "start" "\t" "stop" "\t" "num" "\t" "bases" "\t" "len" "\t" "percent"}; {print}' > Cf_chrs.bed.windows500k_acuminatum_coverage
		#Then truncate the max number of reads (4th column, num) to 10001 to make the plot look better in Circa
			awk '{if ($4!="num" && $4>10000) print $1 "\t" $2 "\t" $3 "\t" "10001" "\t" $5 "\t" $6 "\t" $7; else print}' Cf_chrs.bed.windows500k_acuminatum_coverage > Cf_chrs.bed.windows500k_acuminatum_coverage_10k
		#Load this file into Circa by clicking on the "Build" tab and uploading the file to a new area track, designating the chr column as the chromosome, the start column as the position, and the num column as the y
		
	
	#Create a file Cf_chrs.bed.windows500k_gypsy_coverage containing a count of the number of gypsy LTR repeats in each 500-kb window of each chromosome
		#Starting with the file consensi.fa.classified_RMviridiplantae_combined.fasta from Jeff, which does not contain coordinates but does contain the sequences of all repeats, including the designation of "Gypsy" in the sequence names, extract the names of all Gypsy repeats
			grep "Gypsy" consensi.fa.classified_RMviridiplantae_combined.fasta | sed 's/>//' | sed 's/#/\t/' | cut -f 1 > consensi.fa.classified_RMviridiplantae_combined.fasta.gypsy-names
			sort consensi.fa.classified_RMviridiplantae_combined.fasta.gypsy-names > consensi.fa.classified_RMviridiplantae_combined.fasta.gypsy-names.sort #I didn't actually need to sort it
		#Starting with the RMviridiplantae_c_formosanum.scaffolds_renamedChr_all.fasta.out.gff file from Jeff, which contains the coordinates of all annotated repeats but does not include the "Gypsy" designation, create a new file containing just the chromosome, start, stop, and motif name (the motif name of this file will be used to match up with the names of the Gypsy sequences pulled out from the consensi file in the step above 
			grep -v "#" RMviridiplantae_c_formosanum.scaffolds_renamedChr_all.fasta.out.gff | cut -f 1,4,5,9 | sed 's/Target//' | sed 's/"Motif://' | sed 's/".*//' | sort -k 4 > RMviridiplantae_c_formosanum.scaffolds_renamedChr_all.fasta.out.gff.simplified.sort #I didn't actually need to sort it
		#Then pull out only the lines of the gff file that contain names matching the names of the gypsy repeats
			grep -w -f consensi.fa.classified_RMviridiplantae_combined.fasta.gypsy-names.sort RMviridiplantae_c_formosanum.scaffolds_renamedChr_all.fasta.out.gff.simplified.sort > RMviridiplantae_c_formosanum.scaffolds_renamedChr_all.fasta.out.gff.simplified.sort.gypsy-only
		#Then count the number of Gypsy repeats in each 500-kb window
			bedtools coverage -a Cf_chrs.bed.windows500k -b RMviridiplantae_c_formosanum.scaffolds_renamedChr_all.fasta.out.gff.simplified.sort.gypsy-only | awk 'BEGIN {print "chr" "\t" "start" "\t" "stop" "\t" "num" "\t" "bases" "\t" "len" "\t" "percent"}; {print}' > Cf_chrs.bed.windows500k_gypsy_coverage
		#Load this file into Circa by clicking on the "Build" tab and uploading the file to a new area track, designating the chr column as the chromosome, the start column as the position, and the num column as the y