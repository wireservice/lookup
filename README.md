# lookup

A repository of journalist's lookup tables. Designed for programmatic access using tools such as [agate-lookup](TKTK).

Anyone may contribute a lookup table by sending a pull request to this repository.

## Structure of files

Each folder is a key that can be used for a lookup. Within that folder are CSV files. The name of the CSV file is the name of the value that it maps to. The CSV itself will contain two columns, one with the key and another with the value. For example, `usps/state.csv` contains a CSV file that looks like this:

```
usps,state
AL,Alabama
AK,Alaska
AZ,Arizona
...
```

Sometimes the mapping from a key to value varies over time. For example, NAICS codes change every five years. In this case, a version specifier may be included in the filename. For example, `naics/description.2007.csv` is the 2007 version of the code mapping and `naics/description/2012.csv` is the 2012 version.

It may also be useful to be able to map two keys to a single value. For example, you might want to look up population by state *and* year. In those cases key folders can be nested and the CSV can contain more than one key column. For example, `usps/year/population.csv` contains a CSV that looks like this:

```
usps,year,state
AL,2015,4858979
AL,2014,4846411
AL,2013,4830533
...
```

## Metadata format

Each CSV table must be accompanied by a YAML file. That file must have an identical filename, plus the `.yml` extension. For example, the table `fips/state.csv` must be accompanied by `fips/state.csv.yml`. This file should contain the following metadata:

```yaml
description: A description of the data, including any notes necessary to use it correctly.
version_description: A description of the specific version of the data.
origin: The source of the data, such as "United States Census Bureau"
origin_url: A link to the source of the data. Be as specific as possible.
contributor: The name of the person submitting the data.
contributor_email: The email address of the person submitting the data.
columns:
  key_column_name: Agate column type, such as "Text" or "Number"
  value_column_name: Agate column type, such as "Text" or "Number"
```

## Rules for including data

Anyone may submit a pull request to add a table to this repository, however, the following rules will guide inclusion of any data:

* The data must have journalistic value.
* The data must be from an authoritative source.
* The CSV must be in "standardized" CSV format. (Run through [in2csv](http://csvkit.readthedocs.org/en/latest/scripts/in2csv.html).)
* All keys must be unique. (No split/combine crosswalks.)
* All keys must be proper identifiers, not names.
* All filenames and keys must use `snake_case`.
* Periods must not be used in filenames or keys except as defined above.
* Four digit years must be used everywhere.
* Each CSV must be 250KB or less.
