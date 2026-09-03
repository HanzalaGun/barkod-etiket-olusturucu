[Türkçe](README.md) · [English](README.en.md) · [Русский](README.ru.md) · **Deutsch** · [العربية](README.ar.md)

# Barcode-Etiketten erstellen

Macht aus einer Produktliste druckfertige Barcode-Etiketten. Eine einzige
`index.html` — keine Installation, kein Build, kein Server. Doppelklick genügt.

**Laufende Fassung:** [hanzala.com.tr/araclar/barkod-etiket-olusturucu](https://hanzala.com.tr/araclar/barkod-etiket-olusturucu)

<br>

## Was es macht

- **EAN-13 und Code 128.** Geben Sie bei EAN-13 zwölf Ziffern ein, wird die
  Prüfziffer selbst berechnet; bei dreizehn mit falscher Prüfziffer gibt es eine
  Warnung statt eines stillschweigend kaputten Barcodes.
- **A4-Etikettenbögen** (70×37, 105×37, 52,5×29,7, 38×21, 105×74 mm) oder ein
  eigenes mm-Maß für einen **Thermo-Etikettendrucker**. Im Rollenmodus bekommt
  jedes Etikett seine eigene Seite.
- **Mengenspalte** — wie viele Etiketten desselben Produkts gedruckt werden.
- **Spalte für den alten Preis** — durchgestrichen, mit Rabatt in Prozent.
- Vier Layouts, Schriftgröße, fett/kursiv, Name oder Preis ausblenden.

Es wird nichts verschickt: Ihre Liste verlässt den Browser nicht, es gibt keinen
Server.

<br>

## Eingabeformat

Ein Produkt je Zeile, Spalten getrennt durch **Tabulator**, **Semikolon** oder
**senkrechten Strich**:

```
Gemahlener Kaffee	8690000000012	45	2
Tee	869000000002	20
Tee im Angebot	8690000000012	20	1	35
```

`Name · Barcode · Preis · Menge · alter Preis` — eine leere Menge zählt als 1.

Fehlt in einer Zeile jedes dieser drei Trennzeichen, wird auf das Komma
zurückgegriffen. Das Komma ist bewusst die letzte Wahl: türkische Preise werden
`145,90` geschrieben, und als Trennzeichen gelesen wurde daraus Preis 145 und
Menge 90 — jemand wollte ein Etikett und bekam neunzig.

<br>

## Sprachen

Türkisch, Englisch, Russisch, Deutsch und Arabisch — derselbe Satz wie auf der
Website. Auch Maße, Beispielliste, Bogennamen und Warnungen werden übersetzt:
`52,5×29,7 mm` wird auf Russisch `52,5×29,7 мм` und auf Englisch
`52.5×29.7 mm`.

Arabisch läuft von rechts nach links, mit zwei Ausnahmen: das Feld mit der
Produktliste bleibt von links nach rechts und linksbündig (diese Liste wird aus
einer Tabelle eingefügt, die Spalten müssen in der eingefügten Reihenfolge
bleiben), und die Etikettenvorschau ebenso — dieser Kasten ist Druckausgabe und
darf der Seitenrichtung nicht folgen.

Jede Sprache hat ihre eigene Adresse: `index.html?dil=de`. Der geteilte Link
öffnet dieselbe Sprache, die `hreflang`-Angaben zeigen auf diese Adressen. Ohne
Auswahl gilt die Browsersprache, und Türkisch, falls sie nicht dabei ist.

Die Beispielliste wechselt nur mit der Sprache, solange Sie selbst nichts
getippt haben — ein Sprachwechsel löscht nie eine Liste, die Sie geschrieben
haben.

<br>

## Benutzung

`index.html` herunterladen und doppelklicken. Die Barcodes zeichnet
[JsBarcode](https://github.com/lindell/JsBarcode) über ein CDN, der erste Aufruf
braucht daher Internet.

Für die eigene Website die Datei unverändert kopieren; eine weitere Abhängigkeit
gibt es nicht.

<br>

## Selbstprüfung

`index.html?test=1` öffnen. Geprüft werden die Prüfziffernrechnung, die Wahl des
Trennzeichens und die Barcode-Validierung; danach wird für alle fünf Sprachen
die Vollständigkeit von Übersetzungstabelle und Layoutnamen geprüft. Fällt eine
Prüfung durch, wird der Tab-Titel zu `HATA:`.

<br>

## Lizenz

MIT — [LICENSE](LICENSE). Nutzen, ändern, verkaufen.

Dieses Werkzeug entstand für [hanzala.com.tr](https://hanzala.com.tr); dort gibt
es auch [weitere kostenlose Werkzeuge](https://hanzala.com.tr/araclar).
