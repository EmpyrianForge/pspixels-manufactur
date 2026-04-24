# Vue Landingpage Brief für Claude Code

## Projektziel
Erstelle eine hochwertige, conversion-orientierte Landingpage in **Vue.js** (vorerst nur Frontend) für ein Premium-Produkt, das aus **echtem Holz** und **3D-gedruckten Bestandteilen** besteht. Die Seite soll ein Gefühl von **Natürlichkeit, Präzision, Handwerk, Materialehrlichkeit und modernem Luxus** vermitteln.

Die Zielgruppe sind:
- **B2B-Kunden**: Architekturbüros, Interior-Studios, Boutique-Hotels, hochwertige Offices, Showrooms, Designhändler
- **Wohlhabendere Endkunden / Premium-Käufer**: designaffine Menschen mit Fokus auf Qualität, Nachhaltigkeit und Exklusivität

Die Seite soll nicht wie ein generisches Startup-Template wirken. Kein typischer SaaS-Look, keine Tech-Gradient-Orbs, keine verspielten bunten Cards. Stattdessen: **ruhig, hochwertig, editorial, materialbetont und vertrauenswürdig**.

---

## Designrichtung

### Markenwirkung
Die Seite soll diese Eigenschaften transportieren:
- natürlich
- biologisch / organisch
- hochwertig
- präzise gefertigt
- nachhaltig
- exklusiv
- modern, aber nicht futuristisch-kalt
- warm und taktil

### Stilbild
Denke an eine Mischung aus:
- Premium-Interior-Brand
- Boutique-Möbelmarke
- Architektur-/Materialästhetik
- moderner Produktinszenierung mit editorialem Charakter

Die Wirkung soll eher sein:
- **weniger Massenmarkt**
- **mehr Designobjekt / Sammlerstück / Premium-Manufaktur**

---

## Ziel der Landingpage
Die Landingpage soll:
1. das Produkt emotional hochwertig inszenieren
2. die Materialkombination aus **echtem Holz + 3D-Druck** überzeugend erklären
3. Vertrauen aufbauen
4. den Wert und Premium-Preis rechtfertigen
5. B2B-Anfragen und hochwertige Leads generieren

### Primäre CTAs
- „Projekt anfragen“
- „Beratung anfordern“
- „Katalog anfragen“

### Sekundäre CTAs
- „Materialien entdecken“
- „Fertigung verstehen“
- „Referenzen ansehen“

---

## Technischer Rahmen

### Stack
- **Vue.js**
- vorerst **nur Frontend**
- gern als saubere Component-Struktur aufbauen
- keine unnötig schwere Abhängigkeiten
- Fokus auf gute Lesbarkeit, Erweiterbarkeit und saubere Sections

### Gewünschte Struktur
Bitte erstelle:
- eine Haupt-Landingpage
- wiederverwendbare Vue-Komponenten für Sections
- saubere Datenstruktur für Inhalte, falls sinnvoll
- semantisches HTML
- responsive Umsetzung
- Dark Mode optional, aber Light Mode ist Priorität

Wenn möglich, nutze:
- `App.vue`
- Komponenten wie `HeroSection.vue`, `MaterialsSection.vue`, `ProcessSection.vue`, `AudienceSection.vue`, `ReferencesSection.vue`, `CTASection.vue`, `FooterSection.vue`

---

## Visuelle Richtung

### Farbwelt
Die Farbpalette soll **natürlich, biologisch, organisch und edel** wirken.

#### Bevorzugte Farbfamilien
- warmes Off-White
- Sand / Leinen / Bone
- helles Holzbeige
- gedecktes Moosgrün oder Salbeigrün
- dunkles Oliv / Waldgrün als Akzent
- warme Braun-/Walnusstöne
- Graphit / Anthrazit für Typografie

#### Vermeiden
- Neonfarben
- knalliges Blau
- typisches SaaS-Lila
- kalte Cyber-Farben
- harte Tech-Verläufe
- zu viele Akzentfarben gleichzeitig

### Beispielhafte Design Tokens
```css
:root {
  --bg: #f6f1e8;
  --surface: #efe7db;
  --surface-2: #e4d8c6;
  --text: #2b241f;
  --text-muted: #6e6258;
  --line: #d3c6b6;
  --primary: #4d6b4a;
  --primary-hover: #3d563b;
  --accent-wood: #8a6448;
  --accent-dark: #1f1c19;
}
```

Bitte diese Werte nicht blind übernehmen, sondern als Richtung verstehen.

---

## Typografie
Die Typografie soll Luxus und Ruhe transportieren.

