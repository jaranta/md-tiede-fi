---
title: Automaattinen lähdeluettelo Markdownilla ja Pandocilla
author: Jonne Arjoranta
contributor:
copyright:
date: 2015-08-11
modified:
tags: .bib, bibtex, pandoc, zotero, mendeley
---

Markdown-muotoiseen artikkeliin on helppo lisätä lähdeluettelo, jos viitteet ovat `.bib` tai sen kanssa yhteensopivassa muodossa. Tällaiseen muotoon ne saa automaattisella lähteidenhallinnalla, esimerkiksi [BibTeXin](http://www.bibtex.org/), [Zoteron](https://www.zotero.org/) tai [Mendeleyn](https://www.mendeley.com/) avulla. Kaikki kolme työkalua auttavat lähteiden hallinnassa ja kaikki kolme saa toimimaan yhteen [Pandocin](http://pandoc.org/) kanssa niin , että lähteet käännetään valmiiksi oikeassa muodossa olevaksi lähdeluetteloksi.

Ohjeet on jaettu neljään vaiheeseen:

1. Lähteet tietokantaan
2. Valmis `.bib`-tiedosto
3. Viitteet asiakirjaan
4. Pandocilla valmis lähdeluettelo

## Lähteet tietokantaan

Periaatteessa on mahdollista kasata `.bib`-tiedosto käsin, mutta järkevämpää on käyttää jotain ohjelmaa. Ohjeen kannalta on yhdentekevää, mitä viitetietokantaa käytät. Oleellista on ottaa käyttöön jokin työkalu, johon voi listata haluamasi viitteet oikeine metatietoineen. Käytän itse Mendeleytä, mutta mikä tahansa tässä ohjeessa mainittu työkalu (ja varmasti moni muukin) käy tehtävään.

## Valmis `.bib`-tiedosto

Kun olet saanut lähteitä kasaan, pitää ne saada viitattavaan muotoon. On monenlaisia lähtestymistapoja tähän, mutta tässä ohjeessa oletetaan, että käytät Pandocia. Sekä Zotero että Mendeley käyttävät itse toisenlaista tietokantaa viitteille, joten niistä täytyy saada ulos oikeanmuotoinen tiedosto. Se onnistuu Zoteron tapauksessa esimerkiksi [AutoZotBib-lisäosalla](http://www.rtwilson.com/academic/autozotbib). Mendeley osaa itse tuottaa `.bib`-tiedoston.[^mendeleybib]

[^mendeleybib]: Katso Tools -> Options -> BibTeX -> [x] Enable BibTeX syncing

## Viitteet asiakirjaan

Kun olet saanut valmiin `.bib`-tiedoston, lisää sen sijainti asikirjasi YAML-osioon nimellä `bibliography`. Esimerkiksi:

~~~~~~~~
---
bibliography: /home/jonne/Bibtex/library.bib
---
~~~~~~~~

Nyt voit viitata tekstisi seassa `.bib`-tiedostossa oleviin lähteisiin niiden viittausavaimilla. Esimerkiksi:

~~~~~~~~
Tämä on esimerkkilause, joka päättyy viitteeseen [@Tutkija2012].
~~~~~~~~

Lähteisiin [voi viitata kolmella eri tavalla](http://pandoc.org/README.html#citations):

1. `@Tutkija2012` tuottaa `Tutkija (2012)`-muotoisen viitteen.
2. `[@Tutkija2012]` tuottaa `(Tutkija, 2012)`-muotoisen (tai vastaavan -- riippuu viittaustyylistä) muotoisen viitteen.
3. `[-@Tutkija2012]` jättää nimen pois viitteestä. Se sopii esimerkiksi silloin, kun tekstissä jo viitataan tutkijaan tämän nimellä: `Kuten Tiina Tutkija (2012) jo osoitti...`.

Lopeta asiakirja lähdeluettelon otsikolla, esimerkiksi:

~~~~~~~~
---
title: Artikkeli
bibliography: /home/jonne/Bibtex/library.bib
---

# Otsikko

Viitteen sisältävä lause [@Tutkija2012].

# Lähdeluettelo
~~~~~~~~

## Pandocilla valmis lähdeluettelo

Nyt käännämme artikkelin valmiiseen muotoon ja viitteet ovat automaattisesti lähdeluettelossa:

`pandoc --filter pandoc-citeproc artikkeli.md -o artikkeli.pdf`

Käytämme komennossa filtterinä `pandoc-citeproc` käskyä, joka hoitaa viitteiden asettelun. Valmiiseen asiakirjaan ilmestyy nyt sekä viite että lähdeluettelo:

> **Artikkeli**
>
> Viitteen sisältävä lause (Tutkija, 2012).
>
> **Lähdeluettelo**
>
> Tutkija, Tiina. 2012. *Tutkimus, joka osoittaa tärkeitä asioita*. Kotipaikka: Tärkeä julkaisija.

Katso lisätietoja [Pandocin dokumentaatiosta](http://pandoc.org/README.html#citations).
