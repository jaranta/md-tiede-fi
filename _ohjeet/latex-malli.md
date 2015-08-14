---
title: LaTeX-mallin käyttö Pandocin kanssa
author: Jonne Arjoranta
contributor:
copyright:
date: 2015-08-15
modified:
tags: latex, pandoc
---

Yksi Pandocin käytöstä seuraava etu on mahdollisuus käyttää valmiita mallitiedostoja, jotka sisältävät asetteluun liittyvät tiedot. Kirjoittaessa voi silloin keskittyä vain kirjoittamiseen.

Oletuksena Pandoc käyttää sisäänrakennettuja malleja, jotka pääsee näkemään komennolla `pandoc -D FORMAT`, missä FORMAT tarkoittaa haluttua tiedostotyyppiä (esim. docx, markdown).

Malleja voi muokata myös itse. Pandoc tarkistaa ajettaessa data-kansionsa ja käyttää sieltä löytyviä malleja pyydettäessä. Data-kansion sijainnin näkee komennolla `pandoc --version`. Malleja etsitään oletuksena data-kansion alta löytyvästä *templates*-kansiosta -- sen voi luoda itse, jos sellaista ei vielä ole olemassa.

Käytän itse artkkelien pohjana ja esikatseluun Pandocin oletustyyleistä muokattua *article.latex*-mallia. Se löytyy Githubista, jossa [*templates*-kansioni on git-arkistona](https://github.com/gitkrax/pandoc-templates). Valmiita malleja voi etsiä myös verkosta. Mallipohjani ei noudata mitään tiettyä tieteellisen julkaisun mallia, vaan mahdollistaa suhteellisten selkeiden artikkelien asettelun muutamalla eri tavalla. Voit käyttää mallipohjaa omassa työssäsi ja muokata sitä tarpeen vaatiessa.

Mallipohja tukee ainakin seuraavia muuttujia:

* `twocolumn: true` -- teksti asettuu kahteen palstaan
* `endnotes: true` -- viitteet ovat alaviitteiden loppuviitteitä
* Tekijän nimi ja yliopisto asiakirjan alkuun:

        author:
        - name: Nimi
          affiliation: Yliopiston nimi

Nämä pitää sijoittaa asiakirjan alussa olevaan [YAML-osioon](http://pandoc.org/README.html#metadata-blocks).

Pandocia voi pyytää käyttämään jotain mallipohjaa käyttämällä vaihtoehtoa `--template=article.latex`. Esimerkiksi käsky

`pandoc --template=article.latex artikkeli.md -o artikkeli.pdf`

muuttaa markdown-muotoillun tekstin latexin kautta pdf-muotoon.

Lisätietoa malleista löytyy [Pandocin dokumentaatiosta](http://pandoc.org/README.html#templates).
