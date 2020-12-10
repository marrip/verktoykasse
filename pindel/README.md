# Pindel

Pindel is a tool to detect InDels and larger SVs in NGS data. It is highly
cited but not maintained anymore. The docker image is using an older version
of the samtools repository and the second latest version of the pindel
repository. Pindel requires a config file as input which should look like this:

```
/Path/to/bam [insert_size] [sample_name]
...
```

Pindel generates a number of output files in a special pindel format. To
obtain `vcf` files for downstream analysis, a convenience script is included
`pindel2vcf`.

## Usage

Generally, the input for pindel should be a file containing aligned reads in
`bam` format and a reference `fasta` file. Start by indexing the `fasta` and
including your `bam` files in a config file:

```
samtools faidx [reference.fasta]
echo -e "[bam_file]\\t[insert_size]\\t[sample_name]" >> pindel.cfg
```

Now you can run `pindel`:

```
pindel 
```

Finally, combine the output files into one vcf:

```
pindel2vcf
```
