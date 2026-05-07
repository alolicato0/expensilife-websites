# Informativa sulla Privacy — ExpensiLife

**Ultimo aggiornamento:** 6 maggio 2026

La presente Informativa sulla Privacy descrive come ExpensiLife
(di seguito "ExpensiLife", "noi", "nostro") raccoglie, utilizza e
protegge i dati personali degli utenti dell'applicazione mobile
ExpensiLife (di seguito "App"), in conformità al Regolamento (UE)
2016/679 ("GDPR") e al D.Lgs. 196/2003 e ss.mm.ii. ("Codice Privacy").

## 1. Titolare del trattamento

Il Titolare del trattamento dei dati è:

- **Alberto Lolicato** (persona fisica / ditta individuale)
- **Codice Fiscale:** LLCLRT92R20C351C
- **Sede:** Ariccia (RM), Lazio, Italia
- **Email contatto privacy:** lolicatoalberto@gmail.com

L'utente può rivolgersi al Titolare in qualsiasi momento per
esercitare i diritti previsti dagli artt. 15-22 GDPR (vedi sezione 9).

## 2. Dati personali raccolti

ExpensiLife raccoglie e tratta le seguenti categorie di dati:

### 2.1 Dati di registrazione e profilo
- Nome e cognome
- Indirizzo email
- Password (memorizzata esclusivamente come **hash bcrypt**, mai in
  chiaro)
- Valuta predefinita scelta dall'utente
- Lingua preferita (italiano/inglese)

### 2.2 Dati di utilizzo dell'app
- **Trasferte create dall'utente**: titolo, destinazione, date,
  cliente, note
- **Spese registrate**: importo, valuta, categoria, esercente, data,
  note, eventuale ricevuta allegata
- **Tragitti**: indirizzi di partenza/arrivo, distanza calcolata,
  mezzo di trasporto, data
- **Categorie personalizzate** (solo utenti Pro)
- **Stato dell'abbonamento Pro** (data scadenza, fonte: trial /
  subscription / admin)

### 2.3 Immagini delle ricevute
Quando l'utente effettua la scansione di uno scontrino o carica
una foto da galleria, l'**immagine viene inviata al backend di
ExpensiLife** e successivamente:

1. **Trasmessa al servizio Google Gemini** (Generative Language API)
   per l'estrazione automatica di importo, data, esercente e
   categoria mediante OCR/AI;
2. **Memorizzata** sul backend (codifica base64 nel database) per
   essere riutilizzata nei report e in PDF allegati alle email;
3. **Allegata** alle email di rendicontazione che l'utente decide di
   inviare ai propri destinatari.

Google Gemini riceve esclusivamente il contenuto dell'immagine ai
fini dell'elaborazione OCR; **non riceve dati anagrafici dell'utente
né altri dati di profilo**. La risposta di Google Gemini viene
elaborata e salvata insieme alla spesa.

### 2.4 Dati tecnici
- Identificativo di sessione (cookie/token)
- Indirizzo IP (nei log applicativi del backend, conservazione
  massima 30 giorni)
- Informazioni sul dispositivo (sistema operativo, versione app)
- Contatori di utilizzo delle funzionalità AI/OCR (per il rispetto
  delle quote del piano)

### 2.5 Dati di abbonamento e pagamento
ExpensiLife **non gestisce direttamente** dati di pagamento (carte
di credito, conti bancari). Gli abbonamenti Pro vengono gestiti
tramite **RevenueCat**, **App Store** (Apple) e **Google Play**
(Google). ExpensiLife riceve esclusivamente:
- Identificativo dell'abbonamento e data di scadenza
- Esito della transazione (riuscita/fallita)

I dati della carta non transitano mai dai sistemi di ExpensiLife.

## 3. Finalità del trattamento

I dati personali vengono trattati per le seguenti finalità:

