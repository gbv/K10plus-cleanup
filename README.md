# K10plus cleanup

This repository contains scripts to clean up PICA records in K10plus catalogue.

Analysis of K10plus catalogue with **QA Catalogue** reveals errors such as
typos and wrongly used fields. Some of these can automatically be fixed using
Catmandu and [Catmandu::PICA].

## Installation

Requires Catmandu and current version of [Catmandu::PICA] as listed in `cpanfile`. Install with:

    cpanm --installdeps .

## Usage

Create or reuse a `.fix` file in Catmandu fix language. Either call `catmandu`
as documented with selected data source (e.g. records retrieved via unAPI or
SRU or a plain PICA dump file) or use the tiny shell script `fix`:

    ./fix $FIX_FILE [$INPUT_FILE] [$OUTPUT_FILE]

The default output file name is fix file name with extension changed to `.patch`changed to .

Some file extensions of input file are detected:

- `*.dat.gz` is gzipped [normalized PICA]
- `*.dat` is [normalized PICA]
- everything else is [PICA Plain]

Script `kxpo` can be used to get K10plus records via SRU in online expansion form:

    ./kxpo 1543420281                           # get via PPN
    ./kxpo pica.isb=9783894017316 --total 1     # get first matching record by ISBN

To validate a Patch file and give statistics run (given `$patchfile` has extension `.patch`):

    picadata count $patchfile
    picadata fields $patchfile

## Examples

See `*.fix` files in this repository for examples:

fix file | description | JIRA issue
---------|-------------|------------
[ddc-edition.fix](ddc-edition.fix) | unify DDC edition statementin `045F$e` | <https://jira.gbv.de/browse/CBS-1765>
[bk-74.50.fix](bk-74.50.fix) | deleted BK class `74.50X` | <https://jira.gbv.de/browse/CBS-1766>
[bk-remove-invalid.fix](bk-remove-invalid.fix) | remove invalid BK notation `XX.XX` | <https://jira.gbv.de/browse/CBS-1767>

## See also

- [Einführung in die Verarbeitung von PICA-Daten](https://pro4bib.github.io/pica/)
  with a section on editing PICA with Catmandu::PICA

[Catmandu::PICA]: https://metacpan.org/release/Catmandu-PICA
[normalized PICA]: https://format.gbv.de/pica/normalized
[PICA Plain]: https://format.gbv.de/pica/plain
