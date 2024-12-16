# openEHR

## Wat is openEHR?

openEHR is een open standaard die ontworpen is om de interoperabiliteit van elektronische patiëntendossiers (EPD's) te 
verbeteren. Het biedt een raamwerk voor het modelleren, opslaan en delen van gezondheidsgegevens op een flexibele manier. 
Een **openEHR CDR** (Clinical Data Repository) is een opslagomgeving die is ontworpen volgens de openEHR-standaard. De 
kern van openEHR is een tweelaags architectuur: een referentiemodel voor de technische structuur van gegevens en archetypen 
voor de klinische inhoud. Dit stelt zorgprofessionals in staat om domeinspecifieke kennis vast te leggen zonder 
afhankelijk te zijn van specifieke software. Dankzij deze aanpak wordt het eenvoudiger om gegevens uit verschillende 
systemen te integreren, uit te wisselen, en langdurig bruikbare, patiëntgerichte informatie te waarborgen.

```{figure} ./figures/about-openehr-diagram.svg
---
name: about-openehr-diagram
width: 60%
---
Een overzicht van het openEHR ecosysteem, bron: https://openehr.org/about_us
```

## Hoe werkt openEHR?

In de rest van de workshop zullen we uitgebreid ingaan op hoe openEHR precies werkt en hoe we aan de slag kunnen met 
openEHR. Het is echter ook goed om eerst een globaal overzicht te hebben. Hiervoor zijn een aantal concepten belangrijk.
Allereerst de archetypes en templates die nodig zijn om klinische modellen mee te maken. Vervolgens is het interessant
om te kijken hoe openEHR daadwerkelijk werkt als CDR. Een aantal concepten zal ik hier al noemen zodat het niet 
helemaal uit de lucht komt vallen en het straks duidelijk is wat we gaan doen.

## Wat zijn archetypes?

Archetypes zijn de **bouwstenen** waarmee openEHR werkt. Deze worden vastgelegd door mensen met domein kennis. Het proces 
waarin deze archetypes worden gedefinieerd kan worden gevolgd op de website van de **Clinical Knowledge Manager** (CKM) 
van openEHR. Sommige landen hebben hun eigen CKM. Een archetype probeert zo compleet mogelijk te zijn omdat het probeert een 
'maximale dataset' te faciliteren. Er is één archetype per klinisch concept en ze kunnen referenties bevatten naar 
klinische terminologieën zoals SNOMED CT. We zullen later zien dat we veel van de mogelijkheden van een archetype niet 
zullen gebruiken en deze uit zullen zetten.

Het is in principe niet de bedoeling dat iedereen maar archetypes gaat maken. Het doel is namelijk om een gestandaardiseerde 
set te hebben die iedereen kan gebruiken - anders verlies je de interoperabiliteit. We zullen in deze workshop dus geen 
archetypes maken, maar we gaan er wel een aantal gebruiken uit de CKM. In Nederland hebben we hiervoor nog geen strikt 
governance model voor opgericht, maar dit zal in de toekomst wel moeten.

Een voorbeeld van een tool waarin men archetypes kan maken is de [Archetype Designer](https://tools.openehr.
org/designer/). Deze tool wordt beschikbaar gesteld door Better en OpenEHR International. Deze tool zullen we in de 
workshop ook gebruiken.

## Wat zijn templates?

In templates past men archetypes toe in een bepaalde situatie of context - een klinisch scenario. Hierdoor kan een organisatie
flexibel inspelen op hun behoeften en tegelijkertijd interoperabiliteit bewaren doordat ze werken met archetypes. Als
archetypes de bouwstenen zijn, dan zijn templates de bouwtekeningen. In het template kunnen we vastleggen welke archetypes
we willen zien, welke eenheden mensen moeten gebruiken, welke velden er gebruikt moeten worden, etc. Door specifieke velden
te selecteren gaan we van een maximale dataset naar een klinisch relevante dataset.

Templates maken kan op een aantal verschillende manieren. In deze workshop zullen we de eerdergenoemde Archetype Designer 
gebruiken om zelf templates te maken. Vervolgens moet men de templates registreren op de openEHR server zodat men 
later data kan plaatsen volgens dit template. Templates registreren we met de openEHR API.

## Wat zijn composities?

Composities vormen de daadwerkelijke data die wordt opgeslagen in openEHR volgens de structuur in het template. Composities 
die in openEHR opgeslagen zijn zijn 'immutable': Het is niet de bedoeling dat we de compositie nog aanpassen. Elke 
aanpassing of nieuwe meting wordt geregistreerd met een nieuwe compositie. Hierdoor zorgen we dat er een coherent 
overzicht in het dossier ontstaat gebaseerd op losse events. We zullen composities dus tegenkomen op het moment dat we
data willen opslaan of ophalen.
