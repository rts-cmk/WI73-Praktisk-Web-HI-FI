# API service

app.js

npm install restify, restify-cors-middleware, mysql2 --save
```javascript
const restify = require('restify');
const corsmiddleware = require('restify-cors-middleware');
const server = restify.createServer({
    'name': 'fruit',
    'version': '1.0.0'
});

server.use(restify.plugins.bodyParser());
const cors = corsmiddleware({ origins: ['*'] });
server.pre(cors.preflight);
server.use(cors.actual);

require('./routes/index')(server);

server.listen(1337);
```
config/sql.js
```javascript
const mysql = require('mysql2');

module.exports = {
    'connect': () => {
        return mysql.createConnection({
            'host': 'localhost',
            'user': 'root',
            'password': '',
            'database': 'fruit'
        });
    }
};
```

routes/produkt.js
```javascript
const db = require('../config/sql').connect();

module.exports = function (app) {
    app.get('/produkt', function (req, res) {
        db.query('select * from fruit', function (err, data) {
            res.send(data);
        })
    })
}

```
routes/index.js
```javascript
module.exports = (app) => {
    require('./produkt')(app);
    //require('./kontakt')(app);
};
```
Opret produkt

Endnu et route i routes/produkt.js
```javascript
    app.post('/create', (req, res) => {

        let values = [];
        values.push(req.body.navn);
        values.push(req.body.type);
        values.push(req.body.pris);
        values.push(req.body.billede);

        db.execute('insert into fruit set navn = ?, fk_type = ?, pris = ?, image = ?', values, (err, rows) => {
            if (err) {
                console.log(err);
                res.json(500, {
                    "message": "Internal Server Error",
                    "error": err
                })
            }
            else {
                res.json(200, {
                    "message": "Data indsat"
                })
            }
        })
    });
```

sql dump til databasen fruit
```javascript
REATE TABLE `fruit` (
  `id` int(11) NOT NULL,
  `navn` varchar(30) NOT NULL,
  `fk_type` int(11) NOT NULL,
  `pris` float NOT NULL,
  `image` varchar(60) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

--
-- Data dump for tabellen `fruit`
--

INSERT INTO `fruit` (`id`, `navn`, `fk_type`, `pris`, `image`) VALUES
(1, 'Cox Orange', 1, 2, 'coxorange.jpg'),
(2, 'Filippa', 1, 2, 'filippa.jpg');

-- --------------------------------------------------------

--
-- Struktur-dump for tabellen `type`
--

CREATE TABLE `type` (
  `id` int(11) NOT NULL,
  `navn` varchar(20) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

--
-- Data dump for tabellen `type`
--

INSERT INTO `type` (`id`, `navn`) VALUES
(2, 'pære'),
(1, 'æble');

--
-- Begrænsninger for dumpede tabeller
--

--
-- Indeks for tabel `fruit`
--
ALTER TABLE `fruit`
  ADD PRIMARY KEY (`id`),
  ADD UNIQUE KEY `navn` (`navn`),
  ADD KEY `fk_type` (`fk_type`);

--
-- Indeks for tabel `type`
--
ALTER TABLE `type`
  ADD PRIMARY KEY (`id`),
  ADD UNIQUE KEY `navn` (`navn`);

--
-- Brug ikke AUTO_INCREMENT for slettede tabeller
--

--
-- Tilføj AUTO_INCREMENT i tabel `fruit`
--
ALTER TABLE `fruit`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=3;
--
-- Tilføj AUTO_INCREMENT i tabel `type`
--
ALTER TABLE `type`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=3;
/
```

# Frontend (website)
app.js

(npm install browser-sync --save)
```javascript
const browserSync = require('browser-sync').create();
browserSync.watch('./public/**/*').on('change', browserSync.reload);
browserSync.init({
    'server': './public'
});
```
public/produkt.html
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Produkt</title>
</head>

<body>
    <nav>
        <ul>
            <li><a href="/">Forside</a></li>
            <li><a href="/produkt.html">Produkt</a></li>
            <li><a href="/kontakt.html">Kontakt</a></li>
        </ul>
    </nav>
    <h1>Produkt</h1>
    <div id="content"></div>
    <script>
        fetch('http://localhost:1337/produkt')
            .then((response) => {
                // grib svarets indhold (body) og send det som et json objekt til næste .then()
                return response.json();
            })
            .then((data) => {
                // nu er json objektet lagt ind i data variablen, udskriv data
                console.log(data);
                document.getElementById('content').innerHTML = data[0].navn + " " + data[0].pris;
            })
    </script>
</body>

