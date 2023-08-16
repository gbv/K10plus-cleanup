# K10plus cleanup

This repository contains scripts to clean up PICA records in K10plus catalogue.

Analysis of K10plus catalogue with QA Catalogue reveals some commit errors such
as typos and wrongly used fields. Some of these can automatically be fixed
using Catmandu and [Catmandu::PICA].

## Installation

Requires Catmandu and current version of [Catmandu::PICA] as listed in `cpanfile`. Install with:

    cpanm --installdeps .

## Usage

    catmandu convert pp --fix ddc-edition.fix to pp < records.pp

## See also

- [Catmandu::PICA]
- [https://pro4bib.github.io/pica/](Einführung in die Verarbeitung von PICA-Daten)

[Catmandu::PICA]: https://metacpan.org/release/Catmandu-PICA
