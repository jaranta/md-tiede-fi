---
title: Malli Suomen Akatemian haun tutkimussuunnitelmaan 
author: Jonne Arjoranta
contributor:
date: 2015-10-05
modified:
tags: tutkimussuunnitelma, malli
---

Suomen Akatemia haluaa hauissaan liitteenä tutkimussuunnitelman, jossa vaaditaan (vuonna 2015 ja tutkijatohtoreilta) 12 sivuun paljon tietoa tietyillä asetteluilla. Tein sitä varten [mallipohjan](https://github.com/gitkrax/pandoc-templates/blob/master/aka.latex), jossa on osa vaatimuksista jo valmiiksi asetettuina. Asettelussa on myös kiinnitetty huomiota tilankäyttöön, jotta kahteentoista sivuun saadaan mahtumaan kaikki tarvittava.

Voit ladata mallipohjan itsellesi, kirjoittaa tutkimussuunnitelman markdownilla ja kääntää suunnitelman lähettämistä varten pdf-muotoon. Työtä helpottaa vielä hieman, kun asentaa [`maken`](https://www.gnu.org/software/make/) tai [`winmaken`](http://gnuwin32.sourceforge.net/packages/make.htm) ja tekee itselleen makefilen, jonka avulla voi kääntää tekstin aina tarvittaessa pdf-muotoon tarkistamista varten.

Yksinkertainen makefile voi olla vaikka tällainen:

```
yourlastname_research_plan.pdf:	yourlastname_research_plan.md picture1.png picture2.png
	pandoc \
	--normalize \
	--smart \
	--latex-engine=xelatex \
	--template=aka.latex \
	--filter pandoc-citeproc \
	-o $@ $<
```

Ensimmäiselle riville tulee ensin kohde, eli minkä tiedoston haluat saada tehtyä. Sitten tulevat vaadittavat tiedostot -- kuvat tarvitsee laittaa vaatimuksiksi vain, jos niitä muutetaan ja haluat tehdä uuden version aina kuvien muuttelun jälkeen.

Jos sinulla olisi tutkimussuunnitelma tiedostossa `virtanen_research_plan.md` ja kuvat `picture1.png` ja `picture2.png` samassa kansiossa ylläolevan `makefile`n kanssa, saisit valmiin pdf-version kirjoittamalla komentorivillä `make`.

Käytä Akatemian malliotsikoina tason 1 (#) otsikkoja. Tason 2 (##) otsikoihin kannattaa laittaa kaksoispiste, sillä ne tulevat tilan säästämiseksi tekstin sekaan. Määrittele tiedoston YAML-osiossa marginaalit, esimerkiksi

```
---
geometry: margin=2.54cm
---
```

Tarvittaessa marginaaleja voi hieman pienentää, jos on vaikeuksia saada tekstiä mahtumaan sivumäärään.

Jos haluat asettaa tekstin sekaan taulukkoja markdown-muodossa, niin ne saa esimerkiksi Excelistä markdown-muotoon helposti [Markdown Tables Generatorin](http://www.tablesgenerator.com/markdown_tables) avulla.
