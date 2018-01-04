# Blandede opgaver, 2018 uge 1



## Formål

Som webudvikler/programmør er det vigtigt at vide, hvad der gør hvad, specielt når man får brug for at genbruge kode. Det nytter ikke noget, at man genbruger en hel fil, når man egentligt kun har brug for en lille del af den.

Mens du løser disse opgaver, skal du reflektere over det du gør. Skriv en masse kommentarer, så det senere bliver lettere at genbruge kode.

Læg mærke til den måde opgaverne er formulerede. Vi bruger fagudtryk, som "at definere funktioner", "at kalde funktioner", "events", "parametre", osv. På en arbejdsplads er det utroligt vigtigt, at man kan kommunikere uden hele tiden at skulle forklare, hvad man mener. Derfor skal du sørge for, at bruge mange af disse udtryk, så ofte som overhovedet muligt.


## Struktur

Vi vil råde dig til at lave en **separat mappe til hver opgave**. Dette gør det nemmere for lærere, at finde rundt i dine filer, og det gør det nemmere for dig at se, hvilke filer der egentligt er nødvendige for, at løsningen kan fungere.

Navnet på mapperne kunne bare være "opgave_01", "opgave_05_1", "opgave_05_2", osv.

## Regler

Følgende regler gælder med mindre du får andet at vide i opgaven:
* Brug en fornuftig filstruktur til at løse hver opgave (se opgave 1).

* Alt Javascript skal ligge i JS filen. Ingen Javascript i HTML'en.

* I Javascript er der flere måder hvorpå man kan definére en funktion. Du bestemmer selv hvilken metode du vil bruge.



---

## Opgaver

### Opgave 1: Event - Når siden er indlæst

*(Husk reglerne)*

* Opret `index.html`

* Opret `myscript.js`

* Få index.html til at indlæse `myscript.js`

* I `myscript.js`, lav en event der lytter på om siden er færdig med at blive indlæst.
	* Få den til at logge teksten *"Side indlæst"*.



---

### Opgave 2: Event - Når der trykkes på et element

*(Husk reglerne)*

* Tag en kopi af `Opgave 1`.

* Indsæt en knap på siden.

* Når siden er indlæst skal den gøre følgende:
	* Giv knappen en click-event.
	* Eventen skal bare logge beskeden *"Knap trykket"*.



---

### Opgave 3: Funktion uden parametre

*(Husk reglerne)*

* Definér funktionen `test`.

* Funktionen skal ikke tage imod nogen parametre.

* Funktionen skal logge beskeden *"Funktion kørt"*.

* Kald funktionen, når siden er indlæst.



---

### Opgave 4: Funktion med parametre

*(Husk reglerne)*

* Definér funktionen `udskriv`.

	* Funktionen skal tage imod 2 parametre: `navn` og `alder`

	* Funktionen skal logge beskeden *"Jeg hedder ??? og jeg er ??? år gammel"*. Du skal selvfølgelig indsætte de modtagede oplysninger på spørgsmålenes plads. 

* Kald funktionen, når siden er indlæst, og giv den de to påkrævede oplysninger.



---

### Opgave 5.1: Knapper og funktioner

*(Husk reglerne)*

* Lav 2 knapper. De synlige tekster på knapperne er "Oluf" og "Gertrud".

* Hent definitionen af funktionen `udskriv` fra tidligere opgave eller skriv den igen fra bunden, for at træne det.

* Når der trykkes på "Oluf" knappen skal den vha. `udskriv` funktionen logge beskeden *"Jeg hedder Oluf og jeg er 70 år gammel"*.

* Når der trykkes på "Gertrud" knappen skal den vha. `udskriv` funktionen logge beskeden *"Jeg hedder Gertrud og jeg er 65 år gammel"*.

* Du må <b>ikke</b> definére 2 udskriv funktioner i samme opgave.



---

### Opgave 5.2: Hovsa... Man spørger ikke om en dames alder

*(Husk reglerne)*

* Kopiér forrige opgave.

* Ret "Oluf" knappens event, så den sender "m" med som tredje argument.

* Ret "Gertrud" knappens event, så den sender "k" med som tredje argument.

* Ret definitionen af `udskriv` funktionen, så følgende er opfyldt:

	* Den tager imod et trejde parameter: `kon`.

	* Den tjekker om `kon` er "m" eller "k":
		* Hvis `kon` er "m" logges beskeden: *"Jeg hedder ??? og jeg er ??? år gammel"*.
		* Hvis `kon` er "k" logges beskeden: *"Jeg hedder ???"*.



