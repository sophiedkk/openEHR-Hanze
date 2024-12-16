# Templates

Vervolgens moeten we een template maken met de gekozen archetypes. Er zijn op dit moment twee programma's beschikbaar
waarmee men makkelijk templates kan maken, dat zijn: 
- [Template Designer](https://downloads.oceaninformatics.com//downloads/TemplateDesigner/) (Windows)
- [Archetype Designer](https://tools.openehr.org/) (Web)

In deze workshop kiezen we voor Archetype Designer die door Better en openEHR International beschikbaar wordt gesteld. 
Hiervoor is helaas wel een account nodig, of men kan inloggen met een van de providers. Ik heb voor de workshop mijn
GitHub gelinked aan Archetype Designer.

```{figure} ./figures/archetype_designer.png
---
name: archetype_designer
---
Archetype Designer website.
```

---

```{admonition} Opdracht
Maak een account op Archetype Designer en log in.
```

## Repository maken
````{margin}
```{tip}
Het is ook mogelijk om een Git of andere remote repository te gebruiken. Dit biedt veel extra mogelijkheden voor samenwerken
en versiebeheer!
```
````
Nadat we zijn ingelogd moeten we een nieuwe repository maken. Klik hiervoor op `New repository` en kies een naam voor
de repository. Ik zal de naam `workshop` gebruiken. 

```{figure} ./figures/template-create-repo.png
---
name: template-create-repo
---
De nieuwe repository voor de workshop.
```

---

```{admonition} Opdracht
Maak een eigen repository in Archetype Designer.
```

## Repository vullen

Onze repository is op dit moment nog leeg. Om Archetypes toe te voegen kan men in de bovenste balk op `Import` drukken
vervolgens kan men via je file browser de `ADL` bestanden die je in de vorige stap hebt uitgezocht toevoegen. Klik
op `Upload all` om ze toe te voegen in de repository. Voor een bulk export kost dit een paar minuten. Als de import 
klaar is kan je op `Close` drukken.

```{figure} ./figures/template-import-adl.png
---
name: template-import-adl
---
Het import scherm om archetypes toe te voegen aan de repository in Archetype Designer.
```

---

```{admonition} Opdracht
Importeer alle archetypes die je wil gebruiken tijdens de workshop of alle archetypes uit de bulk export.
```

## Template

### Stap 1: Root archetype

Nu kunnen we een template maken. Klik op de grote groene `New` knop en selecteer de optie om een template te maken. We
kiezen voor de standaard optie om een Compositie te gebruiken. Hiervoor gebruiken we de `encounter` compositie. 
Selecteer deze compositie als Root Archetype Id. Vervolgens moeten we een naam kiezen, deze moet uniek zijn voor de
openEHR server. Als je de sandbox gebruikt moet je dus zorgen dat je een unieke naam gebruikt door wat extra's toe 
te voegen. Ik zal de naam `workshop-example` gebruiken voor het template.

---

```{admonition} Opdracht
Maak een nieuwe template en geef deze een unieke naam (bijv. workshop-example-sdk).
```

### Stap 2: Toevoegen archetypes

````{margin}
```{tip}
Kijk tussendoor in de `Form` view om te zien hoe het formulier eruit komt te zien!
```
````

Om archetypes toe te kunnen voegen moet men de `Content` slot selecteren in de encounter. Daarna verschijnt in de 
rechter kolom een menu om archetypes te filteren en toe te voegen. Selecteer de archetypes die je denkt nodig te hebben
en voeg deze een voor een toe aan de template. 

```{figure} ./figures/template-add-content.png
---
name: template-add-content
---
De template en het toevoegen van archetypes. Rechts is de zoekbalk om archetypes te filteren.
```

Op basis van de casus hebben we een archetype nodig voor:
- Lichaamstemperatuur
- Lichaamsgewicht
- Lichaamslengte
- Bloeddruk (boven- en onderdruk)
- Hartslagfrequentie
- Bloedsaturatie (SpO₂)
- Ademhaling (regelmatigheid, diepte, en frequentie)

---

```{admonition} Opdracht
Voeg alle archetypes toe die nodig zijn voor de casus.
```

### Stap 3: Selecteren velden

Zoals eerder gezegd gaat openEHR uit van een maximale dataset. Het is nu aan ons om deze te reduceren naar de klinisch
relevante set data die nodig is. De eerste stap is meestal om alle velden uit te schakelen. Hiervoor kan men de 
`Prohibit optional elements` knop gebruiken (sneeuwvlok symbool). Voor sommige velden moet de frequentie ook worden 
aangepast. Door te klikken op het gele knopje in dat veld kunnen de occurences naar nul worden gezet en door nog een 
keer te drukken wordt de waarde weer teruggezet. 

```{figure} ./figures/template-select-fields.png
---
name: template-select-fields
---
Het selecteren van de velden die wel en niet nodig zijn.
```

---

```{admonition} Opdracht
Zet alle velden die niet nodig zijn uit. Zet vervolgens de velden die wel nodig zijn aan. Pas de frequentie van velden
aan waar nodig.
```

### Stap 4: Aanpassen velden

Het is ook mogelijk om individuele velden aan te passen zolang het binnen de definitie van het archetype past. Zo 
kan men eenheden aanpassen of vastzetten, minimum en maximum waarden aanpassen, opties in categorische lijsten 
verwijderen, etc. Het is ook mogelijk om waarden te koppelen aan externe codes, bijv. SNOMED CT of de ICD-10. 

```{figure} ./figures/template-adjust-constraints.png
---
name: template-adjust-constraints
width: 30%
---
Het selecteren van de velden die wel en niet nodig zijn.
```

---

```{admonition} Opdracht
Pas de velden aan waar nodig. Stel de eenheden zo in dat deze alleen met gangbare eenheden werken. Stel eventueel 
minima en maxima in.
```

### Stap 5: Exporteren

Wanneer we tevreden zijn kunnen we helemaal bovenin op `Save` drukken en daarna op `Export`. Het is mogelijk om in 
verschillende formats te exporteren. Voor nu is het `OPT` format het belangrijkste, want deze wordt ondersteund door
EHRBase om templates mee te registreren.

---

```{admonition} Opdracht
Exporteer de template in het OPT format en plaats deze op een plek waar je het later makkelijk kan terugvinden.
```

### Metadata

Het is ook mogelijk om metadata toe te voegen en aan te passen via Archetype Designer. In het `Description` tabblad 
kan de Template Id worden aangepast, keywords, purpose, etc. Onder het sub-tabblad Attribution kunnen gegevens 
worden toegevoegd over de build en de auteurs. Zeer belangrijke info in een productieomgeving, maar voor nu zullen we
het laten voor wat het is.
