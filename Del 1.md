# Del 1 - Projektopgave HI-FI

### Om opgaven
Denne opgave er første del af HI-FI og omhandler opsætning, navigation og hentning af data.

Opgaven kan løses selvstændigt eller i grupper.

Hvis det er i grupper skal ALLE stadig løse opgaven, men i samarbejdediskutere løsningsforlag og implementering af kode og dokumentation. 

Alle skal lave en arbejdsplan som ajourføres dagligt i en markdown på github 

### Opgavebeskrivelse

Du skal fremstille en webapplikation til en HI-FI webbutik, som præsenter butikkens produkter inddelt efter kagegori. Brugeren af sitet skal nemt og overskueligt finde rundt i de forskellige produkter og kunne fremsøge produkter vha. søgeord.

### Tekniske krav
**Frontend** skal løses vha. html, css og javascript, som gennem en api henter data fra backend.

**Backend** skal via routes tilbyde forskellige udtræk af databasen, hvor alt dynamisk data er lagret.

### Design og layout
Du skal udarbejde et design og layout, dokumenteret via wireframes med beskrivelse i en markdown fil.<br>
Produktet skal designes efter mobile first princippet, men nødvendigvis ikke implementeret til begge medier.

### Forslag til arbejdsprocess
* Planlægning: Afklaring af opgavens indhold defineret i en opgaveoversigt
* Layout: Udarbejdelse af designskitser og wireframes
* Opsæt html sider med navigation og dummy-data (statisk site)
* Design databasen i et E/R diagram
* Opret databasen og indsæt dummy-data
* Programmér modules til dataudtræk
* Opsæt server og routes
* Dokumenter kode og funktionalitet i markdown-filer 


### Sider og indhold
* Forside 
* Produktside
* Kontaktside 
 
### Forsiden 
* Forsidetekst og billeder af produkter

* Visning af udvalgte et eller flere udvalgte produkter (kan være seneste oprettede, et random produkt, eller andet du finder relevant)
 
### Produktsiden
* Viser alle produkter inden for en bestemt kategori
* Visning af ét produkt ved klik på et produkt fra listen
* Visning af produkter efter søgning

Alle produkter hentes via et Api og udskrives med fetch. Over listen af produkter vises kategoriens titel.
 
### Kontaktsiden 
* Kontaktsiden indeholder informatiner om HI-FI butikken samt en kontaktformular.
* Formulardata indsættes i databasen via et api

* Formularfelter validers som minimum vha. html5 validering
* Besked til brugeren om at formularen er sendt og modtaget (i databasen)
 
### Alle sider 
* Menu 
* Fritekst-søgefunktion til produkter og producenter (visning på produktsiden) 
* Footer med kontaktinfo 
 
### Forslag til routes 
/forside

/produkt/:id 


/produkt/kategori/:id 


/produkt/producent/:id 


/produkt/soeg/:tekst 


/kontakt 
 
### Database 
ER diagram 

Rigtige datatyper 

Relationer i databasen

Dokumentation af kode og funktionalitet i markdown. 

### Github
* Projektet skal med sin dokumentation lægges på github.
* Der skal commites ved væsentlige ændringer eller færdiggørelse af en funktionalitet - og altid inden fyraften.
* Alle commit tekster på Github skal give mening. 

### Billedfiler
Alle billeder ligger i en zippet fil fordelt i mapper.

Du vælger om alle billeder skal ligge i én mappe eller om du vil bevare mappestrukturen. I næste del af opgaven skal du uploade til serveren og der har vi erfaring med at det kan være lidt mere indviklet, hvis filerne er fordelt i mapper - du bestemmer! (spørg evt. din vejleder)

 
Brug følgende liste, hvis I er i tvivl om hvilke kategorier de forskellige billeder tilhører:

  
**(CD Afspillere)**

    * creek_classic_cd.jpg
    * creek_Destiny_CD.jpg
    * creek_evo_cd.jpg
    * Exp_2010S_CD.gif


**(DVD Afspillere)**

    * creek_classic.jpg
    * exposure_2010S.jpg
    * parasound_d200.jpg
    * parasound_halod3.jpg

**(Effektforstærkere)**

    * manley_mahi.jpg
    * manley_neoclassic300b.jpg
    * manley_snapper.jpg
    * parasound_haloa23.jpg


**(Forforstærkere)**

    * Creek_OBH_22_Passive_Preamp.jpg
    * parasound_classic7100.jpg
    * parasound_halop3.jpg
    * Project_prebox.jpg


**(Højtalere)**

    * boesendorfer_vcs_wall.gif
    * epos_m5.gif
    * harbeth_hl7es2.jpg
    * harbeth_monitor30.jpg
    * harbeth_p3es2.jpg


**(Int. Forstærkere)**

    * creek_a50I.jpg
    * creek_classic5350SE.jpg
    * creek_destinyamp.jpg
    * manley_snapper.jpg
    * Manley_Stingray.jpg


**(Pladespillere)**

    * Pro_ject_Debut_3_bl.jpg
    * Pro_ject_Debut_III_red_1.jpg
    * Pro_ject_Debut_III_yellow_1.jpg
    * Pro_ject_rpm_5.jpg
    * Pro_ject_rpm10.jpg


**(Rørforstærkere)**

    * jolida_JD102b.jpg
    * jolida_JD202a.jpg
    * jolida_JD300b.jpg
    * jolida_JD302b.jpg
    * jolida_JD502b.jpg 
 
Redigeret af FRG og  AMO September 2017
