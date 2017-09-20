# API service

app.js

npm install restify, restify-cors-middleware, mysql2
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
```javascript
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
