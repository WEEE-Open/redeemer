# redeemer

Questo script può essere fatto partire da qualsiasi distribuzione GNU/Linux.
L'ideale sarebbe avviarlo come utente "root".

Verificare gli hard disk da redimere usando `fdisk -l`
oppure `lsblk`.

## SINTASSI

    redeemer [OPZIONI] [CORIACEI_DISCHI]
    le opzioni disponibili sono:
        -s --shutdown : spegne il computer al termine dell'esecuzione.
        -c --check    : esegue badblocks sui dischi prima di redimerli.
                        se passano il test, li pulisce, altrimenti
                        lo salta e stampa un messaggio di errore.
        -n --no-sync  : esegue tutti gli step senza eseguire sync.
        -d --dry-run  : non fa nulla di quello che dovrebbe fare.

Questo script può essere eseguito in serie o in parallelo.

## IN SERIE

Usare il comando `redeemer /dev/sda /dev/sdb ... /dev/sdN`.  
Se volete bene all'ambiente aggiungete l'opzione `-s`.  
Se tutti gli hard disk sono, oltre che da pulire,
da testare, aggiungere l'opzione `-c`.  
    
## IN PARALLELO

Lanciare diversi script, uno per ogni hard disk,
evitando di usare l'opzione `-s`, altrimenti appena finisce
di pulire il primo, se gli altri non hanno ancora finito il
computer si spegne prima che gli altri abbiano finito il processo.

## TODO

- [ ] Testare in laboratorio.
