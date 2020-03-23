---
title: Rischio (risk), Quote (Odds), Rapporto tra quote (Odds Ratio)
author: "Corrado Lanera"
date: "2020/03/23"
output: 
  html_document: 
    keep_md: yes
---


Un **rischio** è la probabilità di osservare qualcosa. Quando questo
_qualcosa_ ha un effetto (moralmente) negativo, solitamente lo chiamiamo
"rischio".

Un rischio è quindi sempre compreso tra 0 e 1!

L'**odds** è una "quota" (in italiano), quella che rappresenta a
quanto è "quotato" un certo evento (contro il suo opposto). Esempio
"la sua morte la danno 5 a 1", ovvero ha 5 volte più probabilità di
morire __rispetto__ a vivere (il suo contrario!). Il "rispetto a" è la
parola chiave. Chiaramente "5 a 1" può essere espresso con un solo
numero: 5, eseguendo la divisione $5:1$.

Dunque, considerando **due opzioni** complementari e mutuamente
esclusive (che possono essere solitamente morto/vivo), l'odds mi
rappresenta il rapporto tra la probabilità dell'una rispetto alla
probabilità dell'altra, ovvero risponde alla domanda, nell'esempio
vivo/morto, "quanto è più probabile che muoia rispetto a che viva?"

Mentre dunque il rischio mi dice qual'è la probabilità che io muoia
($p$), l'odds mi dice quanto è più probabile che muoia rispetto a che
viva ($o = \frac{p}{1-p}$)!

L'odds è quindi sempre positivo, e se maggiore di 1 vuol dire che
è più probabile che accada che muoia rispetto a che viva (anche se,
attenzione!, non mi dice nulla quanto valga questa probabilità,
seppur la si possa calcolare a ritroso come $p = \frac{o}{1+o}$);
se invece è compreso tra 0 e 1, allora vuol dire che il denominatore
(probabilità di vivere) è maggiore del numeratore (probabilità di
morire), ovvero è più probabile che io viva rispetto a che muoia
(sempre consapevoli che, a meno di ricalcolarsela, non so quanto sia
questa probabilità)

Bene. A questo punto possiamo calcolare tale odds per vari fattori,
per esempio l'essere trattato o meno con un farmaco. Allora abbiamo
dunque l'odds **se prendo il farmaco** ($o_f$) e l'odds
**se non prendo il farmaco** (ovvero prendo un placebo, $o_p$).
Di nuovo, possiamo calcolare il rapporto tra questi odds
(OR = $\frac{o_f}{o_p}$ = \frac{\frac{p_f}{1-p_f}}{\frac{p_p}{1-p_p}}
ovvero calcoliamo l'**odds ratio**, il cui risultato risponde quindi
alla domanda "di quanto aumenta la mia probabilità di morire,
rispetto a quella che io viva, se prendo il farmaco, rispetto a se
non lo prendo?".

Dunque l'odds ratio è anch'esso sempre positivo, e se maggiore di 1
allora vuol dire che il numeratore del rapporto (l'odd di morte se
prendo il farmaco) è maggiore del denominatore (l'odd di morte se
non prendo il farmaco), e quindi prendere il farmaco aumenta l'odds
di morte!! Nota: questo non vuol dire né che l'odd di morte sia
maggiore di uno in un caso o nell'altro, né ancora meno che la
probabilità di morire sia a un certo livello, alta o bassa... mi dice
solo che prendere il farmaco fa aumentare il rapporto tra la
probabilità di morire e di vivere...ovvero mi sta suggerendo che,
dovendo scommettere sulal ia morte, ora, avendo preso il farmaco,
mi conviene più che nell'altro caso scommettere che morirò! Tutto li!

Nota: per le variabili dicotomiche questo il calcolo e
l'interpretazione è automatico e vincolata (o prendo il farmaco o
no)!, ma l'odds ratio (di morte rispetto alla vita, per esempio) lo
si può calcolare anche per variabili continue, ma serve prendere due
riferimenti. per esempio, posso calcolare l'odds ratio di morte
rispetto a vivere confrontando l'odd a 20 anni con quello di 60... e
quindi valutare quanto quanto in più mi conviene scommettere sulla
morte di un sessantenne rispetto a scommettere sulla morte di un
ventenne. Da notare anche che ipotizzando una relazione lineare,
l'unica cosa che conta è la differenza tra (in questo esempio) le due
età... infatti l'odds ratio non cambierà per nulla se lo calcolo tra
20 e 60 o tra 40 e 80, perchè la differenza è sempre di 40, e la
relazione è lineare. Potrei quindi dire, in generale che "un aumento
di quarant'anni mi porta a una convenienza nello scommettere che
morirò di x" (dove x è l'odds ratio calcolato tra due punti qualsiasi
distanti 40 tra loro...che tanto è sempre uguale!). Nel caso invece
in cui la relazione non sia lineare allora i "punti esatti" che
confronto sono importanti perchè l'odds ratio potrebbe cambiare se
calcolato tra 20 e 60 o tra 40 e 80 anni.

Nota 2: informaticamente le variabili dicotomiche vengono
generalmente codificate come "vero/falso", che si traduce dentro
al computer come "1/0". Inoltre di solito si classifica come "vero",
o "positivo", o "1", l'èvento di interesse, quindi nel nostro esempio
la morte, o l'assunzione del farmaco. Dunquq in generale, quando si
tratta di variabili dicotomiche l'odds ratio rappresenta l'aumento
del vantaggio nel scommettere sull'osservare l'evento di interesse
nel caso in cui si verifichi la condizione sotto esame, rispetto a
che non si verifichi. Per esempio, nel nostro caso, un odds ratio
su `RECIDIVE.DI.DISSEZIONE` rispetto a `PROSSIMALE` mi dice quanto
è più probabile osservare una recidiva rispetto a non osservarla, nel
caso in cui valga il prossimale rispetto al caso in cui non valga.
Dunque, se questo odds ratio fosse maggiore di 1, allora vorrebbe
dire che mi conviene scommetere di più sull'avvenimento di una
recidiva se vale prossimale, rispetto a quanto mi converrebbe
scommettere su una recidiva se non valesse prossimale (ricordando che
non so assolutamente nulla su quanto sia il riscio di recidiva né in
caso di prossimale né in caso di non prossimale (rischio che potrebbe
anche essere bassissimo in entrambe le situazioni)!!)
