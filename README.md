# redeemer
[![License](http://img.shields.io/:license-GPL3.0-blue.svg)](http://www.gnu.org/licenses/gpl-3.0.html)
![Version](https://img.shields.io/badge/version-1.2-yellow.svg)

rischia_di_piantarsi="si pianta di sicuro"  

Questo script può essere fatto partire da qualsiasi distribuzione GNU/Linux.  
Deve essere avviato come utente `root`.  
Utilizzando solamente `sudo` ${rischia_di_piantarsi} in quanto richiederebbe  
nuovamente la password una volta completato un passo, e questo avverrà esattamente  
il venerdì sera quando lancerete questo script poco prima di chiudere il laboratorio,  
e quando il calcolatore vi richiederà la password voi sarete già a casa vostra,  
ignari di tutto.

## Sintassi del comando

    redeemer [OPZIONI] [CORIACEI_DISCHI]
    le opzioni disponibili sono:
        -s --shutdown : spegne il computer al termine dell'esecuzione.
        -c --check    : esegue badblocks sui dischi prima di redimerli.
                        se passano il test, li pulisce, altrimenti
                        lo salta e stampa un messaggio di errore.
        -n --no-sync  : esegue tutti gli step senza eseguire sync.
        -d --dry-run  : non fa nulla di quello che dovrebbe fare.

## How it works
Redeemer esegue una pulizia totale del disco rigido eseguendo 4 cicli di scrittura,  
una scrittura di zeri, una scrittura di uno, una scrittura di valori pseudo-casuali  
ed infine un'ultima scrittura di zeri (redenzione).  
La pulizia viene eseguita in parallelo su tutti i dischi specificati dall'utente.  
Per far questo si serve di una ricorsione che richiama lo script stesso  
generando dei sottoprocessi figli, e una volta eseguita questa chiamata ricorsiva  
lo script attenderà il termine dei processi figli prima di eseguire ulteriori  
operazioni (come ad esempio lo spegnimento automatico del sistema programmabile  
tramite l'opzione `-s|--shutdown`).

## ToDo

- [ ] Aggiungere un'opzione `-o|--output-file` per dare la possibilità di salvare
su file l'output dello script.
