# names-in-bhl
Sample datasets listing names that are known to occur on given BHL pages. Data could be used to compare with results from name extracting tools such as [GNRD](https://github.com/GlobalNamesArchitecture/gnrd).

## Nomenclator Zoologicus
Mapping between names in the digitised version of [Nomenclator Zoologicus](http://uio.mbl.edu/NomenclatorZoologicus/) from uBio, and BHL PageIDs. For each name the bibliographic citation in Nomenclator Zoologicus has been mapped onto the corresponding page in BHL. The data has four columns:

Column  |  Meaning
--------|-------------------------------------------------------
id      | name id
name    | genus
PageID  | BHL PageID that name occurs on
score   | edit difference between name and closed match on page

### Source project and query
Data comes from my project https://github.com/rdmpage/nomenclator-zoologicus. Query to generate this dump:

```
SELECT nz.id, nz.genus, nz_bhl.PageID, nz_bhl.score 
FROM nz INNER JOIN nz_bhl USING(id);
```

## IPNI
Mapping between plant names in [IPNI](http://www.ipni.org) and BHL, based on my work here: https://github.com/rdmpage/ipni-names. Mapping based on bibliographic data in IPNI, not validated by comparing name with OCR text. IPNI has many duplications of names (often triplications), so names may not be unique.

Column  |  Meaning
--------|-------------------------------------------------------
id      | IPNI Id for name
name    | plant name
PageID  | BHL PageID that name occurs on

### Query
```
SELECT id, `Full_name_without_family_and_authors`, bhl FROM names WHERE bhl IS NOT NULL;
```

 
