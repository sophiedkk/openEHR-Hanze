# Composities plaatsen

## Compositie maken

Er zijn veel verschillende manieren om composities te maken. In principe kan je deze genereren uit de template, maar dat
te veel werk voor nu. Er zijn verschillende tools die voorbeelden kunnen genereren:
- Cabolabs
- openEHR SDK
- [VS Code](https://marketplace.visualstudio.com/items?itemName=NedapHealthcare.openehr-adl-lsp) 
- MedBlocks
- EHRBase example
- EHRScape example
- ...

De EHRBase API kan ook een voorbeeld compositie genereren uit een template. Deze API ondersteund op dit moment echter alleen
XML `/definition/template/adl1.4/{template_id}/example`. Op zich is XML een prima format, maar het is niet heel fijn om met 
de hand aan te passen. Voor deze workshop zullen we daarom kiezen uit het FLAT format. EHRBase ondersteund dit format op 
dit moment alleen in de (deprecated) EhrScape API `/rest/ecis/v1/template/{templateId}/example`.

````{tab} Bruno
```{figure} ./figures/template-example-bruno.png
---
name: template-example-bruno
---
Template voorbeelden genereren in Bruno.
```
````
````{tab} Swagger
```{figure} ./figures/template-example-swagger.png
---
name: template-example-swagger
---
Template voorbeelden genereren in Swagger UI.
```
````
````{tab} Python
```python
import requests

template_id = "workshop-example"
url = f"http://localhost:8080/ehrbase/rest/ecis/v1/template/{template_id}/example"

querystring = {"format":"FLAT"}

response = requests.get(url, params=querystring)

print(response.json())
```
````
````{tab} EHRBase Client
TBD
````

---

```{admonition} Opdracht
Genereer een template voorbeeld met de EhrScape API. Gebruik dit voorbeeld vervolgens om een fictief voorbeeld te maken
voor de casus. Pas de waarden in de datavelden aan voor een realistisch voorbeeld.
```

## Compositie plaatsen

Het plaatsen van een compositie kan via de `/rest/openehr/v1/ehr/{ehr_id}/composition` enpoint. Een compositie wordt altijd
geplaatst in een EHR, dus als onderdeel van de endpoint moet men een EHR ID meegeven. Ben je de EHR ID kwijt? Dan kan je 
deze opzoeken door toe zoeken met `subject_id` en `subject_namespace`. Als je deze niet hebt, ben je aangewezen op de 
Query API. De EhrScape API geeft de compositie ID terug via de URL in de respons.

````{tab} Bruno
```{figure} ./figures/composition-post-bruno.png
---
name: composition-post-bruno
---
Composities uploaden in Bruno.
```
````
````{tab} Swagger
```{figure} ./figures/composition-post-swagger.png
---
name: composition-post-swagger
---
TComposities uploaden in de Swagger UI.
```
````
````{tab} Python
```python
import json
import requests

url = "http://localhost:8080/ehrbase/rest/ecis/v1/composition"

querystring = {"format":"FLAT", "templateId":"...", "ehrId":"..."}

with open('composition.json', 'r') as file:
    payload = json.load(file)

response = requests.post(url, json=payload, params=querystring)

print(response.json())
```
````
````{tab} EHRBase Client
Zie https://docs.ehrbase.org/docs/EHRbase/openEHR-Introduction/Load-Data#ehrbase-client-library
````

---

```{admonition} Opdracht
Plaats de compositie in de EHR door gebruik te maken van de openEHR API. Bewaar de identifier die je terugkrijgt na het
plaatsen.
```