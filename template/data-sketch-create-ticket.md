# Data Sketch - Create Ticket

## Prima Di Compilare

Un data sketch e' una classificazione dei campi prima dello schema definitivo.

Serve a decidere quali dati sono accettati, generati, respinti o ancora mancanti.

Il Mermaid finale visualizza solo campi e relazioni gia' motivati nella tabella.

Non usare questo file per progettare tutto il database o accettare campi non collegati a issue e contract.

## Come Scegliere Lo Stato Del Campo

| Stato | Usalo quando | Domanda di controllo |
| --- | --- | --- |
| accettato | il campo arriva dall'input e serve al primo slice | chi lo inserisce? |
| generato | il sistema crea il valore | quando viene creato? |
| respinto | il campo e' fuori scope o non motivato | quale vincolo lo esclude? |
| mancante | il campo potrebbe servire, ma manca una decisione | chi deve chiarirlo? |

Se non sai motivare un campo, non metterlo nel Mermaid: lascialo `mancante` o `respinto`.

## Scopo

Classificare i dati prima di chiedere codice.

## Campi

| Campo | Stato | Motivo | Fonte |
| --- | --- | --- | --- |
| `title` | accettato | senza titolo, il ticket non ha valore | issue / contract / decisione / inferenza |
| `description` | accettato | informazioni aggiuntive per approfondire il campo "title" | issue / contract / decisione / inferenza |
| `priority` | mancante | non abbiamo deciso chi assegna la priortià | issue / contract / decisione / inferenza |
| `area` | respinto | è fuori scope | issue / contract / decisione / inferenza |
| `status` | respinto | è fuori scope | issue / contract / decisione / inferenza |
| `id` | generato | viene creato quando serve la persistenza nel DB | issue / contract / decisione / inferenza |
| `attachments` | respinto | è fuori scope | issue / contract / decisione / inferenza |
| `owner` | generato | campo prelevato in automatico | issue / contract / decisione / inferenza |
| `createdAt` | generato | campo creato in automatico, definisce quanto è recente | issue / contract / decisione / inferenza |

## Mermaid Leggero

Usa Mermaid solo per visualizzare la relazione minima. Non trasformarlo in schema DB definitivo.

```mermaid
erDiagram
    TICKET {
        title string "accettato" 
        description string "accettato"
 
    }

```

Campi mostrati nel diagramma:

- title - accettato
- description - accettato
- priority - mancante
- area - mancante
- status - respinto
- id - generato
- attachments - respinto
- owner - generato
- createdAt - generato

## Campi Scartati O Rimandati

| Campo | Decisione | Motivo |
| --- | --- | --- |
| attachments | respinto | fuori scope |
| priority | rimandato | non è specificato, si rischia di andare fuori scope |

## Domande Per L07

- [quale file potrebbe contenere questi dati?]
- [quale naming andra' verificato nella repo?]
- [quale campo dipende da una decisione non presa?]
