# python-interview-assignment

The following is a description of a coding assignment that is designed
to be aligned with the Open FDA project you're going to be working on.
Please use Python 2 and any open-source libraries and IDE of your choice.
 
[udi.xml](udi.xml) contains a small portion of the FDA's Global
Unique Device Identification Database (GUDID) data set. It is
self-descriptive: root XML element contains a number of `device`
records. Please write Python code that will perform the following:

- Parse the XML and transform it into a JSON object (no strict
  requirement on the schema of resulting JSON, as long as it properly
  represents the UDI data set). Within the scope of this assignment, it
  is OK to use `String` as the target data type for JSON elements.
- As you transform, please rename the camel-cased fields in XML into their
  underscore-cased equivalents, e.g. `versionModelNumber` → `version_model_number`
- As you transform, please omit empty XML elements (e.g. `<catalogNumber
  />`) from the resulting JSON.
- Save JSON to disk.
 
**Test**

Please demonstrate your use of unit tests (write at least one small
test).
 
**Optional Task: Harmonization**

- `foiclass.txt` contains FDA's classification information for medical
  devices. The key element here is the 3-letter product code, e.g. `BRW`
- As you process the UDI XML, you _may_ encounter references to product
  codes, such as in this example:
```
    <productCodes>
      <fdaProductCode>
        <productCode>JEY</productCode>
        <productCodeName>Plate, Bone</productCodeName>
      </fdaProductCode>
    </productCodes>
```
- For every such occurrence, retrieve product code classification
  information from `foiclass.txt` and insert it into JSON as an
  additional `openfda` field (structure of your choice), for example:
```
    "product_codes": [
      "fda_product_code": {
        "product_code": "JEY,
        "product_code_name": "Plate, Bone"
        "openfda": "DE|DE|JEY|Plate, Bone|2||N|N||872.4760|1|||||Y|N"
      }
    ]
```


 