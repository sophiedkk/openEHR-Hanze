# EHR aanmaken

Om data te kunnen uploaden in onze EHRBase server moeten we eerst een EHR aanmaken. Elke EHR is gekoppeld aan één persoon.
Vervolgens kunnen we de EHR vullen met data gebaseerd op de templates die we eerder hebben gemaakt. openEHR biedt ook de
mogelijkheid om data te structureren in directories binnen een EHR. 

Als we een EHR aanmaken krijgen we een EHR ID terug. Deze ID geeft op zichzelf heel weinig informatie. Het is ook de bedoeling
dat demografische gegevens op een andere plek worden opgeslagen. openEHR heeft ook archetypes voor demografische data, 
maar er zijn ook veel vendors die gebruik maken van een FHIR server. In dat geval is het ook mogelijk om in de EHR aan 
te geven aan welke externe service de EHR ID gekoppeld is. Vervolgens kunnen we op deze waarde zoeken in de REST API en
met AQL. De specificatie voor de API staat hier: https://specifications.openehr.org/releases/ITS-REST/latest/ehr.html#ehr-ehr-post

## EHR API

````{tab} Bruno
```{figure} ./figures/create-ehr-bruno.png
---
name: create-ehr-bruno
---
Aanmaken van een EHR in Bruno.
```
````
````{tab} Swagger
TBD
````
````{tab} Python
```python
import requests

ehrbase_url = "http://localhost:8080/ehrbase"  # swap this out with sandkiste URL if needed
url = ehrbase_url + "/rest/openehr/v1/ehr"

response = requests.post(url)

print(response.headers)
```
````
````{tab} EHRBase Client
openEhrClient = DefaultRestClientTestHelper.setupDefaultRestClient();
EhrEndpoint ehrEndpoint = openEhrClient.ehrEndpoint();
UUID ehr = ehrEndpoint.createEhr();
````

---

```{admonition} Opdracht
Maak een EHR aan. Sla de EHR id op zodat we deze in een latere stap weer kunnen gebruiken. De EHR id staat verstopt in
de header!
```

## Bonus: EHR met subject ID

Het is de bedoeling dat we klinische data en demografische data van elkaar scheiden. De eerste optie is om de EHR ID bij
de demografische data op te slaan zodat een link kan worden gelegd naar de klinische data. De tweede optie is om aan de
EHR een globally unique identifier (GUID) toe te voegen. Dit kan met dezelfde API en we moeten dan extra informatie 
meegeven in de body:

````{tab} Bruno
```{figure} ./figures/create-ehr-id-bruno.png
---
name: create-ehr-id-bruno
---
Aanmaken van een EHR in Bruno.
```
````
````{tab} Swagger
TBD
````
````{tab} Python
```python
import requests

ehrbase_url = "http://localhost:8080/ehrbase"  # swap this out with sandkiste URL if needed
url = ehrbase_url + "/rest/openehr/v1/ehr"

payload = {
    "_type": "EHR_STATUS",
    "archetype_node_id": "openEHR-EHR-EHR_STATUS.generic.v1",
    "name": { "value": "EHR Status" },
    "subject": { "external_ref": {
            "type": "PERSON",
            "namespace": "{{subject_namespace}}",
            "id": {
                "_type": "GENERIC_ID",
                "value": "{{subject_id}}",
                "scheme": "{{scheme}}"
            }
        } },
    "is_modifiable": True,
    "is_queryable": True
}

response = requests.post(url, json=payload)

print(response.headers)
```
````
````{tab} EHRBase Client
TBD
````

---

```{admonition} Opdracht
Maak een EHR aan met een subject id en namespace. Sla de EHR id op zodat we deze in een latere stap weer kunnen gebruiken.
```
