# REST API gebruiken

De documentatie van de openEHR API van EHRBase is te vinden op https://docs.ehrbase.org/api/hip-ehrbase/ehr. Bij gebruik
van een lokale EHRBase instantie is de documentatie ook te vinden op 
http://localhost:8080/ehrbase/swagger-ui/index.html. Het voordeel van de **Swagger UI** is dat je hier ook direct 
API calls mee kan testen. Op het moment van schrijven doet de Swagger UI op de EHRBase Sandbox het helaas niet. Om toch 
de documentatie in te zien kan men gebruik maken van de documentatie van EHRBase. API calls moet men dan maken met 
bijv. een API client. EHRBase implementeert de officiële openEHR API volgens de specificatie op 
https://specifications.openehr.org/releases/ITS-REST/Release-1.0.3/ehr.html, dit is onderdeel van de 
openEHR standaard:

```{figure} ./figures/openehr_block_diagram.svg
---
width: 60%
name: openehr_api
---
Afbeelding uit de openEHR REST documentatie. De REST API is onderdeel van de openEHR standaard en worden ook als zodanig
aangeboden door openEHR vendors.
```

Oudere versies van EHRBase ondersteunde ook de ecis API endpoint (ook wel de **EhrScape API**). Hierdoor was het 
mogelijk om bijvoorbeeld composities in FLAT format te posten. Deze endpoint is echter in een recente versie 
verwijderd omdat er overlap in zit met de officiële API. Bepaalde vendors voegen ook andere endpoints toe aan de API 
of geven extra opties mee. Op zich mag dit van de specificatie wel, maar hierdoor kan het zijn dat je verschillende 
methoden online kan vinden om hetzelfde te bereiken.

---

```{admonition} Opdracht
Open de API documentatie en zoek naar de endpoint om een Template te uploaden. Hoe werkt deze API en hoe zou jij hem 
gebruiken?
```
