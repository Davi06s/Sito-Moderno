# Cronologia Modifiche (Changelog)

Questo file traccia la cronologia delle modifiche apportate al progetto, indicando cosa è stato cambiato e il motivo (Perché).

---

## 10 Marzo 2026 - Fase 0: Sviluppo Iniziale Layout HTML Base

### 🚀 Aggiunte
- **Creazione index.html**: Sviluppata la struttura HTML5 base del progetto.
- **Integrazione Asset Esterni**:
  - Fonts (Google Fonts: Source Sans Pro, Pacifico, Oswald).
  - Collegamenti ai fogli di stile originali (`style.css`, `default.css`, `nivo-slider.css`).
  - Integrazione di jQuery e attivazione script Nivo Slider nell' `<head>`.
- **Sviluppo Layout Strutturale (da mockup PDF)**:
  - Header, Navbar, Slider.
  - Sezione `item-evi` (3 colonne).
  - Footer, Sidebar e area Content (per gli articoli).

### 🤔 Perché
- Questa era la primissima fase (Esercizio 3) richiesta per dimostrare l'uso del markup semantico di base, dei selettori CSS e delle tecniche storiche (come i `float`) per strutturare un prototipo funzionante a partire da una reference statica.

---

### 🚀 Aggiunte
- **Integrazione Tailwind CSS**: Inserito lo script CDN di Tailwind nell' `<head>` di `index.html`.
- **Configurazione Tema**: Esteso il tema base di Tailwind per includere i colori originali (`primary: '#21aabd'`) e i font (`Source Sans Pro`, `Pacifico`, `Oswald`).

### 🔄 Modifiche
- **Sostituzione del Layout basato su `float`**: Rimosse tutte le dipendenze da `float: left` e dai div `<div class="clear"></div>`.
- **Integrazione di Flexbox e CSS Grid**: 
  - Applicato `grid-cols-3` per la sezione "Evidenza".
  - Applicato `grid-cols-12` per gestire Content (8/12) e Sidebar (4/12).
- **Tipografia**: Sostituiti i tag CSS standard con le classi di Tailwind (`text-gray-600`, `leading-relaxed`, `font-heading`, `font-nav`).

### 🤔 Perché
- I layout basati su `float` sono ormai considerati obsoleti e difficili da mantenere per siti web reattivi (responsive). 
- Tailwind CSS permette di sviluppare interfacce moderne e responsive in modo molto più veloce direttamente nell'HTML, riducendo la proliferazione di classi nel file `style.css` e standardizzando i valori di spaziatura e tipografia.

---

## 12 Marzo 2026 - Fase 2: Raffinamento Design e "Modernizzazione" (UI/UX)

### 🚀 Aggiunte
- **Effetto Glassmorphism nella Navigation**: Applicate classi come `backdrop-blur-md` e `bg-secondary/95` alla barra di navigazione sticky.
- **Sezione di Ricerca nella Sidebar**: Aggiunto un modulo di ricerca simulato per arricchire la sidebar.
- **Micro-animazioni Avanzate**: Aggiunti effetti fluidi al passaggio del mouse (`hover:scale-110`, `transition-transform`) sulle icone e sulle immagini degli articoli.
- **Footer Avanzato**: Sostituito il semplice footer di copyright con un layout a griglia multipiano (Chi Siamo, Link Rapidi, Copyright).

### 🔄 Modifiche
- **Banner del Messaggio (`Mes-full`)**: Aggiornato da uno sfondo grigio pastello a un vibrante gradiente orizzontale (`bg-gradient-to-r from-primary to-primaryDark`) con testo bianco.

### 🤔 Perché
- **Glassmorphism**: Aggiunge un tocco estetico contemporaneo e "Premium"; permette all'utente di non perdere la concezione dello spazio quando scorre la pagina tenendo la navigazione fissa in alto.
- **Banner Messaggio**: Se un messaggio deve essere "importante" come recitava il testo originale, un background grigio non era sufficiente. Il gradiente brandizzato lo fa risaltare enormemente.
- **Footer e Sidebar**: Elementi come questi danno subito l'impressione che il sito non sia solo un esercizio, ma una vera e propria landing page professionale e pronta all'uso. Le animazioni migliorano l'engagement.

