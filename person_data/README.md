# Que es Eso?

This is the raw data from the census bureau. 

Also, here's [a link to the Google Sheets document for the Excel file](https://docs.google.com/spreadsheets/d/1NKtcz7-bDs0b8OyygSwJgVmwQSogtrLfswWDc8GV_Kg/edit?usp=sharing).

Note I am going to be operating on the file named `census_2000_last-1000_names_Titlecase.txt` which limits my edge cases quite a bit.

## RegEx Conversion

### Initial Search & Replace

#### Just Names

To strip out everything after the name, use the following RegEx:

* Find: `^(\w+)\s*\d.*`
* Replace: `$1`

#### Title case

To convert name data such that the first letter is capitalized and the rest of the name is lower-cased:

* Find: `^(\w)(\w+)`
* Replace: `$1\L$2`

### Additional Search & Replace

For Scottish/Irish surnames, here are some RegEx's to apply.

#### MacD/McD

* Find: `^(Mac|Mc)d(\w+)`
* Replace: `$1D\L$2`

#### McC

* Find: `^(Mcc)(\w+)`
* Replace: `McC$2`

#### O'Brien:

* Find: `^(O)b(\w+)`
* Replace: `$1'B\L$2`

#### O'Co...

O'Connel, O'Connor, etc.

* Find: `^(O)co(\w+)`
* Replace: `$1'Co\L$2`

O'Donnell

* Find: `^(O)don(\w+)`
* Replace: `$1'Don\L$2`
