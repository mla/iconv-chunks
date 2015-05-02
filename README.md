NAME
====
iconv-chunks - Process huge files with iconv

SYNOPSIS
========
iconv-chunks <filename> [iconv-options]

DESCRIPTION
===========
The standard iconv program reads the entire input file into memory,
which doesn't work for large files (such as database exports).

This script is just a wrapper that processes the input file in
manageable chunks and writes it to standard output.

The first argument is the input filename (use - to specify standard
input). Anything else is passed through to iconv.

The real iconv needs to be somewhere in your PATH.

EXAMPLES
========

    # Convert latin1 to utf-8:
    ./iconv-chunks database.txt -f latin1 -t utf-8 > out.txt

    # Input filename of - means standard input:
    ./iconv-chunks - -f iso8859-1 -t utf8 < database.txt > out.txt

    # More complex example, using compressed input/output to minimize disk use:
    zcat database.txt.gz | ./iconv-chunks - -f iso8859-1 -t utf8 | \
    gzip - > database-utf.dump.gz

AUTHOR
======
Maurice Aubrey <maurice.aubrey+iconv@gmail.com>

LICENSE
=======
MIT
