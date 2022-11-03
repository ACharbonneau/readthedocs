# Data sources

CDA currently collects data from 3 sources:
- [GDC](https://portal.gdc.cancer.gov/)
- [PDC](https://pdc.cancer.gov/pdc/)
- [IDC](https://portal.imaging.datacommons.cancer.gov/)

and because of this there may be limitations on the information for a given patient.


## Data extraction and release information
To identify the current version and release dates for each of the database, you can run the following command:

```
r = Q.sql("SELECT option_value FROM `gdc-bq-sample.integration.INFORMATION_SCHEMA.TABLE_OPTIONS` WHERE table_name = 'all_v1'")
strings = r[0]['option_value'].split('\\n')
new_strings = []

for string in strings:
    new_string = string.replace('\"', '')
    new_strings.append(new_string)
print(new_strings)
```

Which will produce the following output:
[GDC data version - v34.0, GDC extraction date - 09/29/2022, PDC data version - v2.10, PDC extraction date - 09/29/2022, IDC data version - v.10.0, IDC extraction date - 09/29/2022  ]
