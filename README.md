# Important Notes

This project is still in development, and the idea is to make my job as a QA engineer automating tests related to EPCIS easier. I figured if I need this, someone else might need as well. This is my first Python package, any problems, doubts or suggestions, either comment on the [Github repository](https://github.com/Violeta-Carvalho/EPCIS-Dummy-Generator), or send me an [email](mailto:violetadecarvalho@gmail.com).

# Companies
EPCIS data related to companies.

## Generate Company Prefix

`generate_company_prefix(length: int)`

Randomly generates a company prefix (str) with a length that varies from 6 to 12, 7 is default.

# Items
EPCIS data related to items.

## Generate GTIN

`generate_gtin(company_prefix: str, company_prefix_length: int)`

Randomly generates a GTIN (str) with a length of 14. You must either inform `company_prefix` or `company_prefix_length`, if only `company_prefix_length` is informed, it generates a `company_prefix` with the `generate_company_prefix` function before generating the GTIN. Then, it generates the check digit.

## Get Company Prefix and GS1 ID from GTIN

`get_company_prefix_and_gs1_id_from_gtin(gtin: str, company_prefix_length: int)`

Reads the GTIN (str) and returns a dictionary with the following template:

```
{
    "gs1_id": <gs1_id>,
    "company_prefix": <company_prefix>
}
```

You must inform both `gtin` and `company_prefix_length`.

## Generate SGTIN

`generate_sgtin(serial: str, gtin=None, company_prefix=None, company_prefix_length=None)`

Generates an SGTIN based on serial informed and `gtin` and `company_prefix` informed. If no `gtin` is informed, it generates one with the `generate_gtin` function, using either the `company_prefix`. If only `company_prefix_length` is informed it generates `company_prefix` with the function `generate_company_prefix`.

# Locations
EPCIS data related to locations.

## Generate GLN

`generate_gln(company_prefix: str, company_prefix_length: int)`

Randomly generates a GLN (str) with a length of 13. You must either inform `company_prefix` or `company_prefix_length`, if only `company_prefix_length` is informed, it generates a `company_prefix` with the `generate_company_prefix` function before generating the GLN. Then, it generates the check digit.

## Generate SGLN

`generate_sgln(serial: str, gln=None, company_prefix=None, company_prefix_length=None)`

Generates an SGLN based on serial informed and `gln` and `company_prefix` informed. If no `gln` is informed, it generates one with the `generate_gln` function, using either the `company_prefix`. If only `company_prefix_length` is informed it generates `company_prefix` with the function `generate_company_prefix`.

# Utils
Functions unrelated to EPCIS, but which are used by EPCIS-related functions.

## Generate X Length Number

`generate_x_length_number(x: int)`

Generates a string made of X digits. Used to randomly generate Company Prefixes and GS1 IDs.

## Calculate Check Digit

`calculate_check_digit(base: str)`

Calculates check digit based on Modulo 10 rule, using the base, a string made entirely of digits.