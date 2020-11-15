# Projekt

Cieľom projektu je osvojiť si základné koncepty a techniky analýzy dát, pochopiť, ako fungujú 
a získať intuíciu pre ich vhodnú aplikáciu za účelom objavovania znalostí v dátach. 
Mali by ste tiež získať predstavu, aké otázky vieme pomocou analýzy dát zodpovedať 
a byť schopní aplikovať a vyhodnotiť základné prístupy strojového učenia.

**Projekt sa vypracúva vo dvojiciach.** 
Pri riešení sa očakáva využitie jazyka `Python` 
a dostupných knižníc na analýzu dát (`pandas`, `numpy`, `scipy`, `scikit-learn`, atd.). 
V každej fáze sa odovzdáva vykonateľný `Jupyter Notebook`, 
ktorý by mal zachytávať a vhodne dokumentovať všetky vykonané transformácie nad dátami. 
Odovzdaný notebook musí obsahovať nielen kód, 
ale aj jeho výsledky (vypočítané hodnoty, výpisy, vizualizácie a pod.) 
spolu s komentárom intrepretujúcim získané výsledky 
a z toho plynúce rozhodnutia pre ďalšie kroky dátovej analýzy. 
Schopnosť dobre odkomunikovať a vybrať relevantné výsledky analýzy 
bude predstavovať významnú zložku hodnotenia. 

**Pri každej fáze v odovzdanom notebooku tiež uveďte percentuálny podiel práce jednotlivých členov dvojice.**

## Dáta
 
Dátová sada predstavuje záznamy pacientov s podozrením na výskyt cukrovky. 
Údaje sú rozdelené do dvoch súborov (opisujú rovnakú množinu pacientov): 
- osobné údaje o pacientoch
- zdravotné údaje o pacientoch. 


**Meranie**
- Pacienti mali po určitú dobu (5-6 dní) zavedený prístroj na nepretržité meranie hladiny cukru a hladiny kyslíku v krvi. 
- Tento prístroj meral tieto dve hodnoty v 30 sekundových intervaloch. 
- Všetky merania boli agregované za celú dobu zberu dát pomocou rôznych agregačných funkcií: 
	priemer, štandardná odchýkla, koeficient asymetrie a koeficient špicatosti. 
- Dátová sada obsahuje pre každú z meraných veličín (hladina cukru a kyslíka v krvi) výsledky týchto agregačných funkcií. 
- Dátová sada obsahuje rôzne základné informácie o pacientovi, ktoré by mohli byť faktormi pri vzniku ochorenia.

Nezávislým testom bola vyhodnotená skutočná prítomnosť ochorenia u pacienta. 
Táto je uložená v stĺpci `class` (názov sa môže líšiť pri niektorých dátových sadách) 
a považujeme ju za **zaručene pravdivú**.


**Dátová sada obsahuje atribúty**
- Agregované výsledky merania hladiny cukru v krvi pomocou 4 rôznych metrík
- Agregované výsledky merania hladiny kyslíku v krvi pomocou 4 rôznych metrík
- Informácie o  pacientovi ako vek, dátum narodenia, najvyššiu úroveň dosiahnutého vzdelania, 
	typ zamestnania, rodinný stav, rasa, pohlavie, krajina narodenia, príjem a týždenné pracovné zaťaženie.
- Závislú premennú indikujúcu skutočnú prítomnosť ochorenia


## Zadanie
- Každá dvojica bude pracovať s im náhodne pridelenou dátovou sadou (4. týždeň, AIS dokumentový server). 
- Vašou úlohou je vedieť predikovať hodnotu **Y** (môže sa líšiť v závislosti od pridelenej dátovej sady). 
- Budete sa musieť pritom vysporiadať s viacerými problémami, ktoré sa v dátach nachádzajú 
	(formáty dát, chýbajúce, nezmyselné alebo vychýlené hodnoty a pod.).


## Fáza 1: Prieskumná analýza (max. 16b)

V tejto fáze sa od Vás očakáva:

**Základný opis dát spolu s ich charakteristikami (5b).** 

Pre dosiahnutie plného počtu bodov uveďte 
- počet záznamov, 
- počet atribútov, 
- ich typy,  
- pre zvolené významné atribúty ich distribúcie, základné deskriptívne štatistiky a pod.

**Párová analýza dát (5b).** 
- Preskúmajte vzťahy medzi zvolenými dvojicami atribútov. 
- Identifikujte závislostí medzi dvojicami atribútov (napr. korelácie) a 
	na závislosti medzi predikovanou premennou a ostatnými premennými (potenciálnymi prediktormi).

**Formulácia a štatistické overenie hypotéz o dátach (2b).** 
- Mali by ste sformulovať aspoň dve hypotézy o dátach, ktoré budú relevantné v kontexte zadanej predikčnej úlohy. 
Príkladom hypotézy v doméne (v závislosti od pridelenej dátovej sady) môže byť, napr. 
	*pacienti s chorobou štítnej žľazy majú v priemere inú (vyššiu/nižšiu) hodnotu nejakej látky 
	alebo hormónu ako pacienti bez danej choroby*. 
