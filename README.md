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

    ./fix $FIX_FILE [$INPUT_FILE] > patches.pp

Some file extensions of input file are detected:

- `*.dat.gz` is gzipped [normalized PICA]
- `*.dat` is [normalized PICA]
- everything else is [PICA Plain]

Script `kxpo` can be used to get K10plus records via SRU in online expansion form:

    ./kxpo 1543420281                           # get via PPN
    ./kxpo pica.isb=9783894017316 --total 1     # get first matching record by ISBN

## Examples

See `*.fix` files in this repository for examples:

- `ddc-edition.fix` - unify DDC edition statementin `045F$e`. [JIRA Issue](https://jira.gbv.de/browse/CBS-1765)
- `bk-74.50.fix` - replace deleted BK class 74.50X. Applied by searching via SRU:

      ./kxpo pica.bkl=74.50X --total 500 | ./fix bk-74.50X.fix > bk-74.50X.pp

## See also

- [https://pro4bib.github.io/pica/](Einführung in die Verarbeitung von PICA-Daten)
  with a section on editing PICA with Catmandu::PICA

[Catmandu::PICA]: https://metacpan.org/release/Catmandu-PICA
[normalized PICA]: https://format.gbv.de/pica/normalized
[PICA Plain]: https://format.gbv.de/pica/plain
