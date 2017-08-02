# Notes on blasting clustered OTUs against JGI assembled contigs

```
module load BLAST+

makeblastdb -in /mnt/scratch/dunivint/Cen06.scaffolds.fasta  -dbtype nucl -out /mnt/scratch/dunivint/databases/Cen06.db

blastn -db /mnt/scratch/dunivint/databases/Cen06.db -query clustered_AsRG_ARG_nucl.fa -out Cen06_blast.txt -outfmt "6 qseqid salltitles pident evalue" -max_target_seqs 10
```

# Notes on blasting clustered OTUs against MAGs

```
cat /mnt/research/ShadeLab/WorkingSpace/Sorensen/MEGA_ASSEMBLY/Genome_Binning/VerySpecific_Bins/* > METABAT.fa

module load BLAST+

makeblastdb -in /mnt/scratch/dunivint/METABAT.fa  -dbtype nucl -out /mnt/scratch/dunivint/databases/METABAT.db

blastn -db /mnt/scratch/dunivint/databases/METABAT.db -query /mnt/research/ShadeLab/WorkingSpace/Dunivin/xander/networks/clustered_AsRG_ARG_nucl.fsa -out metabat_blast.txt -outfmt "6 qseqid salltitles pident evalue" -max_target_seqs 10
```

Once top hits are generated, you can search for the specific contig in the original files
```
cd /mnt/research/ShadeLab/WorkingSpace/Sorensen/MEGA_ASSEMBLY/Genome_Binning/VerySpecific_Bins
grep -Rl "CONTIG_NAME"
```

This list will let you compare top hits to see if any occur in the same bin. 

| GENE | OTU | Contig | % identity | e-value | Bin | 
| ---- | --- | ------ | ---------- | ------- | --- |
|acr3 | OTU_0053 | k107_5410911 |	98.73	| 0.0 | 608 |
|acr3 | OTU_0053	| k107_374618	| 88.89	| 0.0 | 608, 795|
|acr3 | OTU_0053	| k107_30885960	| 86.16	| 0.0 | 795 |
|acr3 | OTU_0053	| k107_3117242	| 84.88	| 0.0 | 559 |
|acr3 | OTU_0053	| k107_24027065	| 81.54	| 0.0 | 736 |
|acr3 | OTU_0053	| k107_2881296	| 77.52	| 1e-164 | 251|
|acr3 | OTU_0053	| k107_20985308	| 76.86	| 6e-153 | 795 |
|acr3 | OTU_0053	| k107_6209637	| 73.29	| 2e-92 | 666 |
|acr3 | OTU_0053	| k107_17335913	| 71.85	| 7e-58 | 231 |
|acr3 | OTU_0053	| k107_22134734	| 73.06	| 9e-57 | 897 |
|acr3 | OTU_0002	| k107_14595991	| 89.19	| 0.0 | 419 |
|acr3 | OTU_0002	| k107_14536628	| 88.13	| 1e-171 | 827 |
|acr3 | OTU_0002	| k107_17642053	| 73.58	| 3e-14 | 654 |
|arsM | OTU_0109	| k107_1005213	| 84.23	| 7e-135 | 632 |
|arsM |OTU_0109	| k107_35201236	| 77.38	| 3e-78 | 848 |
|arsM |OTU_0109	| k107_3530183	| 76.36	| 4e-38 | 742 |
|arsM |OTU_0109	| k107_33012804	| 76.64	| 1e-27 | 783 |
|arsM |OTU_0296	| k107_19011909	| 77.34	| 4e-119 | 1040 |
|arsM |OTU_0296	| k107_10364269	| 78.57	| 7e-112 | 446 |
|arsM |OTU_0296	| k107_1728533	| 78.48	| 2e-107 | 215 |
|arsM |OTU_0296	| k107_9939490	| 78.40	| 7e-107 | 319 |
|arsM |OTU_0296	| k107_9261249	| 78.93	| 4e-99 | 45 |
|arsM |OTU_0296	| k107_33012804	| 79.43	| 3e-90 | 783 |
|arsM |OTU_0296	| k107_1593047	| 76.92	| 7e-87 | 848 |
|arsM |OTU_0296	| k107_1871211	| 76.21	| 7e-87 | 27 |
|arsM |OTU_0296	| k107_17033332	| 75.55	| 2e-78 | 790 |
|arsM |OTU_0296	| k107_13293973	| 75.59	| 5e-78 | 559|
|tolC |OTU_0005	| k107_11533305	| 76.50	| 3e-156 | 232 |
|tolC |OTU_0005	| k107_15504113	| 79.00	| 4e-155 | 1040 |
|tolC |OTU_0005	| k107_32829128	| 76.02	| 2e-117 | 754 |
|tolC | OTU_0005	| k107_10071582	| 74.83	| 7e-98 | 479 |
|ClassB | OTU_0003	| k107_2170412	| 91.45	| 0.0 | 795 |
|ClassB | OTU_0003	| k107_15390298	| 82.17	| 0.0 | 527 |
|drfa12 | OTU_0076	| k107_16275153	| 98.55	| 1e-62 | 966 |
|drfa12 |OTU_0076	| k107_2833959	| 86.13	| 8e-34 | 591 |
|drfa12 |OTU_0076	| k107_15496897	| 84.06	| 2e-29 | 591 |
|drfa12 |OTU_0076	| k107_11473637	| 84.44	| 2e-29 | 591 |
|drfa12 |OTU_0076	| k107_24297536	| 85.71	| 2e-29 | 361 |
|drfa12 |OTU_0076	| k107_2230677	| 85.04	| 3e-28 | 591|
|drfa12 |OTU_0076	| k107_35661732	| 78.83	| 5e-16 | 298|


