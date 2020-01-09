Romano Matteo 807442
Cantoni Matteo 808104

LINGUAGGI DI PROGRAMMAZIONE - AA 2019-2020 - PROLOG - GENNAIO 2020

--------------------------- FUNZIONI PRIMITIVE ---------------------------------

IS_REGEXP: Prende in input un espressione. Ritorna true se le l'espressione è un
espressione regolare. Le espressioni regolari sono formate da numeri, atomi, 
funtori riservati(seq, or, star, plus) e compound/1. In caso di compound/1 viene
gestito come un atomic(ad esempio baz(42) viene visto come a).

NFA_REGEXP_COMP: Prende in input l'ID dell'automa ed un espressione regolare.
Ritorna true se l'ID non è presente nella base di dati e se l'espressione regolare
è compilabile in un automa. Se ritorna true l'automa con identificatore ID viene 
inserito nella base di dati. Per convenzione all'interno del programma tutti gli
stati dell'automa vengono generati progressivamente con gensym. Se si prova a 
definire un ID che è gia stata definito verrà stampato un messaggio di errore.

NFA_TEST: Prende in input l'ID dell'automa ed una lista. Ritorna true se l'automa
con identificatore ID consuma completamente la lista ricevuta in input e si trova
in uno stato finale.

NFA_CLEAR/0: Ritorna true quando dalla base di dati Prolog vengono rimossi tutti gli
automi definiti.

NFA_CLEAR/1: Prende in input l'ID di un automa. Ritorna true quando dalla base di 
dati Prolog viene rimosso l'automa con identificatore ID.

NFA_LIST/0: Ritorna true quando "lista" la struttura di tutti gli automi presenti
nella base di dati Prolog. In caso di base di dati Prolog vuota genera un errore.

NFA_LIST/1: Prende in input l'ID di un automa. Ritorna true quando "lista" la
struttura dell'automa con identificatore ID.

------------------------------FUNZIONI D'APPOGGIO ------------------------------

CONTROLLO_RE: Viene eseguita in caso RE non sia atomic. Riceve in input come primo
elemento un termine e come secondo elemento una lista. Controlla ricorsivamente
che il primo elemento sia una RE(controllando l'arietà in caso di funzioni riservate).

NFA_COMPILAZIONE: Viene eseguita per creare la struttura dell'automa. Riceve in input
come primo elemento l'ID dell'automa, al secondo elemento un termine, al terzo
elemento una lista, al quarto elemento lo stato iniziale e al quinto elemento lo
stato finale. Ricorsivamente controlla il termine e costruisce la struttura
dell'automa, creando le delta in caso il termine sia atomic o un compound/1 con stato
iniziale e stato finale.

ACCEPT: Viene eseguita ricorsivamente per verificare che un input sia consumato
completamente da un automa. Riceve in input come
primo elemento l'ID dell'automa, al secondo elemento una lista e al terzo elemento lo
stato iniziale. Cerca di fare un passaggio con il primo elemento della lista ricevuta
in input, in caso non possa fa un passaggio con la epsilon e riprova con la lista, fino
a trovarsi in uno stato finale.
