---
title: Zotero
author: Jonne Arjoranta
contributor:
date: 2017-07-11
modified: null
tags:
testattu: Windows 7
versiot: Zotero 4.0.29.17, Zotero Better Bib(La)Tex 1.6.100
---

Zotero voi tuottaa Pandoc-yhteensopivia lähdetietoja, mutta toimii paremmin, jos ottaa avuksi [Zotero Better Bib(La)Tex](https://github.com/retorquere/zotero-better-bibtex) -lisäosan.

Zoteron valikkoihin ilmestyy lisäosan asentamisen jälkeen uusi välilehti, Bietter BibTeX. Better BibTeX siirtää lähdetiedot oletuksena Zoteron oletusmuodossa, mutta se ei välttämättä ole parhaiten yhteensopiva. Parempi muoto on esimerkiksi yksinkertainen `[auth:lower][year]`.

Lisäosa voi synkronoida lähdetiedot automaattisesti, mutta se tapahtuu hieman epäintuitiivisesti:

1. Valitse koko kirjastosi (`My Library`)
2. Valitse hiiren oikealla napilla `Export Library...`
3. Vaihda siirtomuodoksi `Better BibTeX` ja valitse ruutu, joka sanoo `Keep Updated`. Sen jälkeen synkroinointi löytyy Better BibTeXin valikosta.