### Empfehlung
- **Display-Font** für Headlines: elegant, editorial, hochwertig
- **Body-Font**: modern, sauber, sehr gut lesbar

### Stil
- Headlines dürfen groß, ruhig und selbstbewusst sein
- Body-Text eher kompakt und hochwertig gesetzt
- kein verspielter Tech-Look
- kein zu steriler Startup-Look

### Mögliche Pairings
- Display: `Cormorant Garamond`, `Bodoni Moda`, `Instrument Serif`, `Canela`-ähnlich
- Body: `Inter`, `Satoshi`, `General Sans`, `Manrope`, `Work Sans`

Wenn du freie Webfonts nutzt, wähle eine Kombination, die wirklich hochwertig aussieht.

---

## UX- und Layout-Prinzipien

### Allgemeine Regeln
- viel Weißraum
- klare Hierarchie
- große Bildflächen / Materialnähe
- asymmetrische, aber ruhige Layouts
- hochwertiger Editorial-Charakter
- mobil zuerst sauber gedacht

### Nicht gewünscht
- 0815-3-Spalten-Featuregrid mit Icons in Kreisen
- überladene Kartenlandschaften
- generische SaaS-Sections
- zu viele Boxen und Borders
- visuelles Durcheinander

### Gewünschte Wirkung
Die Seite soll eher wirken wie:
- eine hochwertige Produktbroschüre
- eine Architektur-/Interior-Marke
- ein Premium-Showcase

---

## Inhaltliche Seitenstruktur

### 1. Hero Section
Ziel: sofort Premium, Materialität und Differenzierung vermitteln.

**Inhalt:**
- starke Headline
- kurze Value Proposition
- 1–2 hochwertige CTA-Buttons
- große Produktvisualisierung / Materialbild
- optional kleiner Vertrauenshinweis

**Mögliche Headline-Richtung:**
- „Wo echtes Holz auf präzisen 3D-Druck trifft.“
- „Natürliche Materialien. Präzise gefertigt.“
- „Für Räume, die Materialität spürbar machen.“

Bitte finale Texte gern noch verfeinern.

### 2. Produktversprechen
Kurzer Abschnitt, der erklärt, warum diese Kombination besonders ist.

Mögliche Kernaussagen:
- echte Haptik statt Imitation
- Präzision durch additive Fertigung
- individuelle Gestaltungsmöglichkeiten
- nachhaltigerer Materialeinsatz
- geeignet für anspruchsvolle Innenräume und Objektbereiche

### 3. Materialien Section
Zeige die zwei Materialwelten bewusst als Spannungsfeld:
- echtes Holz = Wärme, Maserung, Natürlichkeit, Unikat
- 3D-Druck = Präzision, Freiheit, Wiederholbarkeit, Individualisierung

Wichtig: Nicht als Widerspruch darstellen, sondern als **bewusste Synthese aus Natur und Technologie**.

### 4. Fertigungsprozess
Erzähle den Prozess in 3 bis 5 Schritten:
- Materialauswahl
- digitale Konstruktion
- additive Fertigung
- Veredelung / Montage
- Qualitätsprüfung

Der Abschnitt soll Vertrauen schaffen und die Wertigkeit erklären.

### 5. Für wen es gedacht ist
Zwei Pfade oder Segmente:
- **B2B / Professionals**: Innenarchitektur, Hospitality, Offices, Retail, Objektbau
- **Private Premium-Kunden**: exklusive Wohnräume, Sammler, Designliebhaber

Hier kann man gut mit Cards oder Split-Layout arbeiten, aber bitte edel und reduziert.

### 6. Anwendungs- / Referenzbereich
Zeige mögliche Einsatzszenarien:
- Hotel
- Empfang / Office
- Wohnbereich
- Retail / Showroom
- Konferenzraum

Wenn noch keine echten Referenzen existieren, dann mit gut formulierten Use Cases arbeiten.

### 7. Nachhaltigkeit / Werte
Nicht als Greenwashing, sondern sachlich und glaubwürdig.

Mögliche Punkte:
- echte Materialien
- langlebige Gestaltung
- gezielter Materialeinsatz
- lokale / kontrollierte Fertigung, falls passend
- weniger Wegwerfcharakter, mehr Objektwert

### 8. Abschluss-CTA
Klar, hochwertig, vertrauensvoll.

Beispiele:
- Beratung anfordern
- Projekt besprechen
- Materialmuster anfragen

---

## Tonalität im Text
Der Copy-Stil soll:
- hochwertig
- ruhig
- präzise
- glaubwürdig
- nicht werblich-schreierisch
- nicht generisch-AI-kitschig

