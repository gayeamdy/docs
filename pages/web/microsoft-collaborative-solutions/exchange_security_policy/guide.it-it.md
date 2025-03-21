---
title: Gestire la politica di sicurezza di un servizio di posta elettronica
slug: gestire-politica-di-sicurezza-password
excerpt: Come configurare la politica di sicurezza del tuo servizio di posta elettronica
section: Iniziare a utilizzare Exchange
order: 6
---

**Ultimo aggiornamento: 09/06/2020**

## Obiettivo

I servizi di posta elettronica di OVHcloud permette di usufruire di indirizzi email professionali. Per preservare l’ambiente di lavoro è possibile, ad esempio, gestire i parametri generali relativi alla sicurezza dei propri account.

**Come configurare la politica di sicurezza del tuo servizio di posta elettronica.**

## Prerequisiti

- Disporre di un [servizio di posta elettronica OVHcloud](https://www.ovhcloud.com/it/emails/){.external}.
- Avere accesso alla sezione [Web](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.it/&ovhSubsidiary=it) dello [Spazio Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.it/&ovhSubsidiary=it)

## Procedura

Il servizio di posta permette di configurare la politica di sicurezza in modo da consentire le seguenti azioni:

- aumentare la sicurezza degli account Exchange quando gli utenti tentano di effettuare l’accesso
- rendere più complesse le password associate agli account del servizio Exchange
- rafforzare la verifica dei messaggi in entrata sui nostri server e destinati ai tuoi indirizzi email (esclusivamente per gli account [Exchange](https://www.ovhcloud.com/it/emails/hosted-exchange/){.external});
- definire la modalità di visualizzazione dei messaggi indesiderati nei tuoi account di posta elettronica (esclusivamente per gli account [Exchange](https://www.ovhcloud.com/it/emails/hosted-exchange/){.external}).

Per accedere alla politica di sicurezza del tuo servizio Exchange accedi allo [Spazio Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.it/&ovhSubsidiary=it), sezione “Web”. 

|Emails e Email Pro|Exchange| 
|---|---| 
|Clicca su `Emails`{.action} o `Email Pro`{.action} nella colonna di sinistra e seleziona la tua offerta. Clicca sulla scheda `Altre opzioni` e seleziona `Gestisci la politica di sicurezza`{.action}.|Clicca su `Microsoft`{.action} nella colonna di sinistra e poi su `Exchange`{.action}, quindi seleziona la tua offerta. Clicca sulla scheda `Altre opzioni` e seleziona` Gestisci la politica di sicurezza`{.action}.|
|![exchangesecurity](images/manage-security01.png){.thumbnail}|![exchangesecurity](images/manage-security02.png){.thumbnail}|

Prosegui nella lettura di questa guida consultando la sezione corrispondente all’azione che vuoi effettuare:

|Azione|Descrizione| 
|---|---| 
|[Aumentare la sicurezza della connessione](./#aumentare-la-sicurezza-della-connessione){.external}|Permette di definire se gli account devono essere bloccati dopo un certo numero di tentativi di connessione non andati a buon fine.|
|[Rendere la password più complessa](./#rendere-la-password-piu-complessa){.external}|Permette di stabilire i requisiti di complessità e le regole relative alla modifica della password.|
|[Aumentare il controllo dei messaggi in entrata (esclusivamente per Exchange)](./#aumentare-il-controllo-dei-messaggi-in-entrata-esclusivamente-per-exchange){.external}|Permette di indicare se i server OVHcloud devono verificare che i messaggi ricevuti provengano da una sorgente legittima (verifiche DKIM e/o SPF).|
|[Definire la visualizzazione dei messaggi indesiderati|Permette di indicare se assegnare ai messaggi indesiderati un tag che consenta di identificarli o spostarli automaticamente nel cestino.|

### Aumentare la sicurezza della connessione

Questa azione permette di definire se gli account di posta elettronica devono essere bloccati dopo un certo numero di tentativi di connessione non andati a buon fine.

Per farlo, completa le informazioni indicate nella seguente tabella:  

|Campo|Descrizione| 
|---|---| 
|Limite di blocco|Imposta il numero di tentativi di connessione non riusciti tollerati prima di bloccare l’account. Se il valore inserito è “0”, non viene applicato nessun limite di blocco.|
|Tempo di attesa prima della reinizializzazione|Questo campo compare soltanto se viene impostato un limite di blocco. Indica l’intervallo di tempo che deve trascorrere prima che il contatore dei tentativi di connessione non riusciti venga azzerato.|
|Durata del blocco|Questo campo compare soltanto se viene impostato un limite di blocco. Indica l’intervallo di tempo in cui l’account email resterà bloccato in caso di raggiungimento del limite di blocco.|

Una volta completate le informazioni, clicca su `Seguente`{.action} > `Conferma`{.action} per applicare le modifiche relativamente alle soluzioni “Emails” e “Email Pro”. Clicca su `Salva le modifiche`{.action}per la soluzione Exchange. 

### Rendere la password più complessa

Questa azione stabilire i requisiti di complessità e le regole relative alla modifica della password.

Per farlo, completa le informazioni indicate nella seguente tabella:  

|Campo|Descrizione| 
|---|---| 
|Requisiti di complessità|Permette di impostare le regole relative alla complessità delle password:<br> - non deve contenere interamente o in parte il nome dell’account utente<br> - deve contenere almeno 6 caratteri<br> - deve contenere lettere maiuscole, minuscole, caratteri speciali (come “!” o “$”) e numeri|
|Impedisci la modifica della password|Consente di definire la durata di vita minima delle password associate agli account di posta elettronica: gli utenti dovranno attendere un certo numero di giorni prima di poter modificare la password impostata.|
|Durata di validità massima della password|Consente di definire la durata di vita massima delle password associate agli account di posta elettronica. il sistema richiederà all’utente di modificare la password alla scadenza dell’intervallo di tempo impostato.|
|Conserva lo storico delle password (esclusivamente per Exchange)|Questo campo compare soltanto se è stata impostata una durata di vita massima. Indica la durata di vita massima, in giorni, delle password precedenti che possono essere nuovamente utilizzate.|
|Lunghezza minima della password|Consente di impostare un numero minimo di caratteri per la password.|

Una volta completate le informazioni, clicca su `Seguente`{.action} > `Conferma`{.action} per applicare le modifiche relativamente alle soluzioni “Emails” e “Email Pro”. Clicca su `Salva le modifiche`{.action}per la soluzione Exchange. 

### Aumentare il controllo dei messaggi in entrata (esclusivamente per Exchange)

Questa azione permette di indicare se i server OVH devono verificare che i messaggi ricevuti provengano da una sorgente legittima (verifiche DKIM e/o SPF).

Per farlo, seleziona le caselle interessate nella tabella seguente:

|Campo|Descrizione| 
|---|---| 
|Attiva la verifica della firma DKIM|Indica se i server OVH devono verificare la firma DKIM dei messaggi ricevuti sugli account Exchange. Questa azione garantisce l’autenticità del dominio del mittente e l’integrità del messaggio. Consente inoltre di identificare invii non legittimi, che verranno contrassegnati come Spam.|
|Attiva la verifica della protezione SPF|Indica se i server OVH devono verificare che la sorgente dei messaggi ricevuti sia presente nel record SPF del dominio mittente. Questa verifica consente di identificare invii non legittimi, che verranno contrassegnati come Spam.|

Una volta effettuata la scelta, clicca su `Salva le modifiche`{.action} per confermare l’operazione. 

### Definire la visualizzazione dei messaggi indesiderati (esclusivamente per Exchange)

Questa azione permette di indicare se assegnare ai messaggi indesiderati un tag che consenta di identificarli o spostarli automaticamente nel cestino.

Per farlo, seleziona le caselle interessate nella tabella seguente:

|Campo|Descrizione| 
|---|---| 
|Identifica i messaggi indesiderati|Indica se i server OVH devono aggiungere un tag per identificare la posta indesiderata come Spam.|
|Sposta la posta indesiderata nel cestino|Indica se i server OVH devono spostare automaticamente la posta indesiderata nel cestino.|

Una volta effettuata la scelta, clicca su `Salva le modifiche`{.action} per confermare l’operazione. 

## Per saperne di più

Contatta la nostra Community di utenti all’indirizzo <https://community.ovh.com/en/>.