</html>
```
Opret produkt via produkt.html
* I eksemplet er anvendt fire input type text og en button (**uden form-tag**)
```html
    Navn:<input type="text" id="navn"><br>
    Type: <input type="text" id="type"><br>
    Pris: <input type="text" id="pris"><br>
    Billede: <input type="text" id="billede"><br>
    <button id="gem">Gem</button>
```
Herefter et javascript i produkt.html eller i en ekstern js-fil kaldet produkt.js
* Lyt først på button-click.
* Hent de fire værdier over i fire variable
* Opret et header-objekt og sæt Content-Type til application/json
* Opret en variabel kaldet init og tildel den et json-objekt bestående af `method`, `headers`, `body`, `cashe` og `mode`
* Opret et Request-objekt med værdierne url og init
* fetch Request-objektet og brug evt. resultatet til noget (her response eller err)

```javascript
// Lytter på om der er klikket på knappen gem - herefter postes data som indsættes i databasen
document.querySelector('#gem').addEventListener('click', (event) => {
    console.log('event ok');
    event.preventDefault();
    let navn = document.querySelector('#navn').value;
    let type = document.querySelector('#type').value;
    let pris = document.querySelector('#pris').value;
    let billede = document.querySelector('#billede').value;

    let headers = new Headers();
    headers.append('Content-Type', 'application/json');

    let init = {
        method: 'POST',
        headers: headers,
        body: `{"navn":"${navn}","type":"${type}","pris":"${pris}","billede":"${billede}" }`,
        cache: 'no-cache',
        mode: 'cors'
    };

    let request = new Request('http://localhost:1337/create', init);

    fetch(request)
        .then(response => { console.log(response) }).catch(err => { console.log(err) });

});
```



### Eksemplet fra undervisningen (scripts/produkt.js)
(efter koden vises produkt.html)
```javascript
// Når sidens elementer (alt indhold) er loadet på siden
(() => {
    document.addEventListener('DOMContentLoaded', () => {
        hentData(0);
    });

})();

// Funktion som henter data til visning i content
// Funktionen har en parameter - hvis tallet nul hentes alt indhold, og hvis større end nul hentes kun denne ene kategori
function hentData(type = 0) {
    let url = 'http://localhost:1337/produkt';
    if (type > 0) url += '/' + type;
    fetch(url)
        .then((response) => {
            // grib svarets indhold (body) og send det som et json objekt til næste .then()
            return response.json();
        })
        .then((data) => {
            // nu er json objektet lagt ind i data variablen, udskriv data
            console.log(data);
            var type = '';
            document.getElementById('content').innerHTML = "";
            data.forEach(function (item) {
                if (type != item.type) {
                    document.getElementById('content').innerHTML += `<h2>${item.type}</h2>`;
                    type = item.type;
                }
                document.getElementById('content').innerHTML += `
                        <div>
                            <b>${item.navn}</b><br>
                            pris: kr. ${item.pris}<br>
                            <img src="images/${item.image}" width="60px" />
                        </div>  
                        `;

            })
        })
}
document.querySelector('#selecttype').addEventListener('change', (event) => {
    let obj = document.querySelector('#selecttype');
    hentData(obj.value);
})

// Lytter på om der er klikket på knappen gem - herefter postes data som indsættes i databasen
document.querySelector('#gem').addEventListener('click', (event) => {
    console.log('event ok');
    event.preventDefault();
    let navn = document.querySelector('#navn').value;
    let type = document.querySelector('#type').value;
    let pris = document.querySelector('#pris').value;
    let billede = document.querySelector('#billede').value;

    let headers = new Headers();
    headers.append('Content-Type', 'application/json');

    let init = {
        method: 'POST',
        headers: headers,
        body: `{"navn":"${navn}","type":"${type}","pris":"${pris}","billede":"${billede}" }`,
        cache: 'no-cache',
        mode: 'cors'
    };

    let request = new Request('http://localhost:1337/create', init);

    fetch(request)
        .then(response => { console.log(response) }).catch(err => { console.log(err) });

});
```
produkt.html
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Produkt</title>
</head>

<body>
    <nav>
        <ul>
            <li><a href="/">Forside</a></li>
            <li><a href="/produkt.html">Produkt</a></li>
            <li><a href="/kontakt.html">Kontakt</a></li>
        </ul>
    </nav>
    <h1>Frugter</h1>

    Navn:<input type="text" id="navn"><br> Type: <input type="text" id="type"><br> Pris: <input type="text" id="pris"><br>    Billede: <input type="text" id="billede"><br>
    <button id="gem">Gem</button>
    <br><br>
    <select id="selecttype">
    <option value="0">Alle...</option>
    <option value="1">Æbler</option>
    <option value="2">Pærer</option>
</select>
    <div id="content"></div>

    <script src='./scripts/produkt.js'></script>
</body>

</html>
```
