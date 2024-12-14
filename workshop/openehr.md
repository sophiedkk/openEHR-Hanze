# openEHR

## Wat is openEHR?

openEHR is een open standaard die ontworpen is om de interoperabiliteit van elektronische patiëntendossiers (EPD's) te 
verbeteren. Het biedt een raamwerk voor het modelleren, opslaan en delen van gezondheidsgegevens op een flexibele manier. 
Een openEHR CDR (Clinical Data Repository) is een opslagomgeving die is ontworpen volgens de openEHR-standaard. De kern 
van openEHR is een tweelaags architectuur: een referentiemodel voor de technische structuur van gegevens en archetypen 
voor de klinische inhoud. Dit stelt zorgprofessionals in staat om domeinspecifieke kennis vast te leggen zonder 
afhankelijk te zijn van specifieke software. Dankzij deze aanpak wordt het eenvoudiger om gegevens uit verschillende 
systemen te integreren, uit te wisselen, en langdurig bruikbare, patiëntgerichte informatie te waarborgen.

```{figure} ./figures/about-openehr-diagram.svg
---
name: about-openehr-diagram
---
Bron: https://openehr.org/about_us
```

## Hoe werkt openEHR?

In de rest van de workshop zullen we uitgebreid ingaan op hoe openEHR precies werkt en hoe we aan de slag kunnen met 
openEHR. Het is echter ook goed om eerst een globaal overzicht te hebben. Hiervoor zijn een aantal concepten belangrijk.
Allereerst de archetypes en templates die nodig zijn om klinische modellen mee te maken. Vervolgens is het interessant
om te kijken hoe openEHR daadwerkelijk werkt als CDR.

## Wat zijn archetypes?

Archetypes zijn de **bouwstenen** waarmee openEHR werkt. Deze worden vastgelegd door mensen met domein
kennis. Het proces waarin deze archetypes worden gedefinieerd kan worden gevolgd op de website
van de Clinical Knowledge Manager (CKM) van openEHR. Sommige landen hebben hun eigen CKM. 
Archetypes kunnen referenties bevatten naar klinische terminologieën zoals SNOMED CT.

Het is in principe niet de bedoeling dat iedereen maar archetypes gaat maken. Het doel is namelijk om
een gestandaardiseerde set te hebben die iedereen kan gebruiken - anders verlies je de interoperabiliteit.
We zullen in deze workshop dus geen archetypes maken, maar we gaan er wel een aantal gebruiken uit
de CKM. In Nederland hebben we hiervoor nog geen strikt governance model voor opgericht, maar dit
zal in de toekomst wel moeten.

Een voorbeeld van een tool waarin men archetypes kan maken is de [ADL Designer](https://tools.openehr.org/designer/).
Deze tool wordt beschikbaar gesteld door Better en OpenEHR International. 

## Wat zijn templates?
- Templates
- Templates maken
- Templates posten

## Hoe wordt data opgeslagen?
- API benoemen
- Composities benoemen
