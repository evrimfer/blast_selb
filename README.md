# BLASTp for SelB Protein

# 2022-06-28
1. Go to NCBI Protein database. Search for E.coli SelB protein. Selected the first result and download protein fasta file. Accession ID is CAD5999244.1

2. Install Blastp using Miniconda. (blastp: 2.12.0+)
    ```
    conda install -c bioconda blast

    #version check
    blastp -version
    ```
3. Find homolog sequences for SelB using BlastP
-query : the query fasta file 
-db: ncbi database we used (nr: non-redundant)
....details details
``` 
blastp -query ecoli_selb.fasta -db nr -out selb_hits1.csv -outfmt '10 qstart qend sstart send sacc ssciname stitle evalue qlen sseq' -evalue 0.00000001 -max_target_seqs 50 -remote
```
4. Retrieve the accession and sequence from csv file and reformat into fasta
```
    while read -r line; do id=`echo $line | cut -d',' -f5`; seq=`echo $line | cut -d',' -f10`;echo '>'$id"\n"$seq; done < selb_hits1.csv > selb_hits2.fasta 
```
error for single quotes because of copy-pasting, delete single quotes and write again 

askdalfa

