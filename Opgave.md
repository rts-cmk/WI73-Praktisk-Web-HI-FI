# Projektopgave HI-FI

Redigeret af FRG og  AMO September 2017

### Om opgaven
Denne opgave er første del af HI-FI og omhandler opsætning, navigation og hentning af data.

Opgaven kan/bør løses i samarbejde, men alle skal lave sin egen løsning. Gruppearbejdet består i at diskutere løsningsforslag og implementering af kode og dokunemtation.

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
Forsidetekst og billeder af produkter

Visning af udvalgte et eller flere udvalgte produkter (kan være seneste oprettede, et random produkt, eller andet du finder relevant)
 
### Produktsiden 
Kan vise ét specifikt produkt 
Alle produkter hentes via et Api og udskrives med fetch, samt kategoriens titel 
 
### Kontaktsiden 
Formulardata indsættes i databasen via et api-kald 
Minimum html5 validering 
Meddelelse om at kontaktformularen er sendt 
 
### Alle sider 
Menu 
Søgefunktion til produkter til visning på produktsiden 
Footer med kontaktinfo 
 
### Routes 
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
### API 
Funktioner 
 
 
### Gruppearbejde 
Opgaven kan løses selvstændigt eller i grupper 
Hvis det er i grupper skal ALLE stadig løse opgaven, men i samarbejde med gruppen 
Alle skal lave en arbejdsplan som ajourføres dagligt i en markdown på github 
 
### Github 
Der skal commites flere gange om dagen. 
Alle commit tekster på Github skal give mening. 
 
### Udleverede filer 
Billeder 
 
 
### Assorteret 
 
Ingen dynamisk menu i første omgang. 
Produktsiden kan sagtens vise kategorinavne ved hvert produkt. 

Sideskift
 
### Filnavne 
Det er anbefalet at flytte billederne, så alle filerne ligger i samme mappe. I næste del skal I nemlig i gang med backend (admin-delen), hvor I bl.a. skal lave en side til billedupload. Det kan måske give jer problemer i databasen, pga. stierne.
 
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
 
