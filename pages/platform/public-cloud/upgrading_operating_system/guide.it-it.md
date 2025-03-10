---
title: Aggiorna il tuo sistema operativo
slug: upgrade-os
excerpt: Come aggiornare un sistema operativo alla fine del ciclo di vita
section: Tutorial
---

> [!primary]
> Questa traduzione è stata generata automaticamente dal nostro partner SYSTRAN. I contenuti potrebbero presentare imprecisioni, ad esempio la nomenclatura dei pulsanti o alcuni dettagli tecnici. In caso di dubbi consigliamo di fare riferimento alla versione inglese o francese della guida. Per aiutarci a migliorare questa traduzione, utilizza il pulsante "Modifica" di questa pagina.
>

**Ultimo aggiornamento: 09/07/2021**

## Obiettivo

Questa guida descrive gli step da seguire per aggiornare un sistema operativo alla fine del ciclo di vita verso una nuova versione.

> [!alert]
> Avviso: come per qualsiasi aggiornamento significativo di un sistema operativo, esiste il rischio di guasto, perdita di dati o guasto della configurazione software.
> Pertanto, prima di seguire questo tutorial, OVHcloud raccomanda vivamente di [salvare l'istanza](../effettuare-snapshot-di-un-istanza/) e di effettuare test approfonditi sulle applicazioni, per assicurarti che funzionino sulla nuova versione del sistema operativo.
>

> [!primary]
> Per evitare i problemi di cui sopra, ti consigliamo di installare una nuova istanza con il nuovo sistema operativo verso il quale effettui l'aggiornamento e di migrare i dati.
> Potrebbe essere necessario effettuare un esame delle differenze nell'applicazione, ma il sistema operativo risulterà probabilmente più stabile.
>

## Prerequisiti

- Avere un [accesso root al server](../imposta_una_password_amministratore/)
- Aver effettuato [un backup della tua istanza](../effettuare-snapshot-di-un-istanza/)

## Procedura

### Ubuntu

Prima di effettuare l'aggiornamento della versione principale del tuo OS, assicurati di aggiornare le versioni più recenti di tutti i pacchetti installati sulla sua versione attuale:

```sh
$ sudo apt-get update
```

Procedi con l'aggiornamento dei tuoi pacchetti installati verso le loro ultime versioni:

```sh
$ sudo apt-get upgrade -y
```

Una volta terminata questa operazione, effettua un *dist-upgrade* che eseguirà gli altri aggiornamenti che potrebbero essere necessari:

```sh
$ sudo apt-get dist-upgrade -y
```

L'aggiornamento della versione principale può essere effettuato. Ubuntu fornisce un tool chiamato *do-release-upgrade* che rende l'aggiornamento più sicuro e più semplice. Per prima cosa, esegui l'aggiornamento utilizzando questo comando:

```sh
$ sudo do-release-upgrade
```

Segui le indicazioni fornite. Confermo principalmente che vuoi continuare l'aggiornamento.

Osservazioni:

- Il tool può richiedere di riavviare il server prima di effettuare l'aggiornamento. Per farlo, basta digitare "riavvio" e premere Invio.
- Ti informiamo che l'esecuzione di questa operazione tramite una connessione SSH non è consigliata. Dato che il server non ha accesso fisico, la connessione in SSH è la principale via di accesso al server.
Ubuntu avvierà un nuovo servizio SSH su un'altra porta per mantenere un altro accesso in caso di malfunzionamenti. Inoltre, se non hai più accesso in SSH, puoi sempre accedere al server tramite la console.
- Durante il processo di aggiornamento, potrebbe essere necessario confermare l'eliminazione dei pacchetti che non sono più supportati. Verifica che questo non abbia alcun impatto sulle tue applicazioni prima di continuare.

Una volta terminato l'aggiornamento, il server procederà a un riavvio e perderai la connessione fino al riavvio.
Pochi minuti dopo, dovrai essere in grado di connetterti e visualizzare un messaggio simile a questo (la versione successiva sarà disponibile rispetto alla versione precedente):

```sh
$ Welcome to Ubuntu 18.04.5 LTS (GNU/Linux 4.15.0-147-generic x86_64)
```

> [!primary]
> Quando aggiorna il sistema operativo invece di reinstallarlo, la nuova versione del tuo OS non è indicata sullo Spazio Cliente OVHcloud o sull'API Horizon/OpenStack.
>

Verifica che le tue applicazioni funzionino come previsto. In caso di problemi, ti consigliamo di [ripristinare il backup](../crearipristina_il_tuo_server_virtuale_da_un_backup/) prima dell'aggiornamento.

### Fedora

Prima di effettuare l'aggiornamento della versione principale del sistema operativo, assicurati di aggiornare le versioni più recenti di tutti i pacchetti installati sulla sua versione attuale. Inserisci questo ordine:

```sh
$ sudo dnf upgrade --refresh
```

Riavvia il server:

```sh
$ reboot
```

Una volta riavviato il server, installa il pacchetto di aggiornamento:

```sh
$ sudo dnf install dnf-plugin-system-upgrade
```

Una volta attivato il pacchetto, è possibile eseguire l'aggiornamento. Gli aggiornamenti del sistema sono ufficialmente presi in carico e testati solo su un massimo di 2 versioni (ad esempio da 32 a 34).
In questo esempio, passeremo da Fedora 32 a 33:

```sh
$ sudo dnf system-upgrade download --releasever=33
$ sudo dnf system-upgrade reboot
```

Una volta avviato il download della versione e il processo di aggiornamento, il server riavvia per completare l'aggiornamento.
<br>Potrebbe trascorrere un po' di tempo prima di poter ricollegarsi al server, perché l'aggiornamento richiede tempo.

Verifica che le tue applicazioni funzionino come previsto. In caso di problemi, ti consigliamo di [ripristinare il backup](../crearipristina_il_tuo_server_virtuale_da_un_backup/) prima dell'aggiornamento.

> [!primary]
> In caso di difficoltà o dubbi, consulta il sito [Fedora Doc](https://docs.fedoraproject.org/en-US/quick-docs/dnf-system-upgrade/){.external}.
>

## Per saperne di più

Contatta la nostra Community di utenti all’indirizzo <https://community.ovh.com/en/>.