---

### Opgave 6: Manipulering af HTML elementer

*(Husk reglerne)*

* Lav en knap. Du vælger selv hvad der skal stå på knappen.

* Lav et element under knappen, som indeholder teksten *"(Tryk på knappen)"*.

* Når der trykkes på knappen, skal teksten under knappen udskiftes med *"Du har trykket på knappen"*.

Ekstraopgave:

* Få den til at vise hvor mange gange knappen er blevet trykket, *"Du har trykket # gange på knappen"*.

* Vis forskellige beskeder afhængig af antallet af tryk:
	* 1 tryk: *"Dette er første gang du trykker på knappen"*
	* 2 tryk: *"Du har trykket på knappen igen"*
	* 3 og over: *"Du har trykket # gange på knappen"*



---

### Opgave 7: Erstat console.log

*(Husk reglerne)*

* Ret opgave 5.2, så den udskriver beskederne "Jeg hedder (..)" på siden i stedet for i konsollen. Du behøver ikke at oprette en "opgave_7" mappe. Ret du bare i den gamle opgave. Behold dog gerne console.log koden.

Ekstraopgave:

* Hvis du har brug for at træne dette noget mere, så ret gerne alle tidligere opgaver, der bruger console.log



---

### Opgave 8: URL parameter

*(Husk reglerne)*

**Hjælp:**<br>
Definition af funktionen **hentAlleUrlParametre**:<br>
https://github.com/rts-cmk/kode-eksempler/blob/master/eks_url_parameter_og_statisk_menu/js/funktioner.js

Brug af funktionen **hentAlleUrlParametre**:<br>
https://github.com/rts-cmk/kode-eksempler/blob/master/eks_url_parameter_og_statisk_menu/js/produkter.js


* Vælg 3 af dine yndlings <b><a href='https://en.wikipedia.org/wiki/Care_Bears' target='_blank'>Care Bears</a></b><br>
<b>Spørgsmål:</b> *Eeeej, altså. Behøver det virkelig at være Care Bears?*<br>
<b>Svar:</b> *Nej, da!... Det er kun hvis du ønsker at gennemføre uddannelsen.*

* Indsæt et link på siden for hver Care Bear.

* Når der trykkes på et link skal der sendes et parameter via URL'en. <b>Nøglen</b> skal være "`valg`" og <b>værdien</b> skal være navnet på den Care Bear man har klikket på. Browseren skal have lov at genindlæse siden. Lad derfor være at forhindre default handlingen.

* Via Javascript, tjek om URL parametret "`valg`" eksisterer i URL'en.
	* Hvis det gør, så vis teksten (på siden): *"Du har valgt "* og så navnet på den valgte Care Bear.

	* Hvis ikke, så vis teksten: *"Vælg én af mine yndlings Care Bears"*



---

### Opgave 9.1: Skift underside uden at genindlæse siden og uden database

*(Husk reglerne)*

Indsæt følgende kode på din side. Find selv to forskellige billeder.<br>
Du må gerne lave små ændringer i den udleverede HTML, hvis du føler der er brug for det.

```html
<div class='underside'>
	<h2>Side 1</h2>
	<p>Dette er første side.</p>
	<img src='billeder/side1.jpg'>
</div>

<div class='underside'>
	<h2>Side 2</h2>
	<p>Dette er anden side.</p>
	<img src='billeder/side2.jpg'>
</div>
```

* Gør underside 2 usynlig via CSS filen.

* Placér 2 links i toppen af siden med teksterne "Side 1" og "Side 2".

* Når der trykkes på et link, så skal tilhørende underside div vises mens det andet gemmes.

* Siden må ikke genindlæses, når der trykkes på linksne, så husk at forhindre deres default handling.



---

### Opgave 9.2: Skift underside via URL parameter

*(Husk reglerne)*

* Tag en kopi af forrige opgave, der omhandler undersider.

* Lav koden om, så det nu er URL'en der bestemmer, hvilken underside der skal vises.

* Denne gang skal du tillade at browseren genindlæser siden, når der trykkes på et link.

Ekstraopgave

* Highlight det aktuelle link via Javascript <br>(dvs. hvis jeg står på Side 2, så skal link nr. 2 være highlighted)



---

### Opgave 10: Chat for schizofrene

*(Husk reglerne)*

Du skal lave en simpel (og næsten ubrugelig) chat formular med dét formål, at øve dig i at manipulere elementer på siden og i at bruge funktioner.

