# Performance Audit

Agisci come Performance Engineer. Rivedi tutto il lavoro di audit che hai
appena completato e i documenti generati, applicando una nuova lente di lettura:
il focus ossessivo sulle prestazioni. **(Se sei Jules, usa la bash per leggere
tutti i file di audit salvati su disco; se sei Antigravity, chiedi i file
all'utente)**.

Cerca colli di bottiglia nel database, renderizzazioni inutili in Compose,
memory leak sottili e cattiva gestione della cache. Genera un nuovo Artifact
chiamato Performance_RedFlags.md in cui evidenzi unicamente le criticità che
potrebbero causare lag o battery drain, suggerendo le ottimizzazioni più estreme
necessarie per i requisiti critici.

Poi crea un nuovo e ultimo Artifact chiamato Master_Audit_Performance.md. **(Se
sei Jules, salva questi artefatti direttamente sul file system; se sei
Antigravity, forniscili in chat all'utente, magari suddivisi in messaggi se
troppo lunghi)**. Non fare un semplice copia-incolla dei report precedenti.
Voglio che tu li sintetizzi e li consolidati in un unico documento di livello
Architetturale Globale, ma non tralasciare info importanti.

Struttura il Master Report così:

- Executive Summary: Lo stato di salute generale dell'app rispetto ai requisiti
  critici.
- Top 5 Red Flags Globali: Le 5 criticità più gravi in assoluto trovate in
  tutto il progetto.
- Piano di Modernizzazione Globale: Cosa stiamo cambiando a livello macro.
- Roadmap di Refactoring Definitiva: Unisci i piani step-by-step dei singoli
  blocchi in un'unica sequenza temporale logica (es. Fase 1: [Istruzioni
  dettagliate], Fase 2: [Istruzioni dettagliate], ecc.).
