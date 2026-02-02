---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/app-panel-guide/app-builder-user-interface/validation-pattern-for-strings
---

# Validation pattern for strings

A Validation Pattern can be set in the App Builder to ensure the user is inputting a parameter setting in the proper format.  This will be present for input parameters that are strings. &#x20;

Validation patterns are regular expressions, as described [here](https://json-schema.org/understanding-json-schema/reference/regular_expressions).

`^` matches as the beginning of the string, `$` matches at the end of the string.  Using both will ensure the parameter value entered matches the entire string and not part of the string. `+` matches the previous pattern one or more times, `*` matches the previous pattern 0 or more times.&#x20;

Here are some common examples:

* Alphanumeric characters with underscores or dashes, but no spaces: `^[a-zA-Z0-9]+[_]`_`[-]`_`[a-zA-Z0-9]*$`
* Any file name with a fasta extension: `^\S+.fn?a(sta)?(.gz)?$`
* Any file name with a GTF extension: `^\S+.gtf(.gz)?$`
* A csv, tsv, or txt file: `^\S+.(csv|tsv|txt)$`

&#x20;&#x20;