---

## 12 Marzo 2026 - Fase 3: Layout Ultra-Moderno e Sfruttamento Totale Larghezza (Full-Width)

### 🚀 Aggiunte
- **Pannello Scorrimento Decorativo Globale**: Aggiunti gradienti radiali sfuocati (`blur-[120px]`) e pattern di sfondo (griglia in SVG) fissati allo sfondo per un'impressione premium e hi-tech.
- **Tipografia Brutalista/Editoriale**: Inserite due nuove font-family dal forte contrasto estetico moderno: `Outfit` (sans-serif geometrico e pulito) e `Playfair Display` (serif elegante, spesso usato in corsivo per keyword specifiche).
- **Nuova Navigazione "Flottante"**: La navbar è diventata un overlay flottante centrale a "pillola" staccato dai bordi, ultra-glassmorphic.
- **Anchor Links Scroll (Smooth Scroll)**: I bottoni della navigazione (Chi Siamo, Servizi, Contatti) ora puntano dinamicamente alle macro-sezioni chiave (Punti in evidenza, Ultimi articoli, Footer) con scorrimento fluido (`html class="scroll-smooth"`).

### 🔄 Modifiche
- **Abbandono del Container Chiuso**: Rimosso il box contenimento massimo (`max-w-6xl` e `mx-auto`) sul `<body>`. Tutte le sezioni ora operano al 100% della larghezza dello schermo (`w-full`), creando fasce orizzontali ininterrotte.
- **Hero Screen Immersivo (Slider Nivo Modificato)**: L'intestazione è stata fusa con lo Slider. L'Hero copre ora il 90% dell'altezza della finestra (`min-h-[90vh]`) con lo slider declassato a sfondo dinamico (`mix-blend-luminosity` e opacity ridotta). Addio frecce Nivo, solo punti di controllo re-stilizzati con i CSS nativi via tag `<style>`.
- **Restyling Massiccio Box e Footer**:
  - Gli articoli occupano il design con immagini mastodontiche laterali ad angoli strombati (`rounded-[3rem]`).
  - Il footer è ora molto profondo (Massive Footer) riempito di link strutturali fittizi ed integrato con **loghi social vettoriali (SVG reali)** per Facebook e LinkedIn, animati con i rispettivi colori brand on-hover (`#1877F2` e `#0A66C2`). A tali icone sono stati inoltre applicati i link diretti alle rispettive piattaforme social (`https://www.facebook.com/` e `https://www.linkedin.com/`).
  - La sidebar è arricchita con uno spazio "Dashboard Autore" super personalizzato.

### 🤔 Perché
- La richiesta era un utilizzo **totale** dello spazio di pagina assieme ad un approccio **ultra moderno**. Un layout "boxed" (scatola bianca in mezzo ad uno schermo grigio) non è in grado di veicolare questa impressione: i migliori siti SaaS e le landing page Premium Web3 o Agency del momento (Awwwards) usano enormi testi tipografici incrociati (serif vs sans-serif bold), pattern fluidi in background con bagliori esposti, elementi UI rotondati in forma "a pillola" e un flow orizzontale ininterrotto (section stacking a tutto schermo). Questo aggiornamento chiude il divario fra "esercizio formativo base" e "prototipo all'avanguardia".

---

## 16 Marzo 2026 - Fase 4: Documentazione del Progetto

### 🚀 Aggiunte
- **Creazione README.md**: Aggiunto un file introduttivo per spiegare la struttura del progetto, la differenza tra la versione originale e il restyling.
- **Creazione DOCUMENTAZIONE-TECNICA.md**: Redatto un documento tecnico dettagliato sulle scelte architetturali, l'uso di Tailwind CSS, il design system e l'integrazione legacy del Nivo Slider.

### 🤔 Perché
- Un progetto ben documentato è essenziale per la manutenibilità e per permettere di comprendere rapidamente le scelte strategiche ed estetiche effettuate nel rifacimento del layout.