- Vami sformulované hypotézy overte vhodne zvoleným štatistickým testom.

**Identifikácia problémov v dátach spolu s predpokladaným scenárom riešenia v ďalšej fáze (4b).** 

Identifikujte, čo a ako budete musieť v rámci predspracovania vyriešiť v ďalšej fáze, napr.: 
- nevhodná štruktúra dát (dáta nie sú v tabuľkovej podobe alebo jedna entita je opísaná viacerými riadkami tabuľky)
- duplicitné záznamy, resp. nejednoznačné mapovanie medzi záznamami
- nejednotné formáty dát
- chýbajúce hodnoty
- vychýlené (odľahlé) hodnoty
- v dátach sa môžu nachádzať aj iné, tu nevymenované problémy.

**V odovzdanej správe (`Jupyter Notebooku`) by ste tak mali vedieť zodpovedať na otázky**
- Majú dáta vhodný formát pre ďalšie spracovanie? Ak nie, aké problémy sa v nich vyskytujú?
- Sú niektoré atribúty medzi sebou závislé? Od ktorých (jednotlivých) atribútov závisí predikovaná premenná?
- Sú v dátach chýbajúce hodnoty? Ako sú reprezentované? Ako plánujete riešiť problém chýbajúcich hodnôt 
pre jednotlivé atribúty, resp. pozorovania? (Pre rôzne atribúty môže byť vhodné použiť rôzne stratégie.)
- Nadobúdajú niektoré atribúty nezmyselné (nekonzistentné) či inak výrazne odchýlené hodnoty? Ktoré?
- Ako plánujete v ďalšej fáze tieto identifikované problémy adresovať / riešiť?

> Správa sa odovzdáva v 6. týždni semestra na cvičení.
> Dvojica svojmu cvičiacemu odprezentuje vykonanú prieskumnú analýzu v `Jupyter Notebooku`). 
> Následne správu elektronicky odovzdá jeden člen z  dvojice do systému AIS do **nedele 01.11.2020 23:59**.


## Fáza 2: Predspracovanie (max. 21b)

Na základe identifikovaných problémov v dátach a návrhu ich riešenia v predchádzajúcej fáze 
treba zrealizovať predspracovanie. Výsledkom by mala byť upravená dátová sada (vo formáte `csv`) 
vo vhodnom tvare pre strojové učenie. 
- To znamená, že jedno pozorovanie musí byť opísané jedným riadkom tabuľky; 
- V tretej fáze budeme pracovať s algoritmom(-ami), ktorého(ých) implementácia podporuje len numerické dáta, 
je možné že bude potrebné všetky nenumerické atribúty transformovať na numerické. 
- Keď sa predspracovaním mohol zmeniť tvar a charakteristiky dát (počet atribútov, distribúcie hodnôt a pod.), 
je možné že treba znovu zrealizovať podstatné časti prieskumnej analýzy a opakovane podľa Vašej potreby. 
- Významnú časť hodnotenia bude predstavovať znovupoužiteľnosť (replikovateľnosť) predspracovania.

V druhej fáze sa od Vás očakáva:

**Integrácia dát a prípadná deduplikácia záznamov (5b).** 

Výsledkom by mala byť jednotná tabuľková reprezentácia dát, ktorá bude predstavovať vstup 
pre ďalšie spracovanie a (v 3. fáze) strojové učenie.

**Realizácia predspracovania dát a ich zdokumentovanie (6b).** 
  - Pri riešení chýbajúcich hodnôt vyskúšajte rôzne stratégie (minimálne 1 stratégiu z 2 nasledujúcich podskupín):
    - nahradenie chýbajúcej hodnoty mediánom, priemerom alebo pomerom ku korelovanému atribútu
    - nahradenie chýbajúcej hodnoty priemerom segmentu, pomocou jednoduchej lineárnej regresie 
    	alebo k-najbližších susedov (kNN)
  - Podobne postupujte aj pri riešení vychýlených hodnôt (outlier): 
    - odstránenie vychýlených (odľahlých) pozorovaní
    - nahradenie vychýlenej hodnoty hraničnými hodnotami rozdelenia (5 percentilom, resp. 95 percentilom)
  - Transformácia atribútu/ov pomocou Power transform (logaritmus, odmocnina a pod.)

**Znovupoužiteľnosť predspracovania (5b).** 
  - Upravte váš kód realizujúci predspracovanie trénovacej množiny tak, aby ho bolo možné bez ďalších úprav 
  	znovupoužiť na predspracovanie validačnej/testovacej množiny (napr. pomocou funkcie/í) 
  - Očakáva sa aj využitie možnosti `sklearn.pipeline`. 
<!--  
  Častým problémom býva využitie informácií, 
