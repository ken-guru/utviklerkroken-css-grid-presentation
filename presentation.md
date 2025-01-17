---
marp: true
paginate: true
---

<!-- _class: invert -->

# Introduksjon til CSS Grid Layout

## Ken P. Sørevåge

Arkitekt

---

# Grunnleggende terminologi

- **Grid Container**: Elementet med `display: grid`.
- **Grid Item**: Direkte barn av Grid Container.
- **Grid Line**: Delingslinjer som skaper rutenettstrukturen.
- **Grid Track**: Plassen mellom to tilstøtende Grid Lines.
- **Grid Cell**: Krysningspunktet mellom en rad og en kolonne.
- **Grid Area**: Et rektangulært område avgrenset av fire Grid Lines.
- **Explicit Grid**: Grid spor som er eksplisitt definert med `grid-template-*`.
- **Implicit Grid**: Grid spor generert automatisk basert på innholdet.
- **Grid Flow**: Hvordan `grid-auto-flow` styrer plasseringen av elementer.

---

<!-- _class: invert -->

# CSS Grid egenskaper

Noen beskrivelser og eksempler.

---

# Grid Container

```css
.container {
  display: grid;
}
```

- Etablerer elementet som en Grid Container og definerer konteksten for innholdet.
- Kan bruke `display: inline-grid` for å lage en inline Grid Container.
- Kan bruke `display: subgrid` for å arve grid-definisjonene fra en overordnet Grid Container.

---

# Grid kolonner og rader

```css
.container {
  grid-template-columns: 1fr 1fr 1fr; /* eventuelt repeat(3, 1fr) */
  grid-template-rows: 100px auto;
}
```

- Definerer størrelsen på kolonner og rader i Grid Containeren.
- Bruker **fr** som enhet (fraction unit) for proporsjonal plass.
- Andre muligheter:
  - **`minmax()`**: Definerer minimums- og maksimumsstørrelser.
  - **`auto`**: Justerer størrelsen basert på innholdet.
  - **`fit-content()`**: Passer til innhold innenfor en maksimal bredde.

<!-- /examples/01.html -->

---

# Avstand mellom grid tracks

```css
.container {
  row-gap: 1rem;
  column-gap: 1rem;
}
```

- Definerer avstanden mellom grid tracks.
- Alternativ: `gap: 1rem` for å sette både rad- og kolonneavstand samtidig.
- For å sette avstand til kantene, kombiner `gap` med `padding`:

```css
.container {
  gap: 1rem;
  padding: 1rem;
}
```

<!-- /examples/02.html -->

---

# Justering av elementer i grid containeren

```css
.container {
  justify-items: end;
  align-items: center;
}
```

- **`justify-items`** justerer elementene langs hovedaksen (inline-aksen).
- **`align-items`** justerer elementene langs tverraksen (block-aksen).

Forskjellen på **`align-content`** og **`align-items`**:
- `align-content`: Distribuerer flere spor (når det er plass til overs).
- `align-items`: Justerer innholdet i hvert spor.

<!-- /examples/03.html -->

---

# Justering av innholdet i grid cellene

```css
.container {
  justify-content: space-between;
  align-content: center;
}
```

- **`justify-content`**: Justerer innholdet langs hovedaksen.
- **`align-content`**: Justerer innholdet langs tverraksen.
- Krever ledig plass i grid containeren.

<!-- /examples/04.html -->

---

# Justering av individuelle grid items

```css
.item {
  justify-self: center;
  align-self: end;
}
```

- **`justify-self`**: Justerer elementet langs hovedaksen i sin grid cell.
- **`align-self`**: Justerer elementet langs tverraksen i sin grid cell.

<!-- /examples/05.html -->

---

# Plassering av individuelle grid items

```css
.item {
  grid-column-start: 1;
  grid-column-end: 3;
  grid-row-start: 2;
  grid-row-end: 4;
}
```

- Definerer start- og sluttpunkt for en grid item basert på Grid Lines.
- Alternativ: Bruk `span` for å strekke over flere spor.

```css
.item {
  grid-column: 1 / span 2;
}
```

<!-- /examples/06.html -->

---

# Navngitte områder

```css
.container {
  grid-template-areas:
    "header header header"
    "nav    main   main"
    "nav    footer .";
}

.header {
  grid-area: header;
}
```

- En strukturert måte å definere områder på.
- Bruk `grid-area` for å plassere elementer i områdene.
- Tomme celler representeres med `.`.

<!-- /examples/07.html -->

---

# Subgrid

```css
.parent {
  display: grid;
  grid-template-columns: 1fr 2fr;
}

.child {
  display: subgrid;
}
```

- Arver grid-definisjoner fra en overordnet Grid Container.
- Nyttig for komplekse, nested layouts.

<!-- /examples/08.html -->

---

# Komplett eksempel

- Kombinerer flere egenskaper for å skape en kompleks layout.
- Navngitte områder: Bruk av grid-template-areas for å organisere layouten.
- Grid og Flexbox: Kombinasjon av teknologier for ulike dimensjonale behov.
- Responsivitet: Media queries og dynamiske verdier som auto-fill og minmax() demonstrerer hvordan layout tilpasses ulike skjermstørrelser.

<!-- /examples/09.html -->

---

<!-- _class: invert -->

# Takk for meg