* Gør et tomt HTML element klar, som senere vil indeholde tekst. I opgaven vil jeg fremover referere til dette element som `output` elementet.

* Definér funktionen `chat`, som tager imod 2 parametre: `navn` og `besked`.

	* Når funktionen kaldes, skal den tage navnet og beskeden som den har modtaget og konstruere en tekststreng i stil med dette: <br>*"<b>Anders And:</b> Hvorfor går jeg egentligt iklædt en jakke, men ingen bukser?"*. <br><br>Denne tekststreng skal så indsættes i toppen af `output` elementet, så de nyeste beskeder står øverst.

* Test din funktion, når siden er blevet indlæst.<br>
Kald funktionen mindst to gange i koden lige efter hinanden med forskellige navne og beskeder, for at teste, at `output` elementet kan vise flere beskeder samtidig. Hvis det virker, så udkommentér eller slet de to kald (altså din test).

* Lav et input felt til `navn` (hele formularen skal placeres OVER output elementet)

* Lav et textarea til `besked`

* Lav en knap til at sende oplysningerne.

* Når der trykkes på knappen, skal du kalde din `chat` funktion og give den de to oplysninger fra formularen. Siden må naturligvis ikke genindlæses.

* Besked-feltet i formularen skal tømmes, hver gang man trykker send, men navnet skal blive stående.

* Sørg for at teste, at du kan sende adskillige beskeder efter hinanden og at ældre beskeder bliver stående.

Ekstraopgave

* Validér formularen.

* Vis tidsstempler i chatten.

* Typisk placerer man formularen UNDER output elementet og de nyeste beskeder vises i bunden. Dette kræver dog, at du giver output elementet en lodret scrollbar og at du via Javascript sørger for at rulle ned i bunden af chatten, hver gang en ny besked tilføjes. Hvis du har mod på det, så prøv og se om du kan gøre dette (behold dog den gamle version).



---

### Opgave 11: Et forholdsvist simpelt galleri vha. Array

*(Husk reglerne)*

* Gør et `<img>` klar på siden.<br>Lad `src` attributten være tom til at starte med.

* Lav array'et `filnavne` (i global scope) som indeholder filnavnene på 3 billeder i dit projekt.

* Lav variablen `index` (i global scope) som indeholder tallet 0. Dette skal bruges til at holde styr på, hvilket billede i array'et vi skal hente.

* Definér funktionen `opdater_billede`, som ikke tager imod nogen parametre.

	* Når funktionen kaldes, så bruger den index variablen til at hente navnet på et specifikt billede i `filnavne` array'et.

	* Hiv fat i `<img>` elementet via Javascript og ændr `src` attributten. Det er her du skal bruge det filnavn, som du lige har fået fra dit array.

* Når siden er blevet indlæst, kald funktionen `opdater_billede`.

* Test din side. Gå ikke videre med opgaven til du har set et billede på siden på trods af, at `src` attributten startede med at være tom - Dette er dit bevis på, at du højst sandsynligt har gjort det korrekt.

* Definér funktionen `naeste_billede`, som ikke tager imod nogen parametre.

	* Når funktionen kaldes, så øger den `index` med 1.

	* Du skal forhindre `index` i at overskride grænsen. Der er jo kun et vist antal billeder i `filnavne` array'et. <br>Hvis tallet overskrider grænsen, så nulstil det.

	* Til sidst i funktionen, skal den kalde `opdater_billede` funktionen.

* Lav en knap på siden med teksten "Næste".

	* Når knappen trykkes, skal den kalde `naeste_billede` funktionen.

* Test knappen. Gå ikke videre med opgaven til du har set billedet skifte og at galleriet endda starter om, når alle billeder er blevet vist.

* Definér funktionen `forrige_billede`, som ikke tager imod nogen parametre.

	* Når funktionen kaldes, så trækkes der 1 fra `index`.

	* Du skal forhindre `index` i at komme under 0. <br>Hvis tallet overskrider grænsen, så sæt det til det højeste, tilladte tal i forhold til dit array.

	* Til sidst i funktionen, skal den kalde `opdater_billede` funktionen.

* Lav en knap på siden med teksten "Forrige".

	* Når knappen trykkes, skal den kalde `forrige_billede` funktionen.

* Test knappen.

Ekstraopgave

* Sørg for, at dit script ikke begynder at crashe, hvis du tilføjer eller fjerner billeder fra dit `filnavne` array (dvs. hvis antallet ændres)
