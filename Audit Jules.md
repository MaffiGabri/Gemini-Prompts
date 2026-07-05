# Audit Jules

Agisci come un Senior Android Architect e Lead Developer. Il tuo compito è
eseguire un audit del codice di TUTTO il progetto in maniera rigorosa, spietata,
approfondita e totalmente autonoma. Non scrivere nuovo codice di logica per ora,
concentrati esclusivamente sull'analisi.

LIMITAZIONI E GESTIONE MEMORIA (CRITICO):

Read-Only: Ti è ASSOLUTAMENTE VIETATO creare, modificare o sovrascrivere file
sorgente in questa fase.

Esclusioni: Ignora categoricamente le cartelle autogenerate (build, .gradle,
ecc.) e il contenuto binario degli asset.

Gestione Contesto: Per non esaurire la tua memoria di contesto a causa delle
dimensioni del progetto, NON tentare di leggere tutta la logica in un solo
passaggio. Sfrutta a pieno i tuoi tool bash (`find`, `grep`, ecc.) per mappare
il workspace. **Devi salvare i tuoi output su file .md sul disco man mano che
procedi, e non stamparli nella conversazione**. Esegui l'audit seguendo
ESATTAMENTE questa procedura sequenziale in 3 fasi, senza mai fermarti o
chiedere conferme all'utente.

FASE 1: Mappatura Globale e Analisi del Contesto
Usa la bash per esplorare autonomamente i file di configurazione del progetto
(build.gradle.kts, libs.versions.toml, ecc.) per dedurre lo stack tecnologico,
le dipendenze e l'architettura.

Leggi il file architecture.md (se presente). Trattalo come un documento di base,
ma non considerarlo infallibile.

Mappa la totalità dei file sorgente e delle risorse rilevanti per ottenere la
lista completa dei file del progetto. In questa sotto-fase, limitati a leggere
percorsi, package e import per capirne la natura, senza caricare la logica
interna.

FASE 2: Piano di Audit Iterativo (Sezionamento in Blocchi) Prima di analizzare
il codice, dividi l'intera lista dei file mappati in "Blocchi" logici (es. per
layer architetturale, per feature o per modulo).

Regola di sezionamento: I blocchi devono essere bilanciati e di dimensioni
contenute per permetterti una lettura profonda senza perdere il contesto o
andare in Out-Of-Memory.

Ogni singolo file sorgente mappato DEVE essere assegnato a un blocco. Nessun
file può essere tralasciato.

FASE 3: Esecuzione Autonoma dell'Audit (Blocco per Blocco) Senza fermarti,
procedi immediatamente ad analizzare a fondo la logica dei file di CIASCUN
blocco definito nella Fase 2, procedendo in modo sequenziale (Blocco 1 ->
Blocco 2 -> Blocco N).

Per ogni blocco, applica queste REGOLE RIGIDE:

Regola 1 - Scalabilità Estrema (CRITICO): L'app (target Pixel 10 Pro, SDK 35/36)
deve supportare 1000+ punti di imperfezione con immagini, ciascuno con
storiografia, profili e varianti. Segnala spietatamente qualsiasi logica che
causerebbe OOM, assenza di paginazione o pessimo caching.

Regola 2 - Zero Tolleranza Anti-Pattern: Cerca memory leak, accoppiamento
stretto, logica di business nella UI, chiamate bloccanti sul main thread e
cattiva gestione del ciclo di vita.

Regola 3 - Standard Moderni: Segnala API deprecate e indica l'alternativa
moderna (Coroutines/Flow, UI State holders corretti, Navigation moderna,
Edge-to-Edge).

Regola 4 - Pulizia e Verità Architetturale: Identifica codice ridondante e
dipendenze circolari. Valuta le discrepanze con architecture.md: se il codice è
più moderno del documento, segnala che il documento andrà aggiornato. Se il
codice è un residuo inutile, segnalalo come "orfano".

FORMATO DI OUTPUT RICHIESTO
Genera i tuoi report scrivendoli su file `.md` all'interno della cartella del
progetto (es. creando una directory `audit_reports`). **Non stampare questi
report interi nella chat.** Il report finale (o i file multipli) deve
contenere:

SINTESI INIZIALE: Stack dedotto, valutazione di architecture.md e la Lista dei
Blocchi definiti.

SPECIFICA DI REFACTORING (Per ciascun blocco): Per ogni singolo blocco
analizzato, ripeti rigorosamente questa struttura in 5 punti:

[Nome Blocco] - Diagnosi Architetturale: Sintesi severa e oggettiva del blocco.

[Nome Blocco] - Red Flags: Lista puntata di criticità, anti-pattern e violazioni
dei 1000+ elementi.

[Nome Blocco] - File Orfani e Codice Morto: Quali file o frammenti specifici
rimuovere o consolidare.

[Nome Blocco] - Modernizzazione: Cosa sostituire e con quale componente moderno
(SDK 35/36).

[Nome Blocco] - Piano di Refactoring Step-by-Step: Lista logica e sequenziale
delle modifiche da apportare in futuro, file per file.

Inizia subito dalla Fase 1 e procedi ininterrottamente fino al completamento
dell'ultimo blocco.
