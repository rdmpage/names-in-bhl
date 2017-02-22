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

### Query
```
SELECT nz.id, nz.genus, nz_bhl.PageID, nz_bhl.score 
FROM nz INNER JOIN nz_bhl USING(id);
```


