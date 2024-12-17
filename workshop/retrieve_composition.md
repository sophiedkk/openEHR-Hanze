# Data ophalen

## Compositie laden

We kunnen door gebruik te maken van de compositie ID die we net hebben teruggekregen ook direct weer de data ophalen uit
openEHR. De openEHR API in EHRBase biedt hier een endpoint voor, maar deze 
Compositie ophalen met `/rest/openehr/v1/ehr/{ehr_id}/composition/{versioned_object_uid}`

````{tab} Bruno
```{figure} ./figures/composition-get-bruno.png
---
name: composition-get-bruno
---
Composities ophalen in Bruno.
```
````
````{tab} Swagger
```{figure} ./figures/composition-get-swagger.png
---
name: composition-get-swagger
---
Composities ophalen in de Swagger UI. Let op: via de Swagger UI kan je alleen XML ophalen, dit komt omdat de header 
altijd accept: application/xml meekrijgt.
```
````
````{tab} Python
```python
import requests

ehr_id = ""
composition_uid = ""
url = f"http://localhost:8080/ehrbase/rest/openehr/v1/ehr/{ehr_id}/composition/{composition_uid}

querystring = {"format":"FLAT"}

response = requests.get(url, params=querystring)

print(response.json())
```
````
````{tab} EHRBase Client
Zie https://docs.ehrbase.org/docs/EHRbase/openEHR-Introduction/Load-Data#ehrbase-client-library
````

---

```{admonition} Opdracht
Haal de compositie uit de vorige stap weer op door gebruik te maken van de openEHR API, probeer de compositie op te 
halen in json, xml, en FLAT format.
```

## AQL

Om uitgebreidere zoekopdrachten te doen moeten we gebruik maken van de Archetype Query Language. Deze taal lijkt veel op
SQL, maar is specifiek gemaakt om openEHR queries mee te schrijven. We kunnen op elk niveau van een EHR queries 
gebruiken, bijv. op het niveau van een EHR, op mappen, specifieke composities, of voor specifieke archetypes. Er kan 
ook gefilterd worden op waarden uit elk niveau. AQL is wel heel verbose, daarom is het het beste om een editor te 
gebruiken die dit kan ondersteunen. Voor de simpele queries die we vandaag zullen doen hebben we echter geen editor 
nodig.

Hieronder zie je een voorbeeld uit de documentatie van openEHR https://specifications.openehr.org/releases/QUERY/latest/AQL.html#_aql_example

```text
SELECT                                                       -- Select clause
   o/data[at0001]/.../items[at0004]/value AS systolic,       -- Identified path with alias
   o/data[at0001]/.../items[at0005]/value AS diastolic,
   c/context/start_time AS date_time
FROM                                                         -- From clause
   EHR[ehr_id/value=$ehrUid]                                 -- RM class expression
      CONTAINS                                               -- containment
         COMPOSITION c                                       -- RM class expression
            [openEHR-EHR-COMPOSITION.encounter.v1]           -- archetype predicate
         CONTAINS
            OBSERVATION o [openEHR-EHR-OBSERVATION.blood_pressure.v1]
WHERE                                                        -- Where clause
   o/data[at0001]/.../items[at0004]/value/value >= 140 OR    -- value comparison
   o/data[at0001]/.../items[at0005]/value/value >= 90
ORDER BY                                                     -- order by datetime, latest first
   c/context/start_time DESC
```

Zoals je ziet ondersteund AQL een aantal standaard clauses die redelijk bekend moeten overkomen. De paden die 
gebruikt worden zijn echter wel heel specifiek voor openEHR. Daarnaast ondersteunt AQL nog veel meer functies en 
operators. Kijk voor meer informatie in de documentatie

### Voorbeeld queries

Om alle EHR IDs uit de database op te halen kan men de volgende query gebruiken:

```sql
SELECT e/ehr_id/value
FROM EHR e
```

````{margin}
```{note}
Het is ook mogelijk om een GET request te sturen, maar dat kom je in de knoop met de maximum lengte van de URL.
```
````
Hiervoor moeten we een POST maken naar de `/rest/openehr/v1/query/aql` endpoint. In de body van de request geven we 
dan de query mee:

```json
{
"q": "SELECT e/ehr_id/value FROM EHR e"
}
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

Om specifieke velden op te halen moet de at-codes gebruikt worden. Deze zijn het makkelijkst op te zoeken in 
Archetype Designer door te klikken op de waarde die je wil gebruiken en dan naar de `Details` tab te gaan. Onder pad 
staat dan de waarde die je kan gebruiken, bijvoorbeeld voor systolische/diastolische druk:
```sql
SELECT
    o/data[at0001]/events[at0006]/data[at0003]/items[at0004]/value as systolic,
    o/data[at0001]/events[at0006]/data[at0003]/items[at0005]/value as diastolic,
    c/context/start_time/value as creation_time
FROM COMPOSITION c
CONTAINS OBSERVATION o[openEHR-EHR-OBSERVATION.blood_pressure.v2]
LIMIT 5
```

---

```{admonition} Opdracht
Maak een API call naar de Query endpoint en probeer een aantal AQL queries. Probeer in ieder geval de bovenstaande queries
en minimaal één datapunt uit een andere observation. Probeer ook de ORDER BY clause te gebruiken. Hoe kun je op 
meerdere observaties selecteren?
```