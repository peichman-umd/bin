Utility Scripts
===============

## bnodec

Counts the number of blank nodes in an RDF file. Accepts Turtle as input, and
uses rapper to convert it to N-Triples.

    $ bnodec rdf_data.ttl

## callgraph

Uses gprof2dot.py and dot to create a PNG callgraph image from a cachegrind file.

## countelements

    $ countelements file.xml > count.csv

Count the number of occurances of all XML elements in a file. Outputs a 2-column
CSV of the element name and count. Use "-" as the filename to read from STDIN
instead.

## hidiff

Pass a diff through a syntax highlighter (pygmentize) and pager (less) for easy
viewing. All command line arguments are passed directly to diff.

If it detects its output is not a terminal, it instead becomes plain diff. This
makes it safe to use in pipes. (This idea stolen from less.)

## pdfcombine

Combine multiple PDF files into one using ghostscript. The output PDF is sent to
STDOUT.

    $ pdfcombine first.pdf second.pdf third.pdf > output.pdf

## sendkey

    $ sendkey < ~/id_rsa.pub server1 server2 server3

Copy the SSH public key on STDIN to the `~/authorized_keys` file on one or more
servers.