| Finalità | Base giuridica |
|---|---|
| Registrazione e gestione dell'account | Esecuzione del contratto (art. 6.1.b GDPR) |
| Erogazione delle funzionalità dell'app (gestione trasferte, spese, tragitti, OCR) | Esecuzione del contratto (art. 6.1.b GDPR) |
| Invio email di rendicontazione ai destinatari indicati dall'utente | Esecuzione del contratto + richiesta dell'utente (art. 6.1.b GDPR) |
| Gestione dell'abbonamento Pro | Esecuzione del contratto (art. 6.1.b GDPR) |
| Adempimenti fiscali e contabili | Obbligo di legge (art. 6.1.c GDPR) |
| Sicurezza dei sistemi e prevenzione frodi | Legittimo interesse del Titolare (art. 6.1.f GDPR) |
| Pubblicità all'interno dell'app per utenti Free (Google AdMob) | Legittimo interesse / consenso (a seconda della giurisdizione) |
| Statistiche aggregate sull'utilizzo dell'app | Legittimo interesse del Titolare (art. 6.1.f GDPR) |
| Notifica interna al Titolare delle nuove registrazioni (email automatica con dati di registrazione, esclusi password e segreti) | Legittimo interesse del Titolare per monitoraggio attività, sicurezza e prevenzione abusi (art. 6.1.f GDPR) |

### 3.1 Notifica automatica delle registrazioni al Titolare

Al momento della registrazione, il sistema invia un'email automatica
all'indirizzo `support@expensilife.org` (gestito dal Titolare) contenente:

- user_id, email, nome, valuta, data di nascita
- timestamp della registrazione, lingua dell'app
- stato Pro / scadenza abbonamento
- (se impostata) tariffa rimborso km

**Mai inviati**: password (in nessuna forma, neanche hashed), codici di
verifica email, codici di reset password, secret 2FA.

Finalità: monitoraggio dell'attività di registrazione per ragioni di
sicurezza, supporto clienti e prevenzione abusi (registrazioni di massa,
account fraudolenti, ecc.). Base giuridica: art. 6.1.f GDPR (legittimo
interesse del Titolare). L'email rimane nella casella di posta
`support@expensilife.org` per il tempo necessario alla finalità e
viene cancellata secondo le policy di conservazione email.

L'utente può richiedere la cancellazione di queste email contattando
il Titolare ai recapiti indicati al §13.

## 4. Modalità di trattamento e luogo di archiviazione

I dati sono trattati con strumenti elettronici, mediante
infrastrutture cloud di provider qualificati. Sono adottate misure
tecniche e organizzative atte a garantire la sicurezza del
trattamento, tra cui:

- **Password salvate solo come hash bcrypt** (non reversibili)
- **Connessioni TLS/HTTPS** per ogni comunicazione client/server
- **Cookie di sessione** marcati `httpOnly` + `secure` + `samesite=none`
- **Token di sessione** memorizzati sul dispositivo dell'utente in
  modo cifrato (`expo-secure-store`)
- **Chiavi API** dei servizi esterni mai esposte al client; solo il
  backend dialoga con Google, Brevo, MongoDB Atlas
- **Accesso controllato** ai dati personali da parte del solo Titolare

I server applicativi e di database sono ospitati presso fornitori
cloud (vedi sezione 5).

## 5. Soggetti a cui possono essere comunicati i dati (Responsabili
esterni del trattamento)

I dati possono essere trattati da terze parti che forniscono servizi
strumentali al funzionamento dell'app. Tali soggetti operano in
qualità di **Responsabili del trattamento ex art. 28 GDPR**. I
principali sono:

| Responsabile | Servizio fornito | Sede / Trasferimento dati |
|---|---|---|
| **MongoDB Atlas** (MongoDB Inc.) | Database gestito (utenti, trasferte, spese, sessioni) | UE/USA — adesione SCC + DPF |
| **Render** (Render Services Inc.) | Hosting del backend | USA — adesione SCC + DPF |
| **Google LLC — Gemini API** | OCR/AI per scansione ricevute | USA — adesione SCC + DPF |
| **Google LLC — Maps Platform** | Geocoding e calcolo distanze tragitti | USA — adesione SCC + DPF |
| **Google LLC — AdMob** | Visualizzazione pubblicità (utenti Free) | USA — adesione SCC + DPF |
| **Brevo** (Sendinblue SAS) | Invio email transazionali (rendiconti) | UE (Francia) |
| **RevenueCat** (RevenueCat Inc.) | Gestione abbonamenti in-app | USA — adesione SCC + DPF |
| **Apple Inc.** | App Store, in-app purchase iOS | USA |
| **Google LLC** | Google Play, in-app purchase Android | USA |

I trasferimenti di dati personali al di fuori dello Spazio Economico
Europeo verso fornitori statunitensi avvengono in conformità alle
**Standard Contractual Clauses (SCC)** approvate dalla Commissione
Europea e/o all'**EU-US Data Privacy Framework (DPF)** in vigore.

## 6. Periodo di conservazione

I dati personali sono conservati per il tempo strettamente necessario
al raggiungimento delle finalità per cui sono trattati:

