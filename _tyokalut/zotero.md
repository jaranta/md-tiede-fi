---
title: Zotero
author: Jonne Arjoranta
contributor:
date: 2017-07-11
modified: 2018-05-03
tags:
testattu: Windows 7, Mac OS, Linux
versiot: Zotero 5.0.47, Zotero Better Bib(La)Tex 5.0.133
---

Zotero voi tuottaa Pandoc-yhteensopivia lähdetietoja, mutta toimii paremmin, jos ottaa avuksi [Zotero Better Bib(La)Tex](https://github.com/retorquere/zotero-better-bibtex) -lisäosan.

## Lähdetietojen avaimet

Zoteron valikkoihin ilmestyy lisäosan asentamisen jälkeen uusi välilehti, Better BibTeX. Better BibTeX luo lähdetietoihin viittaavat avaimet oletuksena Zoteron oletusmuodossa, mutta se ei välttämättä ole paras. Parempi muoto on esimerkiksi yksinkertainen `[auth:lower][year]`. Hieman monimutkaisempi `[auth][>0][year]|[title][year]` toimii myös hyvin: se käyttää kirjoittajan nimeä ja vuosilukua, paitsi jos kirjoittaja puuttuu, jolloin avaimena toimii otsikko ja vuosiluku.

## Synkronointi

Lisäosa voi synkronoida lähdetiedot automaattisesti, mutta se tapahtuu hieman epäintuitiivisesti:

1. Valitse koko kirjastosi (`My Library`)
2. Valitse hiiren oikealla napilla `Export Library...`
3. Vaihda siirtomuodoksi `Better BibTeX` ja valitse ruutu, joka sanoo `Keep Updated`. Sen jälkeen synkroinointi löytyy Better BibTeXin valikosta.
