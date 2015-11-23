Utility Scripts
===============

## bnodec

Counts the number of blank nodes in an RDF file. Accepts Turtle as input, and
uses rapper to convert it to N-Triples.

    $ bnodec rdf_data.ttl
    
Uses: rapper, awk, grep, sort, uniq, wc

## callgraph

Uses gprof2dot.py and dot to create a PNG callgraph image from a cachegrind file.

Uses: gprof2dot.py, dot

## countelements

    $ countelements file.xml > count.csv

Count the number of occurances of all XML elements in a file. Outputs a 2-column
CSV of the element name and count. Use "-" as the filename to read from STDIN
instead.

Uses: Perl, XML::Parser

## curlpw

    $ curlpw http://example.com/protected

This is a wrapper around `curl` that interactively prompts for a username and
password, then executres `curl` with those credentials. Any command-line
arguments are passed on to the `curl` command as-is.

Uses: curl

## editjson

    $ editjson http://example.com/api/path/to/resource.json

Downloads a JSON file, opens it in an editor of your choice, and then reuploads
the JSON using an HTTP PUT request back to the original URL.

When downloading, it runs the JSON through [jq](https://stedolan.github.io/jq/)
with a default filter of `.`. The filter can be specified as the second
argument. For example, to remove the `badkey` key from the JSON before opening
the editor, you could use:

    $ editjson http://example.com/api/path/to/resource.json 'del(.badkey)'

The editor to use is taken from the `$EDITOR` environment variable. It defaults
to `vim` if there is no `$EDITOR` set.

The PUT request is only sent if the eidted file is non-empty. Therefore, to
cancel the PUT request, delete all of the contents of the file before saving and
quitting your editor.

Uses: curl, jq

## hidiff

Pass a diff through a syntax highlighter (pygmentize) and pager (less) for easy
viewing. All command line arguments are passed directly to diff.

If it detects its output is not a terminal, it instead becomes plain diff. This
makes it safe to use in pipes. (This idea stolen from less.)

Uses: diff, pygmentize, less

## pdfcombine

Combine multiple PDF files into one using ghostscript. The output PDF is sent to
STDOUT.

    $ pdfcombine first.pdf second.pdf third.pdf > output.pdf

Uses: gs

## sendkey

    $ sendkey < ~/id_rsa.pub server1 server2 server3

Copy the SSH public key on STDIN to the `~/authorized_keys` file on one or more
servers.

Uses: ssh

## sshpw

    $ sshpw user@server

Force `ssh` to prompt for a password, and disables public-key authentication.
Any arguments are simply passed through to `ssh`.

Uses: ssh
