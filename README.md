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

## Examples

See `*.fix` files in this repository for examples:

- `ddc-edition.fix` - unify DDC edition statementin `045F$e`. [JIRA Issue](https://jira.gbv.de/browse/CBS-1765)
- ...

## See also

- [https://pro4bib.github.io/pica/](Einführung in die Verarbeitung von PICA-Daten)
  with a section on editing PICA with Catmandu::PICA

[Catmandu::PICA]: https://metacpan.org/release/Catmandu-PICA
[normalized PICA]: https://format.gbv.de/pica/normalized
[PICA Plain]: https://format.gbv.de/pica/plain

