Slovenské sémantické vektory pre word2vec
=========================================

Autorské práva
--------------

Copyright (c) 2015 Essential Data, s.r.o.

Toto dielo je možné používať v súlade s licenciou Apache License, verzia 2.0 z januára 2004

Viac informácií v súbore LICENSE. 

Zaujíma vás práca s jazykom? Pracujte pre nás!
----------------------------------------------

Essential Data pracuje s jazykom, s dátami a na zaujímavých projektoch. Pozrite si
[aktuálne otvorené pozície](http://www.essential-data.sk/pracujte-pre-nas/) a pracujte v skvelom
tíme plnom šikovných ľudí.

O projekte
----------

Tento projekt je určený pre použitie s nástrojom [word2vec](https://code.google.com/p/word2vec/). Obsahuje
vygenerované sémantické vektory z jazykového korpusu, ktorý obsahuje cca 110 miliónov slov. Nástroj,
pomocou ktorého boli vygenerované je zverejnený v projekte [word2vec-sk-gen](https://github.com/essential-data/word2vec-sk-gen).
Tento nástroj však neobsahuje všetky zdrojové dáta, nakoľko nemáme právo ich zverejniť. Ak nemáte prístup
k dostatočne veľkému korpusu dát, odporúčame použiť tieto natrénované vektory a negenerovať ich znova,
nakoľko kvalita vektorov čisto zo slovenskej wikipedie nie je natoľko dobrá ako dáta natrénované z väčšieho
korpusu.

Boli použité obidva podporované algoritmy (continuous bag of words, skip-gram). Slovníky, v ktorých mene sa
nachádza reťazec "lemma" boli natrénované na korpuse, ktorý prešiel morfologickou úpravou (známych) slov na
základný tvar lematizátorom.

Použitie
--------

Sémantické vektory majú mnohé zaujímavé vlastnosti. Zachovávajú vzťahy (napríklad pri spustení nástroja
word-analogy a zadaní slov ``Francúzsko Paríž Nemecko`` najbližší vektor k výsledku je slovo ``Berlín``.

Takto je možné vytvárať aj triedy slov pre clustering a množstvo iných užitočných aplikácií.

Technické detaily
-----------------

Slovník bol natrénovaný pomocou nasledovných príkazov:

    word2vec -train corpus-merged-lemma.txt -output vec-sk-cbow-lemma -size 200 -window 5 -sample 1e-4 -negative 5 -hs 0 -binary 1 -cbow 1 -iter 3 -threads 4
    word2vec -train corpus-merged.txt -output vec-sk-cbow -size 200 -window 5 -sample 1e-4 -negative 5 -hs 0 -binary 1 -cbow 1 -iter 3 -threads 4
    word2vec -train corpus-merged-lemma.txt -output vec-sk-skipgram-lemma -size 200 -window 10 -sample 1e-4 -negative 5 -hs 0 -binary 1 -cbow 0 -iter 3 -threads 4
    word2vec -train corpus-merged.txt -output vec-sk-skipgram -size 200 -window 10 -sample 1e-4 -negative 5 -hs 0 -binary 1 -cbow 0 -iter 3 -threads 4


Odkazy
------

* [Github spoločnosti Essential Data](https://github.com/essential-data/) - obsahuje naše open-source projekty (aj) pre prácu s jazykom
* [Aktuálne otvorené pozície](http://www.essential-data.sk/pracujte-pre-nas/) v spoločnosti Essential Data
* [word2vec](https://code.google.com/p/word2vec/) - nástroj pre vytvorenie a používanie sémantických vektorov
* [word2vec-sk-gen](https://github.com/essential-data/word2vec-sk-gen) - nástroj, ktorým boli prefiltrované a vygenerované slovenské vektory.