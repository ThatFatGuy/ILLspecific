The following codes are specifically aimed at members of the ILL lab. 

**Using the local install of BLAST**

>Sign into the biochem server on command line/terminal using your credentials (i will not detail how to do this online).
>When you log on you will be in your own student/staff directory. From here you need to navigate to the lab_group folder. An easy way of doing this is -

```bash
cd /Network/Servers/biocldap.otago.ac.nz/Volumes/BiochemXsan/staff_groups/lamontlab/Documents/BLAST

```
> You are now in the BLAST directory, in here there is a bunch of files and folders. Note* the path might change if the server is reconfigured, just keep that in mind if it doesnt work in a year or two.

>In this folder there is an output_files and input_files folders - they are self explainatory, each of them contain an instructions file if you wish to read it. You can do this simply by using (when in the folder containing) -

```bash
less INSTRUCTIONS

```

> PLEASE, for any sequence you want to blast, you put it as a .txt or .fasta file in the input_sequences file, with your initials and what gene it is - This makes life easier for everyone else. Also make sure you sequence has a fasta header as the first line (although not needed, it makes downstream analysis a lot easier). Denoted by a **>** followed by whatever you want to call your sequence.

> To use our BLAST databases

```bash
blastn -db DATABASE -query input_sequences/my_file -perc_identity n -out output_files/myoutput

```

> Currently our BLAST databases for blastn (nucleotide blast) are **AERUGINOSA** and **ClinPsamples**. AERUGINOSA contains all complete genomes from pseudomonas.com, and is quite a big database. ClinPsamples contains all genome assemblies of the 48 clinical isolates obtained from Canada, these are strains from either NZ or Tasmania, and is a nice database to look at variability of genes involved in antibiotic resistance. PLEASE NOTE* when telling blastn which database to use, do not add the file suffixes of .nhr, .nin, .nsq, you just need to tell it the main database name.

> I have added the perc_identity argument into this code as well, this will enable you to choose a minimum matching percent for the query vs the database. This comes in handy when you are looking at a highly variable sequence (ie: mexT).

> The blast command is very customisable if you want to change it then just use.

```bash
blastn -h
blastn -help

```



