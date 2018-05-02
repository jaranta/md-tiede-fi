---
layout: page
title: Työnkulku
---

Markdownilla työskentelyn työnkulku voi koostua useista erilaisita työtavoista ja ohjelmista. Tässä esitellään yksi mahdollinen tapa työskennellä.[^tyonkulku] Tässä esitelty esimerkki on toimiva, mutta yksinkertaistettu.

Ensin kirjoitetaan tekstimuotoinen markdown-tiedosto. Se voidaan tallentaa millä tahansa nimellä, mutta on tavanomaista tallentaa markdown-tiedostot joko `.md` tai `.markdown` päätteillä.

Tiedoston `esimerkki.md` sisältö voi olla esimerkiksi seuraavan kaltainen:

~~~~~~
---
title: 'Esimerkki Markdownin käytöstä'
author: Jonne Arjoranta
---

Tässä ensimmäinen kappale.

# Tässä ensimmäinen otsikko

Tässä ensimmäisen otsikon jälkeinen kappale.

## Tässä alaotsikko

Tässä alaotsikon jälkeinen kappale.
~~~~~~

Määrittelemme tekstin alkuun vapaaehtoista metadataa, tässä tapauksessa asiakirjan pääotsikon ja kirjoittajan. Sen jälkeen tulee varsinainen markdown-muotoiltu teksti.

Kun olemme tyytyväisiä tiedoston sisältöön, käytämme markdown-kääntäjää, tässä esimerkissä [Pandocia](http://pandoc.org/README.html). Jos annamme Pandocille käskyn kääntää edellä olevan tiedoston pdf-muotoon, se tapahtuu käskyllä

`pandoc esimerkki.md -o esimerkki.pdf`

Kuten odottaa saattaa, Pandocin tuottamassa pdf-tiedostossa on otsikko, se sisältää kirjoittajan nimen ja sen jälkeen määrittelemämme tekstin. Jos käyttäisimme vaihtoehtoista käskyä

`pandoc esimerkki.md -o esimerkki.html`

saisimme täsmälleen saman tekstin käännettynä html-muotoon. Jos kyseessä olisi tutkimusartikkeli, siitä olisi helppo tuottaa useita erilaisia tiedostomuotoja.[^vaitoskirja] Todelliset esimerkit tutkimuskäytöstä olisivat hieman monimutkaisempia ja sisältäisivät kuvia, viitteitä, kaavoja ja kaikkea muuta, mitä tutkimusartikkeli sisältää.

Esimerkiksi työstämämme artikkelia `tutkimusartikkeli.md`:

~~~~~~
---
title: Tutkimusartikkeli
subtitle: Ratkaisu kaikenlaisiin tärkeisiin kysymyksiin
author:
- name: Jonne Arjoranta
  affiliation: Jyväskylän yliopisto
date: 31.7.2015
bibliography: library.bib
lang: finnish
locale: fi-Fi
csl: apa.csl
abstract: | 
	Tämä tulostuu ensimmäisenä asiakirjaan abstraktiksi, koska käyttämämme artikkelipohja sisältää abstraktin. Jos sitä ei olisi määritelty, sitä ei tulisi asiakirjaan.
---

Tämä kappale esittelee, miten markdown-muotoinen artikkeli voisi olla kirjoitettu. Se sisältää viitteen sekä keskellä lausetta [@Esim2001] että lauseen lopussa [@Esim2002]. Viitteet korvautuvat lopullisessa asiakirjassa oikeanmuotoisilla lähdeviitteillä.

![Tässä on kuvateksti tärkeälle kuvalle](kuvat/kuva1.jpg)

Tässä kappaleessa on *sekä kursivoitua tekstiä* että **lihavoitua tekstiä**, koska näiden asioiden huomioiminen on tärkeää.
~~~~~~

Seuraavaksi käännämme tekstin pdf-muotoiseksi.

`pandoc --filter pandoc-citeproc --template=artikkelipohja.latex tutkimusartikkeli.md -o tutkimusartikkeli.pdf`

Voimme käyttää tähän komentoa, jossa käsketään Pandocia käyttämään filtteriä `pandoc-citeproc` ja korvaamaan viitteet lähdeviitteillä. Metatiedoissa on määritelty `csl: apa.csl`, joten pandoc tietää, miten lähdeviitteet täytyy muotoilla. Käytämme valmista artikkelipohjaa, joten tekstin asettelu on myös oikeanlaista ja kirjoittaessa täytyy kiinnittää huomiota vain kirjoittamiseen.

[^tyonkulku]: Katso myös esimerkiksi [Markus Kainun](http://markuskainu.fi/tools/2013/10/15/markdown-pandoc-tieteellinen-teksti.html) ja [Kieran Healyn](http://kieranhealy.org/blog/archives/2014/01/23/plain-text/) esimerkit. Tässä esitelty työtapa perustuu pitkälti heidän esimerkeilleen.

[^vaitoskirja]: Esimerkkinä väitöskirjani, jonka voi lukea [verkossa html-muodossa](https://jonne.arjoranta.fi/dissertation/) tai [pdf-muotoisena tiedostona](https://jyx.jyu.fi/dspace/handle/123456789/45647), josta on painettu fyysinen kirja. Teksti on käännetty docx-muodosta Pandocilla markdowniksi, jonka [jekyll](http://jekyllrb.com/) tulkitsee html-tiedostoksi verkkosivuilla.

