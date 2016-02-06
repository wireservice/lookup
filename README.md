lookup
======

A repository of lookup tables.

Rules:

* Must have journalistic value.
* Must be created from a primary source.
* Must be in standardized CSV format. (Run through in2csv)
* Must map unique keys to unique values.
* Keys must be durably unique: not vulnerable to mispellings
* Underscores in filenames and column names.
* 250KB file limit.
* No periods in filenames other than specified delimiters.

Metadata format:

```
dataset: USPS to state name
description: TKTK
version_description: N/A
origin: Census Bureau
origin_url: TKTK
contributor: Christopher Groskopf
contributor_email: chrisgroskopf@gmail.com
columns:
  usps: Text
  state: Text
```
