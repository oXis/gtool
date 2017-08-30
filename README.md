# Introduction
When doing bioinformatics/genomics you always manipulate fasta files (at least I do) and often you need the size/GC content of your genomes as a quick check. Or after a blast you have the coordinates of a match and you want to extract the sequence for future analysis. This why I wrote this small script.

# Deps
- Python 3

# Usage
The script takes a file, list of files or can read from `stdin` using `-` as input.

```
$ ./gtool.py --help
usage: gtool.py [-h] [-s] [-g] [-c CONTIG] [-e start stop] seqIn [seqIn ...]

positional arguments:
  seqIn                 Genome, list of genome or stdin (uses '-' for stdin)

optional arguments:
  -h, --help            show this help message and exit
  -s, --size            Show size.
  -g, --gcontent        Show GC content.
  -c CONTIG, --contig CONTIG
                        Specify contig to work on, supports regular
                        expressions.
  -e start stop, --extract start stop
                        Extract sequence from START to STOP, works only with
                        -c and stops at the first match.

```

# Examples
I've provided two fasta files to work on.
### Show size
```
$ ./gtool.py -s A.fasta
SeqName: A
    Contig: 3
    Size: 924
```

### Show size and GC content of all fasta files
```
$ ./gtool.py -sg *.fasta
SeqName: A
    Contig: 3
    Size: 924
    GC%: 48.16
SeqName: B
    Contig: 2
    Size: 1302
    GC%: 47.31
```

### Show size and GC content of `contig2`, read from `stdin`
```
$ cat A.fasta | ./gtool.py -sg -c contig2 -
SeqName: stdin
    Contig: contig2
    Size: 252
    GC%: 53.97
```

### Extract sequence from 10 to 35 on `contig1`, with and without output

```
$ ./gtool.py -sg -c contig1 -e 10 35 B.fasta
SeqName: B
    Contig: contig1 Some prot
    Size: 26
    GC%: 57.69
    Seq: GTATCGGGTAGGTGACTGCGACGAGA
```
```
$ ./gtool.py -c contig1 -e 10 35 B.fasta
>contig1 Some prot
GTATCGGGTAGGTGACTGCGACGAGA
```

# Supports
Open a issue :)