## rplB matches
```
module load BLAST+

makeblastdb -in /mnt/scratch/dunivint/METABAT.fa  -dbtype nucl -out /mnt/scratch/dunivint/databases/METABAT.db

blastn -db /mnt/scratch/dunivint/databases/METABAT.db -query /mnt/research/ShadeLab/WorkingSpace/Dunivin/xander/networks/clustered_rplB_nucl.fsa -out metabat_rplB_blast.txt -outfmt "6 qseqid salltitles pident evalue" -max_target_seqs 10
```

|  OTU | Contig | % identity | e-value | Bin | 
| ---- | --- | ------ | ---------- | ------- |
| OTU_1131 | k107_974644 | 97.35 | 0.0 | 916, 795, |
| OTU_1131 | k107_18736747 | 85.02 | 0.0 | 897 |
| OTU_1131 | k107_3134199 | 81.53 | 2e-150 | 581 |
| OTU_1131 | k107_31965501 | 81.20 | 4e-143 | 725 |
| OTU_1131 | k107_14923167 | 79.48 | 1e-123 | 885 |
| OTU_1131 | k107_16818979 | 81.28 | 4e-123 | 791 |
| OTU_1131 | k107_21709338 | 78.89 | 3e-115 | 213 |
| OTU_1131 | k107_177340 | 78.65 | 6e-92 | 725, 1040 |
| OTU_1131 | k107_10004184 | 76.57 | 4e-89 | 1036 |
| OTU_1131 | k107_7326416 | 76.18 | 1e-88 | 68 |
| OTU_1027 | k107_3197021 | 99.87 | 0.0 | 165, 768 |
| OTU_1027 | k107_35332285 | 84.53 | 0.0 | 165 |
| OTU_1027 | k107_1847100 | 80.10 | 1e-159 | 760 |
| OTU_1027 | k107_12423742 | 79.65 | 1e-148 | 438 |
| OTU_1027 | k107_24698228 | 80.47 | 1e-113 | 760 |
| OTU_1015 | k107_2199868 | 89.49 | 0.0 | 1015 |
| OTU_1015 | k107_3339952 | 84.50 | 0.0 | 485 |
| OTU_1015 | k107_8505121 | 83.83 | 0.0 | 187 |
| OTU_1015 | k107_35014900 | 83.93 | 0.0 | 559 |
| OTU_1015 | k107_25260313 | 83.23 | 0.0 | 629 |
| OTU_1015 | k107_25164596 | 83.20 | 0.0 | 36 |
| OTU_1015 | k107_5009744 | 82.92 | 0.0 | 795 |
| OTU_1015 | k107_1089496 | 82.83 | 0.0 | 87 |
| OTU_1015 | k107_7225361 | 82.98 | 0.0 | 367 |
| OTU_1015 | k107_28905039 | 81.40 | 2e-176 | 835 |
| OTU_0886 | k107_25260313 | 92.42 | 0.0 | 629 |
| OTU_0886 | k107_35014900 | 83.33 | 0.0 | 559 |
| OTU_0886 | k107_5009744 | 83.44 | 0.0 | 795 |
| OTU_0886 | k107_25164596 | 83.62 | 0.0 | 36 |
| OTU_0886 | k107_7225361 | 82.47 | 0.0 | 367 |
| OTU_0886 | k107_8505121 | 82.70 | 0.0 | 187 |
| OTU_0886 | k107_28905039 | 81.73 | 0.0 | 835 |
| OTU_0886 | k107_3339952 | 82.00 | 0.0 | 485 |
| OTU_0886 | k107_12586753 | 81.09 | 0.0 | 186 |
| OTU_0886 | k107_33593027 | 79.07 | 1e-153 | 559 |
| OTU_0692 | k107_1847100 | 87.43 | 7e-165 | 760 |
| OTU_0692 | k107_9820022 | 87.06 | 2e-161 | 586 |
| OTU_0692 | k107_27099482 | 86.74 | 1e-158 | 732 |
| OTU_0692 | k107_24565332 | 86.64 | 3e-158 | 535 |
| OTU_0692 | k107_26328263 | 86.47 | 2e-156 | 372 |
| OTU_0692 | k107_31342389 | 86.08 | 1e-153 | 523 |
| OTU_0692 | k107_4671586 | 85.69 | 8e-150 | 1040 |
| OTU_0692 | k107_22181471 | 85.46 | 4e-148 | 821 |
| OTU_0692 | k107_27042815 | 84.81 | 5e-142 | 760 |
| OTU_0692 | k107_23528253 | 85.07 | 1e-138 | 141 |
| OTU_0564 | k107_2504596 | 84.29 | 1e-141 | 532 |
| OTU_0564 | k107_18540592 | 80.30 | 2e-105 | 750 |
| OTU_0564 | k107_6924811 | 79.62 | 2e-101 | 7 |
| OTU_0564 | k107_21351319 | 79.89 | 3e-99 | 1036 |
| OTU_0564 | k107_16357629 | 79.55 | 1e-97 | 80 |
| OTU_0564 | k107_9736387 | 79.46 | 2e-96 | 255 |
| OTU_0564 | k107_33810829 | 78.35 | 1e-88 | 346 |
| OTU_0564 | k107_27416274 | 78.37 | 3e-83 | 225 |
| OTU_0564 | k107_4903305 | 76.89 | 4e-68 | 283 |
| OTU_0564 | k107_2509520 | 77.41 | 1e-57 | 1040 , 532 |
| OTU_0549 | k107_3223105 | 84.60 | 0.0 | 632 |
| OTU_0549 | k107_3150412 | 84.21 | 0.0 | 815 |
| OTU_0549 | k107_14786139 | 84.48 | 0.0 | 553 |
| OTU_0549 | k107_54727 | 80.93 | 6e-172 | 477, 439,313,706|
| OTU_0549 | k107_17682343 | 79.49 | 5e-153 | 261 |
| OTU_0549 | k107_2732013 | 86.38 | 3e-135 | 655 |
| OTU_0549 | k107_35724266 | 77.57 | 1e-123 | 701 |
| OTU_0549 | k107_1530434 | 77.55 | 1e-114 | 701 |
| OTU_0549 | k107_22964606 | 76.28 | 1e-109 | 701 |
| OTU_0549 | k107_856657 | 75.74 | 5e-103 | 27 |
| OTU_0407 | k107_1235957 | 92.15 | 0.0 | 70 |
| OTU_0407 | k107_11992326 | 90.56 | 0.0 | 1040 |
| OTU_0407 | k107_12547512 | 88.31 | 4e-177 | 465 |
| OTU_0407 | k107_16417613 | 88.29 | 2e-175 | 678 |
| OTU_0407 | k107_30031548 | 87.52 | 9e-169 | 49 |
| OTU_0407 | k107_14426587 | 87.05 | 2e-165 | 246 |
| OTU_0407 | k107_11993512 | 86.92 | 1e-163 | 246 |
| OTU_0407 | k107_13442791 | 86.35 | 1e-158 | 235 |
| OTU_0407 | k107_11835691 | 86.32 | 4e-157 | 1040 |
| OTU_0407 | k107_23009873 | 86.04 | 2e-155 | 678 |
| OTU_0355 | k107_27852957 | 88.71 | 0.0 | 969 |
| OTU_0355 | k107_23528253 | 84.33 | 0.0 | 141 |
| OTU_0355 | k107_20518726 | 84.33 | 0.0 | 768 |
| OTU_0355 | k107_9820022 | 83.12 | 4e-179 | 586 |
| OTU_0355 | k107_24565332 | 80.86 | 2e-172 | 535 |
| OTU_0355 | k107_1847100 | 81.18 | 1e-169 | 760 |
| OTU_0355 | k107_26328263 | 80.27 | 5e-168 | 372 |
| OTU_0355 | k107_29573965 | 80.35 | 5e-168 | 137 |
| OTU_0355 | k107_4671586 | 83.08 | 2e-166 | 1040 |
| OTU_0355 | k107_12423742 | 82.87 | 2e-161 | 438 |
| OTU_0267 | k107_24020376 | 85.71 | 6e-166 | 633 |
| OTU_0267 | k107_16357629 | 78.05 | 6e-91 | 80 |
| OTU_0267 | k107_7152071 | 77.29 | 5e-82 | 725 |
| OTU_0267 | k107_33737978 | 76.03 | 3e-69 | 806 |
| OTU_0267 | k107_21423826 | 74.72 | 5e-57 | 725 |
| OTU_0267 | k107_26953992 | 73.68 | 2e-50 | 879 |
| OTU_0267 | k107_12423742 | 74.36 | 3e-34 | 438 |
| OTU_0169 | k107_32624099 | 82.85 | 9e-155 | 711 |
| OTU_0169 | k107_23831040 | 82.52 | 3e-150 | 768 |
| OTU_0169 | k107_6446546 | 85.06 | 3e-140 | 1040 |
| OTU_0169 | k107_25187919 | 79.94 | 3e-130 | 678 |
| OTU_0169 | k107_30822690 | 80.27 | 3e-130 | 246 |
| OTU_0169 | k107_16900348 | 81.19 | 1e-129 | 344 |
| OTU_0169 | k107_23729499 | 79.73 | 1e-123 | 1040 |
| OTU_0169 | k107_28682794 | 79.45 | 1e-123 | 1040 |
| OTU_0169 | k107_20518726 | 79.90 | 4e-123 | 768 |
| OTU_0169 | k107_26634182 | 80.17 | 3e-120 | 768 |
| OTU_0149 | k107_18415688 | 83.53 | 3e-133 | 419 |
| OTU_0149 | k107_25151106 | 82.48 | 4e-127 | 486 |
| OTU_0149 | k107_13007571 | 82.26 | 2e-126 | 879 |
| OTU_0149 | k107_24542821 | 82.41 | 6e-126 | 84 |
| OTU_0149 | k107_58981 | 82.05 | 2e-121 | 466, 241, 833, 1040 |
| OTU_0149 | k107_19059003 | 80.19 | 2e-105 | 832 |
| OTU_0149 | k107_23447480 | 79.36 | 2e-100 | 186 |
| OTU_0149 | k107_14769129 | 79.14 | 4e-98 | 386 |
| OTU_0149 | k107_9969145 | 79.28 | 5e-97 | 96 |
| OTU_0149 | k107_29591449 | 79.49 | 2e-95 | 367 |