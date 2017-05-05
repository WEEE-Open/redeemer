# redeemer

Questo script può essere fatto partire da qualsiasi distribuzione linux.
L'ideale sarebbe avviarlo come utente "root".

Verificare che l'hard disk da macellare sia effettivamente `/dev/sda`
digitando `fdisk -l` oppure `lsblk`.

Questo script può essere eseguito in serie o in parallelo:

IN SERIE:
    Accertarsi che gli hard disk siano collegati.
    Aggiungere allo script le istruzioni necessarie
    a pulire anche gli altri hard disk, ovvero copiare
    paro paro il file (tranne `shutdown -h now`)
    e cambiare solo la lettera finale di `/dev/sda`
    con quella opportuna.


IN PARALLELO:
    Lanciare diversi script, uno per ogni hard disk,
    ricordandosi di rimuovere il comando `shutdown -h now`
    alla fine, altrimenti appena finisce di scannare il primo, se gli
    altri non hanno ancora finito il computer si spegne prima che
    gli altri abbiano finito il processo.


TODO:
  - Implementare un'opzione `-s` per scegliere se spegnere la
    macchina o meno al termine dell'esecuzione dello script.

  - Implementare la lettura da command line della lista di device
    a cui fare il wipe. Se i device in lista sono più di uno li
    esegue in serie, se il device è uno solo fa normalmente.
    In tal modo, se si vuole fare il wipe di tanti hard disk in
    serie, li si scrive nella lista dopo il comando.
    Se si vuole fare il wipe di tanti hard disk in parallelo,
    bisogna avviare tanti script ognuno per ogni hard disk, badando
    bene che non sia attiva l'opzione di spegnimento automatico del
    sistema.
