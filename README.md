# Integrazione INAD - Agenzia Riscossione

## Esigenza

Risulta necessario individuare una modalità di scambio basato su API REST esposte tramite PDND Interoperabilità per dare seguito all'individuazione dei domicili digitali (di seguito DD) a partire dai CF (persona fisica e/o persona giuridica).


## Contesto

I seguenti soggetti possono eleggere un DD in INAD:

1. le persone fisiche che abbiano compiuto il diciottesimo anno di età e che
abbiano la capacità di agire;
2.  i professionisti che svolgono una professione non organizzata in ordini, albi
o collegi ai sensi della legge n. 4/2013;
3. gli enti di diritto privato non tenuti all’iscrizione nell’INI-PEC.

Ne consegue che:

- dato un CF di una persona fisica INAD restituisce un elenco di DD specificando, per i DD eletti dai soggetti di cui al precedente punto 2, la professione per cui lo stesso è stato eletto (in caso di professione non presente si assume che il DD è eletto nel ruolo di cittadino, precedente punto 1);
- dato un CF di una persona giudica INAD restituisce al più un DD per la stessa.

## Soluzione

Nel presente repository è definita la soluzione individuata.

Nello specifico sono riportati:

- [sequence diagram](sequence-diagram.md) del flow implementato da INAD e Agenzia Riscossione;
- il [formato della lista di CF](listCF.json) predisposto da Agenzia Riscossione di cui di richiedono i DD;
- il [formato della lista di CF con i relativi DD](listDD.json) predisposto da INAD in rispota ad una richiesta dell'Agenzia Riscossione;
- l'[OpenAPI implementato dall'Agenzia Riscossione](openapiAR.yaml);
- l'[OpenAPI implementato dall'INAD](openapiINAD.yaml).

Si assume che per il recupero: 

- della lista di CF predisposto da Agenzia Riscossione da parte di INAD, Agenzia Riscossione implementa [Range Requests](https://www.rfc-editor.org/rfc/rfc9110#name-range-requests) e [Conditional Requests](https://www.rfc-editor.org/rfc/rfc9110#name-conditional-requests);
- della lista di CF con i relativi DD predisposto da INAD da parte di Agenzia Riscossione, INAD implementa [Range Requests](https://www.rfc-editor.org/rfc/rfc9110#name-range-requests) e [Conditional Requests](https://www.rfc-editor.org/rfc/rfc9110#name-conditional-requests).