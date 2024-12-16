# Data ophalen

## Compositie laden

We kunnen door gebruik te maken van de compositie ID die we net hebben teruggekregen ook direct weer de data ophalen uit
openEHR. De openEHR API in EHRBase biedt hier een endpoint voor, maar deze 
Compositie ophalen met `/rest/openehr/v1/ehr/{ehr_id}/composition/{versioned_object_uid}`

````{tab} Bruno
```{figure} ./figures/composition-get-bruno.png
---
name: composition-post-bruno
---
Composities uploaden in Bruno.
```
````
````{tab} Swagger
```{figure} ./figures/composition-get-swagger.png
---
name: composition-post-swagger
---
TComposities uploaden in de Swagger UI.
```
````
````{tab} Python
```python

```
````
````{tab} EHRBase Client
Zie https://docs.ehrbase.org/docs/EHRbase/openEHR-Introduction/Load-Data#ehrbase-client-library
````

---

```{admonition} Opdracht
Haal de compositie uit de vorige stap weer op door gebruik te maken van de openEHR API. Haal dezelfde compositie ook op
door gebruik te maken van de EhrScape API in FLAT format.
```

## AQL

Om alle EHR IDs uit de database op te halen kan men de volgende query gebruiken:
```sql
SELECT e/ehr_id/value
FROM EHR e
```

Om alle composities op te halen die we net hebben gepost met hun respectievelijke EHR IDs kunnen we de volgende query
gebruiken:
```sql
SELECT e/ehr_id/value, c/uid/value 
FROM EHR e 
    CONTAINS COMPOSITION c 
WHERE 
    c/name/value = 'workshop-example'
```

{
"q": "SELECT e/ehr_id/value, c/uid/value FROM EHR e CONTAINS COMPOSITION c WHERE c/name/value = 'workshop-example'"
}

