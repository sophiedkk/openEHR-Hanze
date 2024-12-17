# Intermezzo: Bruno

````{margin}
```{note}
Het is ook helemaal prima om Postman of Insomnia te gebruiken tijdens de workshop als je daar meer mee bekend bent. 
```
````

Als API client zullen we in deze workshop Bruno gebruiken: https://www.usebruno.com/

Bruno is een relatief simpele API client die alle data opslaat in tekstbestanden en een simpele mapstructuur op je 
computer. De bestanden zijn dus goed te combineren met Git. Een ander groot voordeel van Bruno is dat het volledig 
te gebruiken is zonder accounts en cloud functionaliteiten.

Als je Bruno net opstart ziet het er als volgt uit:

```{figure} ./figures/bruno.png
---
name: bruno
---
De interface van Bruno.
```

De eerste stap is om een nieuwe collection aan te maken en te kiezen waar men deze wil opslaan.

Vervolgens moeten we een nieuwe request maken. Klik op de drie puntjes naast je collection in het linkerpaneel en 
klik daarna op `New Request`.

```{figure} ./figures/bruno-new-request.png
---
name: bruno-new-request
---
Een nieuwe request maken in Bruno.
```

Tot slot is het handig om alvast een environment aan te maken. Hierin zullen we in ieder geval de URL van de EHRBase 
server in opslaan. Dit kan door op de knop rechts bovenin te klikken:

```{figure} ./figures/bruno-environments.png
---
name: bruno-new-environments
---
Een nieuwe environment maken in Bruno. Handig om bijv. de server URL in op te slaan!
```