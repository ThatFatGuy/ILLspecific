The following codes are specifically aimed at members of the ILL lab. 

**Using the local install of BLAST**

>Sign into the biochem server on command line/terminal using your credentials (i will not detail how to do this online).
>When you log on you will be in your own student/staff directory. From here you need to navigate to the lab_group folder. An easy way of doing this is -

```bash
cd /Network/Servers/biocldap.otago.ac.nz/Volumes/BiochemXsan/staff_groups/lamontlab/Documents/BLAST

```
> You are now in the BLAST directory, in here there is a bunch of files and folders. NOTE* the path might change if the server is reconfigured, just keep that in mind if it doesnt work in a year or two.

>In this folder there is an output_files and input_files folders - they are self explainatory, each of them contain an instructions file if you wish to read it. You can do this simply by using (when in the folder containing) -

```bash
less INSTRUCTIONS

```

> PLEASE, for any sequence you want to blast, put it as a .txt or .fasta file in the input_sequences file, with your initials and what gene it is - This makes life easier for everyone else. Also make sure you sequence has a fasta header as the first line (although not needed, it makes downstream analysis a lot easier). Denoted by a "**>**" followed by whatever you want to call your sequence.

> To use our BLAST databases

```bash
blastn -db DATABASE -query input_sequences/my_file -perc_identity n -out output_files/myoutput

```

> Currently our BLAST databases for blastn (nucleotide blast) are **AERUGINOSA** and **ClinPsamples**. AERUGINOSA contains all complete genomes from pseudomonas.com, and is quite a big database. ClinPsamples contains all genome assemblies of the 48 clinical isolates obtained from Canada, these are strains from either NZ or Tasmania, and is a nice database to look at variability of genes involved in antibiotic resistance. **PLEASE NOTE when telling blastn which database to use, do not add the file suffixes of .nhr, .nin, .nsq, you just need to tell it the main database name**.

> I have added the perc_identity argument into this code as well, this will enable you to choose a minimum matching percent for the query vs the database. This comes in handy when you are looking at a highly variable sequence (ie: mexT).

> The blast command is very customisable if you want to see what changes you can make then use.

```bash
blastn -h
blastn -help

```

> For protein blasts (blastp) currently there is only the annotated proteins from pseudomonas.com called **AERUGINOSAprot** to perform a protein blast - 

```bash
blastp -db AERUGINOSAprot -query input_files/my_protein.txt -out output_files/my_protein_out

```

> The output from both blastn and blastp (if you have done it correctly) will be in the output_files directory. This output if you stuck to default settings will be in the normal blast output style, now you can look at this using "less" (like the instructions), however its not very interesting. What is interesting however, is converting this file to an aligned multi-fasta file for examination as a multiple alignment of the gene/protein. To do this you will need to use the program mview, which is installed on the server.

```bash

mview -in blast my_output_file -out fasta > my_output_file.fasta

```

> If you get the error something to the effect 'mview command not found', then something has changed on the server and you will need to set the mview binary in your path (handily enough i have prepared for this by including mview in this directory). To do this -

```bash

export PATH=/Network/Servers/biocldap.otago.ac.nz/Volumes/BiochemXsan/staff_groups/lamontlab/Documents/BLAST/output_files/mview-1.60.1/bin/:$PATH

mview -in blast my_output_file -out fasta > my_output_file.fasta

```

> The output will be a nicely aligned multi-fasta file that can be processed however you want.

