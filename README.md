# gtool
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
