# Documentazione Tecnica - Sito Moderno (Esercizio 3)

Questo documento fornisce una panoramica tecnica dettagliata sulle scelte di design e sull'architettura implementate nel restyling della versione presente nella cartella `03-sito-moderno`.

## 1. Architettura CSS e Styling

### 1.1 Tailwind CSS via CDN
Il restyling abbandona il foglio di stile custom originale in favore dell'approccio *utility-first* fornito da **Tailwind CSS**, integrato tramite script CDN. Questa scelta permette:
- **Rapid Prototyping:** Creazione di componenti complessi per l'interfaccia utente direttamente nel markup HTML.
- **Zero Config Build (in sviluppo):** Impostazione rapida delle direttive nell'oggetto `tailwind.config` all'interno dello `<script>` nella `<head>`. L'oggetto script personalizza in modo granulare i colori, i font e le estensioni tipografiche o d'ombra.

### 1.2 Tema e Design System (Configurazione Tailwind)
Nel file `index.html`, il file di configurazione di Tailwind definisce precise scelte stilistiche:
- **Color Palette:**
  - `primary` (#0ea5e9 - cyan/blue): Utilizzato per accenti brillanti, effetti hover e call-to-action (CTA) principali.
  - `primaryDark` (#0284c7): A supporto di `primary` per realizzare sfumature e gradienti vividi.
  - `secondary` (#0f172a - slate ultra dark): Colore principale per il footer, sfondi di sezioni in risalto e testi di forte peso visivo su fondo chiaro.
  - `surface` e `surfaceAlt`: Palette neutre (#ffffff e #f8fafc) utilizzate per sfondi distensivi e la naturale separazione dei contenuti.
  - `accent` (#f43f5e - rose): Colore d'accento introdotto strategicamente per richiamare attenzione e ravvivare l'interazione.
- **Box Shadows e Blur:** Definizione di proprietà come `neon` e `float` per simulare profondità, morbidezza delle interfacce ed effetto *Glassmorphism*.
- **Tipografia Dual-Font:** Combina l'utilizzo del font *Outfit* (sans, geometrico, pulito) per i paragrafi e *Playfair Display* (serif, elegante, "heading") per generare forte e netto contrasto visivo nei testi dedicati ai titoli.

## 2. Layout e Paradigmi di Struttura

Il sito è costruito come una singola landing page *Full-width*, sfruttando con efficacia le utility class grid e flex di Tailwind.

### 2.1 Navigazione "Glassmorphism"
La barra di navigazione (`<nav>`) abbandona il classico layout a contenitore chiuso a ridosso dell'header, e diventa "floating":
- Posizionata tramite l'utility `fixed` e centrata sull'asse orizzontale.
- Utilizza `backdrop-blur-xl` accoppiato a sfondi ultra-trasparenti (es: `bg-secondary/70`) per simulare un notevole effetto vetro satinato a forte impatto (*Glassmorphism*).

### 2.2 CSS Grid e Layout Editoriale Multicolonna
La sezione "Esplora", pensata per listare articoli e formare la graticola principale (id `#explore`), sfrutta **CSS Grid** con uno schema robusto a 12 colonne (`grid-cols-12` da breakpoint ampi in poi), ricalcando il layout editoriale:
- All'area dedicata al contenuto principale (articoli centrali) vengono assegnate 8 colonne (`col-span-8`).
- Alla Sidebar o "dashboard" laterale vengono assegnate 4 colonne (`col-span-4`).
- Questa tecnica permette di gestire proporzioni, white space e adattabilità di breakpoint su tablet, trasformandosi in una naturale e leggibile impilazione verticale (singola colonna) sui dispositivi mobile (`md` in giù).

## 3. UX, Animazioni ed Esperienza Utente

- **Stati Hover & Group-Hover:** Le singole interfacce a card o articoli listati sfruttano l'accoppiamento di classi introdotte in un div contenitore (es. classe `group`) e intercettate negli elementi figlio via modifier (`group-hover:scale-110` / `group-hover:translate-x-3`). Risulta una tecnica vitale e molto accattivante per le micro-animazioni di elementi interni quali la spinta laterale dell'icona (arrow), l'espansione del container d'ombra o la dolce zoomata delle immagini al passaggio in focus o hover puntatore.
- **Fondi Astratti e Pattern Dinamici:** Introdotte classi helper (sotto background config) come `bg-grid-pattern` (una stringa SVG convertita) e `div` decorativi circolari colorati, mitigati con un notevole `blur-[120px]`. Fissati poi nello `z-index: -10` (negativo) del documento per conferire uno spessore e un gradevole pattern globale distensivo dietro ai testi normali.

## 4. Integrazione Legacy del Nivo Slider / JavaScript

Uno degli obiettivi integrativi era mantenere l'utilizzo originale del plugin **Nivo Slider** pur all'interno di un layout alterato radicalmente.
- **Sovrascrittura CSS in linea e Reset:** Tailwind ha rigide policy di base css per il proprio reset che avrebbero azzerato interfacce di codice di terze parti meno recenti, originariamente assenti nel border-box model (come il nivoSlider che usa vecchi posizionamenti boxati dell'epoca `1.7.x` di jQuery). Lo stile del plugin è stato domato tramite uno script aggiuntivo `<style>` nella tag `<head>` forzando il ridimensionamento (nessun box-shadows, arrotondamento e ri-stilizzazione del control navigation).
- **Impianto Fading JS Originale:** Il plugin viene caricato e inizializzato come da origine con la libreria jQuery legacy. É stato però implementato e circondato all'interno di utility Tailwind come `mix-blend-luminosity` e *gradient overlays*, alterandone l'output visivo integrandosi elegantemente sullo sfondo senza ostacolare l'originale *engine JS* del nivo slider durante le fasi di fade/fading nativo tra un background e l'altro nell'header hero.