- **Dati account e profilo**: per tutta la durata dell'utilizzo
  dell'app, e fino a 30 giorni dopo l'eliminazione dell'account
- **Trasferte e spese**: per tutta la durata dell'utilizzo dell'app;
  in caso di cancellazione account, vengono eliminate entro 30 giorni
- **Immagini delle ricevute**: come sopra (sono parte integrante del
  documento di spesa)
- **Log applicativi**: massimo 30 giorni
- **Dati di abbonamento**: 10 anni per obblighi fiscali/contabili,
  conformemente alla normativa italiana
- **Email transazionali (rendiconti)**: i log Brevo sono conservati
  da Brevo per il periodo previsto dai loro termini di servizio

## 7. Cookie e tecnologie simili

L'App utilizza:

- **Cookie tecnici di sessione** (necessari, non bloccabili) per
  mantenere l'utente autenticato
- **`expo-secure-store`** per salvare il token di sessione sul
  dispositivo
- **AsyncStorage** per preferenze locali (lingua scelta)
- **AdMob** può utilizzare identificativi pubblicitari del
  dispositivo per il targeting (utenti Free); l'utente può
  disabilitare gli annunci personalizzati dalle impostazioni di
  Android/iOS

Non vengono utilizzati cookie di profilazione di terze parti per
finalità diverse da quelle qui descritte.

## 8. Pubblicità (utenti Free)

Gli utenti del piano gratuito visualizzano pubblicità interstitial
(a schermo intero) fornite da **Google AdMob** in occasione di:

- Creazione di una nuova trasferta
- Invio dell'email di rendicontazione

I dati eventualmente trattati da Google AdMob sono soggetti
all'informativa privacy di Google. Sottoscrivendo il piano Pro,
l'utente non visualizza più alcuna pubblicità.

## 9. Diritti dell'interessato

In qualunque momento l'utente può esercitare i seguenti diritti
ex artt. 15-22 GDPR:

- **Diritto di accesso** (art. 15): sapere quali dati personali sono
  trattati e ottenerne copia
- **Diritto di rettifica** (art. 16): correggere dati inesatti
- **Diritto alla cancellazione** (art. 17, "diritto all'oblio")
- **Diritto di limitazione del trattamento** (art. 18)
- **Diritto alla portabilità dei dati** (art. 20): ricevere i dati
  in formato strutturato e leggibile da macchina
- **Diritto di opposizione** (art. 21)

L'app mette a disposizione strumenti dedicati nella sezione
"Profilo → Account e sicurezza":

- **Scarica i tuoi dati** (export JSON di tutti i dati personali)
- **Elimina account** (cancellazione definitiva dei dati)

In alternativa, le richieste possono essere inviate via email a
**lolicatoalberto@gmail.com**.

L'utente ha inoltre il diritto di proporre **reclamo al Garante per
la protezione dei dati personali** (https://www.garanteprivacy.it).

## 10. Sicurezza

Adottiamo misure tecniche e organizzative idonee a garantire un
livello di sicurezza adeguato al rischio, tra cui:

- Cifratura HTTPS/TLS per tutte le comunicazioni
- Hash bcrypt per le password (nessuna password in chiaro)
- Token di sessione monouso conservati in storage cifrato
- Backup periodici del database
- Limitazione degli accessi al backend ai soli responsabili tecnici
- Monitoraggio di sicurezza e log di audit

In caso di **data breach** che possa comportare un rischio per i
diritti degli utenti, il Titolare provvederà alla notifica al
Garante e agli interessati nei termini previsti dall'art. 33 e 34
GDPR (entro 72 ore).

## 11. Minori

ExpensiLife non è destinato a minori di **16 anni**. Non
raccogliamo consapevolmente dati personali di minori di tale età.
Se venissimo a conoscenza di aver raccolto dati di un minore senza
adeguato consenso, provvederemo a cancellarli immediatamente.

## 12. Modifiche all'informativa

La presente informativa può essere aggiornata. La versione più
recente sarà sempre disponibile in app e sul repository pubblico.
In caso di modifiche sostanziali, l'utente sarà avvisato all'avvio
dell'app o via email.

## 13. Contatti

Per qualsiasi domanda relativa al trattamento dei tuoi dati
personali:

- **Email:** lolicatoalberto@gmail.com
- **Titolare:** Alberto Lolicato, Ariccia (RM), Italia
- **Codice Fiscale:** LLCLRT92R20C351C
