# BreakDancer

BreakDancer can detect SVs in next generation paired-end sequencing data.
Unfortunately, it is not actively maintained anymore. We are using the
last commit on the `master` branch to ensure proper compilation. The tool
comes with a convenience script `bam2cfg.pl` which is written in `perl`
and requires some dependencies which we need to install using `cpan`.

## Usage

After aligning your reads using `BWA`, you can go about to generate the
config file, breakdancer requires, like so:

```
bam2cfg.pl /path/to/sample.bam 1> sample.cfg
```

The generated config file can in turn be utilized in a breakdancer run:

```
breakdancer-max sample.cfg > output.vcf
```