### Vermeiden
- „revolutionär“
- „disruptiv“
- „next generation“
- „unlock the future“
- „all-in-one solution“

### Bevorzugen
- konkrete, materialnahe Sprache
- kurze, klare Aussagen
- hochwertige, ruhige Formulierungen

---

## Bildsprache
Die Bildsprache ist extrem wichtig.

### Gewünscht
- Makroaufnahmen von Holzmaserung
- Nahaufnahmen von Materialübergängen
- hochwertige Produkt-Render oder Fotos
- ruhige Interior-Szenen
- natürliches Licht
- Schatten, Tiefe, Materialität

### Vermeiden
- generische Stockfotos von lächelnden Business-Personen
- billige Mockups
- zu technische CAD-Anmutung in der Hero Section
- künstlich überinszenierte Hochglanz-Render ohne Materialtiefe

---

## Animationen und Interaktion
Bitte subtil und hochwertig.

### Gut
- sanfte Fade-/Slide-Reveals
- leichtes Parallax oder ruhige Scroll-Dynamik
- feine Hover-Zustände
- dezente Mikrointeraktionen

### Nicht gut
- übertriebene GSAP-Show
- hektische Animationen
- fliegende Elemente
- starke Blur-/Glow-Effekte

Animationen sollen die Wertigkeit unterstreichen, nicht Aufmerksamkeit erzwingen.

---

## Conversion-Fokus
Die Seite soll nicht nur schön aussehen, sondern gezielt Anfragen erzeugen.

Bitte achte auf:
- klare CTA-Platzierung oberhalb der Falz
- wiederkehrende, aber nicht nervige CTA-Momente
- gute Vertrauenssignale
- klare Leseführung
- hochwertige Formular-/Kontakt-Andeutung im CTA-Bereich

Optional kann ein simples Anfrageformular als Frontend-UI vorbereitet werden.

---

## Komponenten-Ideen
Bitte modular umsetzen. Denkbar sind z. B.:
- `SiteHeader`
- `HeroSection`
- `ValuePropsSection`
- `MaterialsComparison`
- `CraftProcess`
- `AudienceSplit`
- `UseCasesSection`
- `SustainabilitySection`
- `FinalCtaSection`
- `SiteFooter`

Wenn sinnvoll, erstelle auch:
- `BaseButton`
- `SectionIntro`
- `MaterialBadge`
- `SplitLayout`

---

## Beispiel für gewünschte Seitenwirkung in einem Satz
„Eine ruhige, luxuriöse, naturverbundene Produkt-Landingpage, die echtes Holz und 3D-Druck als hochwertige Design- und Fertigungssynthese inszeniert.“

---

## Erwartetes Ergebnis von Claude Code
Bitte liefere:
1. eine saubere Vue-Frontend-Struktur
2. eine stilistisch starke Landingpage
3. hochwertige Beispiel-Copy auf Deutsch oder englisch konsistent
4. responsives Layout
5. saubere Komponentenstruktur
6. gepflegte Styles mit natürlicher Premium-Farbwelt
7. Code, der leicht weiterentwickelt werden kann

---

## Zusatz: bevorzugte Designentscheidung
Wenn du zwischen „zu modern-techy“ und „warm-premium-natural“ entscheiden musst, wähle **immer warm, reduziert, materialnah und hochwertig**.

Wenn du zwischen „verspielt“ und „architektonisch ruhig“ entscheiden musst, wähle **architektonisch ruhig**.

Wenn du zwischen „B2C-Massenmarkt“ und „Premium-B2B / wohlhabend“ entscheiden musst, wähle **Premium-B2B / wohlhabend**.

---

## Optionale Umsetzungsdetails
Wenn es zur Qualität beiträgt, kannst du zusätzlich berücksichtigen:
- sticky, sehr reduzierte Navigation
- smooth scrolling
- dezente Section-Divider
- Material-Swatches
- hochwertige Buttons mit subtiler Hover-Animation
- eine Hero-Komposition mit Holztextur + Produktbild + ruhiger Typografie

---

## Kurzbrief für die kreative Leitlinie
Baue keine typische Tech-Landingpage. Baue eine **digitale Premium-Markenwelt** für ein Produkt aus echtem Holz und 3D-gedruckten Komponenten. Die Seite soll sich an einer **natürlichen, biologischen, organischen Farbwelt** orientieren und gezielt **B2B-Entscheider sowie wohlhabendere Kunden** ansprechen. Fokus auf Materialität, Vertrauen, Designqualität, ruhige Eleganz und hochwertige Conversion.