ktoré nie sú dostupné v čase zbierania údajov (napr. štatistické informácie o celej testovacej sade 
pri spracovaní trénovacích údajov alebo aj pri spracovaní jednotlivých pozorovaní z testovacej sady), 
čím môžete do trénovania zaniesť znalosť z validačnej alebo testovacej množiny; 
vaše riešenie toto musí ošetrovať.
//-->

**Opätovná realizácia podstatných častí prieskumnej analýzy (5b).** 
  - Očakáva sa že dokumentujete zmeny distribúcie hodnôt po realizácii predspracovania 
  - Následne dokumentujete LEN zmeny v prieskumnej analýze 


> Správa sa odovzdáva v 9. týždni semestra na cvičení.
> Dvojica svojmu cvičiacemu odprezentuje vykonané predspracovanie v `Jupyter Notebooku`). 
> Následne správu elektronicky odovzdá jeden člen z  dvojice do systému AIS do **nedele 22.11.2020 23:59**.


## Fáza 3: Strojové učenie (max. 18b)

Pri dátovej analýze nemusí byť naším cieľom získať len znalosti obsiahnuté v aktuálnych dátach, 
ale aj natrénovať model, ktorý bude schopný robiť rozumné predikcie pre nové pozorovania 
pomocou techniky strojového učenia. 

V tomto projekte sa zameriame na rozhodovacie stromy vzhľadom na ich jednoduchú interpretovateľnosť.
V tejto fáze použite všetky data, ktoré ste dostali. 
Oddemonštrujete znovupoužiteľnosť vami realizovaného predspracovania. 


**Predspracovanie validačného datasetu Vami realizovaným postupom predspracovania a opis prípadných zmien (3b).** 
  - Spustite postup predspracovania realizovaný v predchádzajúcej fáze nad novým datasetom. 
    Nový dataset bude mať rovnakú štruktúru ako váš pôvodný. 
  - Ak si spustenie predspracovania vyžiada zmeny v kóde, opíšte ich. 
    Zabezpečíte aby postup predspracovanie funguje rovnako na obidve datasety.
<!--
nebudú sa v ňom však možno nachádzať niektoré problémy (nové vám nepribudnú). 
-->


**Manuálne vytvorenie a vyhodnotenie rozhodovacích pravidiel pre klasifikáciu (3b).** 
  - Vyskúšajte jednoduché pravidlá zahŕňajúce jeden atribút pre CART, 
    ale aj komplikovanejšie zahŕňajúce viacero atribútov (ich kombinácie). 
  - Pravidlá by v tomto kroku mali byť vytvorené manuálne na základe pozorovaných závislostí v dátach. 
  - Pravidlá (manuálne vytvorené klasifikátory) vyhodnoťte pomocou metrík *accuracy*, *precision* a *recall*. 


**Natrénovanie a vyhodnotenie klasifikátora s využitím rozhodovacích stromov (6b).** 
  - Na trénovanie využite stromový algoritmus (resp. algoritmy) dostupný/é v scikit-learn. 
  - Vizualizujte natrénované pravidlá. 
  - Vyhodnoťte natrénovaný rozhodovací strom pomocou metrík *accuracy*, *precision* a *recall* 
  - Porovnajte natrénovaný klasifikátor s Vašimi manuálne vytvorenými pravidlami z druhého kroku. 


**Optimalizácia hyperparametrov (4b).** 
  - Preskúmajte hyperparametre Vášho zvoleného klasifikačného algoritmu a vyskúšajte ich rôzne nastavenie tak, 
    aby ste minimalizovali overfitting (preučenie) a optimalizovali výsledok. 
    Vysvetlite, čo jednotlivé hyperparametre robia. 
  - Pri nastavovaní hyperparametrov algoritmu využite 10-násobnú krížovú validáciu na trénovacej množine.


**Vyhodnotenie vplyvu zvolenej stratégie riešenia na správnosť klasifikácie (2b).** 
  - Okrem scikit-learn, stretaváme aj s inými knižniciami. 
    Preto dátovú transformáciu vieme spraviť aj v mimo scikit-learn.
  - Manuálne zlučíte trénovaciu a validačnú množinu dát pre strojové učenie (2 csv súbory). 
    Výsledný súbor (1 csv súbor) použite na manuálnu 10-násobnú krížovú validáciu.

<!--
- **Vyhodnotenie vplyvu zvolenej stratégie riešenia chýbajúcich hodnôt na správnosť klasifikácie (2b).** 
Zistite, či použitie zvolených stratégií riešenia chýbajúcich hodnôt vplýva 
na správnosť (angl. accuracy) klasifikácie. Ktorá stratégia sa ukázala ako vhodnejšia pre daný problém?
-->

> Správa sa odovzdáva v 12. týždni semestra na cvičení.
> Dvojica svojmu cvičiacemu odprezentuje výsledky strojového učenia v `Jupyter Notebooku`). 
> Následne správu elektronicky odovzdá jeden člen z dvojice do systému AIS do **nedele 13.12.2020 23:59**.



## References 
- https://github.com/FIIT-IAU
- https://github.com/FIIT-IAU/IAU-2019-2020
