# Casus

In deze workshop gaan we alle delen van het gebruik van openEHR langs. 1) We beginnen bij het definiëren van het
klinische scenario wat we willen vastleggen en bepalen welke klinische informatie hiervoor relevant is. 2) Daarna 
zoeken we de juiste archetypes om de klinische informatie mee vast te leggen. 3) Deze archetypes combineren
we in een template. 4) Het template zullen we registreren in een op openEHR gebaseerde Clinical Data 
Repository. 5) Vervolgens zullen we data opslaan door een compositie te POSTen die gebaseerd is op dit 
template. 6) We zullen de compositie ook weer ophalen om aan te tonen dat deze in de database is opgeslagen.

```{figure} ./figures/workflow.svg
---
name: workflow
---
Stappen die we gaan nemen in de workshop.
```

## De casus

Een arts in een huisartsenpraktijk wil voor routinecontroles een aantal vitale parameters meten. Hiervoor
wordt u gevraagd een formulier te maken en de data opslag te verzorgen:

Tijdens de controle meet de arts de **lichaamstemperatuur**, bepaalt het **lichaamsgewicht** en de 
**lichaamslengte** om de **BMI** te berekenen, en meet de **bloeddruk** (systolisch en diastolisch) 
met een bloeddrukmeter. Vervolgens controleert men de **hartslagfrequentie** en wordt de **bloedsaturatie** 
(SpO₂) bepaalt d.m.v. een pulse oximeter. De **ademhaling** wordt geëvalueerd door frequentie, diepte en 
regelmatigheid vast te stellen.