# EHRBase gebruiken

## Wat is EHRbase

Er zijn verschillende vendors die op openEHR gebaseerde systemen aanbieden. Een deel hiervan biedt hun implementatie
van de openEHR standaard aan als open-source software. De bekendste open-source variant is [EHRbase](https://github.com/ehrbase/ehrbase)
dat met name wordt onderhouden door [vitagroup](https://www.vitagroup.ag/en/). EHRBase heeft een implementatie van de 
openEHR server en werkt met het laatste referentiemodel en de laatste versie van de Archetype Definition Language (ADL). 
De openEHR REST API en de Archetype Query Language om queries te kunnen maken op de database zijn ook beschikbaar. 

## Optie 1: De sandbox 🏖️

Verschillende openEHR vendors zoals CODE24 en vitagroup bieden nu een sandbox aan. De EHRbase 
sandbox van vitagroup is te vinden op [https://sandkiste.ehrbase.org/](https://sandkiste.ehrbase.org/). Om gebruik te
kunnen maken van de sandbox kan je een gratis account maken. Nadat je je e-mail hebt bevestigd kan je inloggen op de
sandbox. Let wel op dat dit een gedeelde omgeving is, dus zet geen privacy- en bedrijfsgevoelige informatie in deze
omgeving!

De testserver URL kan je vinden op het dashboard van de sandkiste omgeving. Deze URL kan je gebruiken om calls te maken
naar de openEHR REST API. Voor het maken van de calls is geen authenticatie nodig.

```{figure} ./figures/testserver_URL_example.png
---
height: 150px
name: testserver_URL_example
---
Voorbeeld van de testserver URL. Een deel is weggehaald: log in op de sandkiste om de URL
op te halen.
```

## Optie 2: Zelf installeren 👷

Om EHRbase te kunnen gebruiken op je eigen systeem heb je docker nodig. Als je nog geen ervaring hebt
met docker is het handig om de sandbox te gebruiken. Voor meer informatie over docker en hoe het
te installeren, kijk op de [website](https://docs.docker.com/).

Download eerst de [docker compose file](../docker-compose.yml) en de [environment file](../.env.ehrbase). De bestanden 
in deze workshop zijn iets aangepast ten opzichte van de EHRbase Github versie om zeker te weten dat we 
een versie hebben die werkt voor de workshop. De laatste versie kan je altijd vinden via de 
[documentatie](https://docs.ehrbase.org/) van EHRbase.

Nu kun je de containers starten met docker compose:
```shell
docker compose up
```
De server is nu beschikbaar op `http://localhost:8080/ehrbase/`. De instellingen zoals het wachtwoord voor de database 
server en die van de openEHR server staan in de environment file. Voor nu niet heel belangrijk want we gaan geen authenticatie
gebruiken, maar voor echt gebruik natuurlijk wel.

---

```{admonition} Opdracht
Maak een account op de sandbox óf start zelf een EHRBase instantie met docker.
```