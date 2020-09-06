# Informácie o dátovej sade

J. Ševcech: [Dátová sada](https://drive.google.com/drive/folders/1qsPo2LLpPypq9IQZViOZ4rFZg5IA4ccR)

Dátová sada predstavuje záznamy pacientov s podozrením na výskyt cukrovky. 
Údaje sú rozdelené do dvoch súborov: osobné údaje o pacientoch a zdravotné údaje o pacientoch. Tieto súbory opisujú rovnakú množinu pacientov.

Pacienti mali po určitú dobu (5-6 dní) zavedený prístroj na nepretržité meranie hladiny cukru a hladiny kyslíku v krvi. Tento prístroj meral tieto dve hodnoty v 30 sekundových intervaloch. Všetky merania boli agregované za celú dobu zberu dát pomocou rôznych agregačných funkcií: priemer, štandardná odchýkla, koeficient asymetrie a koeficient špicatosti. Dátová sada obsahuje pre každú z meraných veličín (hladina cukru a kyslíka v krvi) výsledky týchto agregačných funkcií. Zároveň dátová sada obsahuje rôzne základné informácie o pacientovi, ktoré by mohli byť faktormi pri vzniku ochorenia.

Nezávislým testom bola vyhodnotená skutočná prítomnosť ochorenia u pacienta. Táto je uložená v stĺpci `class` (názov sa môže líšiť pri niektorých dátových sadách) a považujeme ju za zaručene pravdivú.

## Informácie o atribútoch

Dátová sada obsahuje atribúty:
- Agregované výsledky merania hladiny cukru v krvi pomocou 4 rôznych metrík
- Agregované výsledky merania hladiny kyslíku v krvi pomocou 4 rôznych metrík
- Informácie o  pacientovi ako vek, dátum narodenia, najvyššiu úroveň dosiahnutého vzdelania, typ zamestnania, rodinný stav, rasa, pohlavie, krajina narodenia, príjem a týždenné pracovné zaťaženie.
- Závislú premennú indikujúcu skutočnú prítomnosť ochorenia

Zdroj: [Intelligent Data Analysis at FIIT STU in 2019/2020](https://github.com/robom/IAU-2019-2020)
