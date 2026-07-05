# Audit Antigravity

Agisci come un Senior Android Architect e Lead Developer. Il tuo compito è
eseguire un audit del codice di TUTTO il progetto, rigoroso, spietato e
approfondito dei file e delle logiche. Non scrivere nuovo codice per ora,
concentrati esclusivamente sull'analisi.

LIMITAZIONI (CRITICO):

Ti è ASSOLUTAMENTE VIETATO creare, modificare o sovrascrivere file in questa
fase.

Ignora categoricamente le cartelle autogenerate e il contenuto binario degli
asset.

Per non esaurire la tua memoria di contesto a causa delle dimensioni del
progetto, NON tentare di leggere tutto il codice in un solo passaggio. Sfrutta
la tua intelligenza e i tuoi tool per esplorare il workspace seguendo
ESATTAMENTE questa procedura iterativa:

***Fase 1: Mappatura Globale e Analisi del Contesto***

- Esplora autonomamente i file di configurazione del progetto per dedurre lo
  stack tecnologico, le dipendenze e l'architettura.

- Leggi il file architecture.md. Trattalo come un documento di base, ma non
  considerarlo infallibile.

- Mappa la totalità dei file sorgente e delle risorse rilevanti. Usa i tuoi tool
  nel modo più efficiente per ottenere la lista completa di tutti i file del
  progetto, ma NON leggere la logica interna per ora. Puoi sbirciare gli import
  o i package per capirne la natura,

***Fase 2: Report Preliminare e Sezionamento in Blocchi***

Genera un report preliminare salvandolo come nuovo Artifact contenente:

- Una breve sintesi dello Stack e dell'Architettura che hai dedotto.

- Piano di Audit Iterativo (Cruciale): Dividi l'intera lista dei file mappati in
  "Blocchi" logici (es. per layer architetturale, per feature o per modulo).
  Regola di sezionamento: I blocchi devono essere bilanciati e di dimensioni
  contenute per permetterti una lettura profonda senza perdere il contesto. Ogni
  singolo file sorgente mappato DEVE essere assegnato a un blocco. Nessun file
  può essere tralasciato. Se il progetto è troppo vasto, suddividilo prima per
  Moduli/Feature, e poi dettaglia i file solo per il primo Modulo.

***Fase 3: Regole e Output per l'Audit (Da applicare blocco per blocco)***

FERMATI alla fine della Fase 2 e chiedimi ESPLICITAMENTE l'autorizzazione per
procedere con il Blocco 1. Non analizzare mai il blocco successivo senza il mio
permesso esplicito, in modo da non saturare il tuo contesto conversazionale.

Quando ti autorizzerò ad analizzare un blocco specifico, dovrai leggerne a fondo
i file tramite i tuoi tool e generare un nuovo artifact "Specifica di
Refactoring" per quel blocco, applicando queste REGOLE RIGIDE:

Regola 1 - Scalabilità Estrema (CRITICO): L'app deve supportare oltre 1000+
punti di imperfezione, ciascuno con immagini e storiografia su ogni sfondo
diverso (chiamato variante), e possibilità di avere più profili, con ognuno un
set definito di varianti. Segnala spietatamente qualsiasi cosa causerebbe OOM,
l'assenza di paginazione o un pessimo caching.

Regola 2 - Zero Tolleranza Anti-Pattern: Cerca memory leak, accoppiamento
stretto, logica di business nella UI, chiamate bloccanti sul main thread e
cattiva gestione del ciclo di vita.

Regola 3 - Standard Moderni: Segnala API deprecate e indica l'alternativa
moderna (Coroutines/Flow, UI State holders corretti, Navigation moderna,
Edge-to-Edge).

Regola 4 - Pulizia e Verità Architetturale: Identifica codice ridondante e
dipendenze circolari. Valuta le discrepanze con architecture.md: se il codice è
più moderno o corretto del documento, segnala che il documento andrà aggiornato.
Se il codice è un residuo inutile, segnalalo come "orfano".

Il Documento artifact di Specifica per ogni blocco dovrà avere ESATTAMENTE
questo formato Markdown:

1. Diagnosi Architetturale: Sintesi severa e oggettiva del blocco.

2. Red Flags: Lista puntata di criticità e anti-pattern.

3. File Orfani e Codice Morto: Quali file/frammenti rimuovere o consolidare.

4. Modernizzazione: Cosa sostituire e con quale componente moderno.

5. Piano di Refactoring Step-by-Step: Lista logica e sequenziale delle
   modifiche da apportare, file per file.

/goal Esegui la Fase 1, poi la Fase 2, e infine **FERMATI**. Attendi la mia
autorizzazione esplicita prima di avviare l'analisi del primo blocco nella
Fase 3.
