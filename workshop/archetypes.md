# Archetypes

In openEHR is een archetype een specificatie voor het vastleggen van patiëntgegevens volgens 
het referentiemodel. Archetypes vormen de basis van de openEHR-architectuur en worden samen met clinici en 
domeindeskundigen geformuleerd. Ze definiëren afzonderlijke klinische concepten inclusief alle relevante 
data-elementen en worden breed en flexibel opgezet voor maximale interoperabiliteit. openEHR streeft voor
een maximale dataset en tijdens het maken van templates kunnen bepaalde datavelden worden uitgezet. Archetypes
worden vastgelegd in de Archetype Definition Language (ADL).

## Clinical Knowledge Manager

Het lezen van een ADL template in een text editor is niet heel fijn. Daarom zijn er gelukkig ook andere manieren om 
archetypes in te zien. De internationale [Clinical Knowlege Manager](https://ckm.openehr.org/ckm/) bevat alle 
archetypes die zijn vastgesteld door de internationale openEHR community. 

```{figure} ./figures/ckm.png
---
name: ckm
---
De internationale Clinical Knowledge Manager. 
```

## Archetypes ontdekken

De CKM is ook een goede manier om archetypes te ontdekken en te inspecteren. Wanneer je in de linkerkolom een 
archetype selecteert opent er een tabblad met daarin alle informatie over het archetype. Hier kan
men onder andere zien waar het archetype voor is bedoeld en waar het expliciet niet voor is bedoeld.
Onder het tabbladen Data, State, Protocol, en Events staan de velden die beschikbaar zijn in dit archetype.
Hierbij wordt waar mogelijk verwezen naar de SNOMED-CT en LOINC codes die bij elk concept horen.

Door op het mindmap symbool te klikken krijg je een handig overzicht van het archetype:

```{figure} ./figures/blood_pressure_archetype.png
---
name: blood_pressure
---
Het [blood pressure archetype](https://ckm.openehr.org/ckm/archetypes/1013.1.3574/mindmap) in de Clinical Knowledge Manager in de Mind Map view.
```

## Archetypes exporteren

Als we het juiste archetype hebben gevonden kunnen we deze exporteren met de download knop. Om zeker te weten dat de 
editor die we gebruiken het format ondersteund kiezen we voor `ADL`. Dit proces kun je nu herhalen totdat je alle 
archetypes hebt gevonden die je nodig hebt. 

### Bulk export

Normaliter zou je gewoon alle archetypes kunnen exporteren en daarna kunnen gebruiken. Het inlezen van de 900+
archetypes in ADL Designer duurt echter best lang. Daarom is het voor deze workshop aan te raden om de archetypes 
die je nodig hebt te downloaden en daarmee verder te werken.

```{figure} ./figures/bulk_export.png
---
name: bulk_export
---
De internationale Clinical Knowledge Manager. 
```

Wanneer je wel van bulk export gebruik wil maken kan je onder het archetype tabblad (in het centrale paneel bovenaan)
de `Bulk Export` knop vinden. Daarna kan je aanvinken wat je wel en niet nodig hebt. Alle archetypes zullen in een .zip 
bestand gedownload worden. Met dit bestand (of dus de losse bestanden) gaan we verder in de volgende stap.

---

```{admonition} Opdracht
Zoek en download de archetypes die je denkt nodig te hebben voor de {doc}`opdracht` in het ADL format. Download 
ook het archetype voor Encounter, deze hebben we nodig om onze compositie mee te maken. Bewaar de documenten op een plek 
waar je ze later terug kan vinden.
```