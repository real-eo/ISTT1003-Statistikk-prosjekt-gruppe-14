Her er en konkret oppgaveliste for hver person, med leveranser og frister. Felles frister: problemstillingen godkjent **25. okt**, renset data **28. okt**, alle resultater og tekstutkast **8. nov**, innlevering senest **15. nov**.

---

### Alle sammen (25. okt)
- [ ] Bli enige om problemstilling og hypotese H1–H4, og skriv dem ned.
- [ ] Få dem godkjent av en studentassistent eller Steffi.
- [ ] Avtal felles `random_state = 42` og 80/20-splitt mellom trening og test.
- [ ] Sett opp en felles mappe eller et Git-repo og en felles notebook.

---

### Person 1 – Data
**Analyse (frist 28. okt)**
- [ ] Kjør og forstå rensekoden, og skriv den om med egne kommentarer.
- [ ] Lagre `zomato_india_clean.csv` og lag train/test-splitten én gang, slik at alle bruker de samme radene.
- [ ] Lag en tabell over antall rader etter hvert filtreringssteg.

**Rapport (ca. 1 side)**
- [ ] Dataseksjon: kilde, hva variablene betyr, hvert renseskritt med begrunnelse, særlig hvorfor vurdering 0 = mangler.

**Slutten (9.–14. nov)**
- [ ] Design lysbildene i felles mal og klipp sammen videoen.

**Video:** lysbilde 3, Dataene.

---

### Person 2 – Utforskende analyse
**Analyse (frist 1. nov)**
- [ ] Histogram av vurdering
- [ ] Histogram av pris og stemmer, før og etter log, side om side
- [ ] Spredningsplott av vurdering mot log(pris) og mot log(stemmer)
- [ ] Boksplott av vurdering etter bordbestilling, nettlevering og by
- [ ] Korrelasjonsmatrise
- [ ] Velg de 3–4 beste figurene til rapporten.

**Rapport (ca. 1 side)**
- [ ] Beskriv hva figurene viser, og begrunn log-transformasjonen og hvorfor prisklasse droppes (korrelasjon 0,83).

**Slutten**
- [ ] Referanseliste, sjekk aksenavn og enheter på alle figurer, og korrekturles metodedelen.

**Video:** lysbilde 4, Utforskende analyse.

---

### Person 3 – Regresjon
**Analyse (frist 8. nov)**
- [ ] OLS med statsmodels: `rating ~ log_cost + log_votes + table_booking + online_delivery + city`
- [ ] Tabell med koeffisienter, standardfeil, p-verdier og 95 %-konfidensintervaller
- [ ] Tolk hver koeffisient i ord, alt annet likt.
- [ ] Residualer mot predikerte verdier og QQ-plott. Kommenter mønsteret fra avrundet vurdering.
- [ ] RMSE på testsettet
- [ ] Svar på H1 og H3.

**Rapport (ca. 2 sider):** kort teori om lineær regresjon og forutsetningene, resultater og tolkning.

**Video:** lysbilde 5–6, Regresjon.

---

### Person 4 – Klassifikasjon
**Analyse (frist 8. nov)**
- [ ] Logistisk regresjon med statsmodels på `high_rating` (≥ 3,5), med samme forklaringsvariabler.
- [ ] Tolk koeffisientene som oddsratio (`np.exp(coef)`).
- [ ] KNN med scikit-learn som sammenligning: standardiser variablene og velg k med kryssvalidering.
- [ ] Forvirringsmatrise, sensitivitet, spesifisitet og nøyaktighet for begge modellene på testsettet
- [ ] ROC-kurve med AUC
- [ ] Svar på H2.

**Rapport (ca. 2 sider):** teori, valg av grense, resultater og sammenligning av modellene.

**Video:** lysbilde 7, Klassifikasjon.

---

### Person 5 – Klyngeanalyse
**Analyse (frist 8. nov)**
- [ ] Standardiser log(pris), vurdering og log(stemmer).
- [ ] K-means for K = 1–10, med albueplott for å velge K
- [ ] Tabell med gjennomsnitt per klynge, og gi klyngene tolkbare navn.
- [ ] Spredningsplott farget etter klynge
- [ ] Sjekk sammenhengen mellom klyngene og bordbestilling og by.
- [ ] Svar på H4.

**Rapport (ca. 1,5 sider):** teori om K-means, valg av K, resultater og begrensninger (K-means antar runde klynger).

**Video:** lysbilde 8, Klynger.

---

### Person 6 – Redaktør og koordinator
**Underveis**
- [ ] Følg opp fristene og hold oversikt over hvem som er på etterskudd.
- [ ] Samle alt i én hovednotebook, som blir kodevedlegget.

**Rapport (ca. 2,5 sider + helhet)**
- [ ] Innledning: problemstilling, hypoteser, motivasjon
- [ ] Diskusjon: svar på hver hypotese, lav R², kausalitet mellom stemmer og vurdering, begrensninger i dataene
- [ ] Konklusjon
- [ ] KI-deklarasjon, med innspill fra alle
- [ ] Rediger hele rapporten til én stemme og sjekk at den er maks 10 sider.

**Video:** lysbilde 1–2 og 9–10, Problemstilling, hypoteser og konklusjon.

---

### Alle sammen (9.–15. nov)
- [ ] **9. nov:** Felles gjennomgang av alle resultater. Hver person forklarer sin del til de andre.
- [ ] **11. nov:** Les en annen persons rapportdel og gi tilbakemelding.
- [ ] **13. nov:** Prøveopptak av videoen, med maks 1 min 20 s hver og uten manus.
- [ ] **14.–15. nov:** Endelig opptak, og innlevering i Inspera.

Vil dere at jeg gjør dette om til et delbart dokument eller en oppgaveliste dere kan krysse av i sammen?
