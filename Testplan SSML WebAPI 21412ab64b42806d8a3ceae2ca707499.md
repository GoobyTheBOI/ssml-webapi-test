# Testplan SSML WebAPI

**SSML Testplan - Web Browsers**

---

### 1. Doelstelling

Dit testplan heeft als doel om te evalueren hoe goed verschillende Windows-browsers SSML (Speech Synthesis Markup Language) ondersteunen in hun WebAPI. Hierbij wordt specifiek getest op de correcte verwerking van tags. Dit zijn `break`, `emphasis` en `prosody`. De resultaten worden gebruikt om te bepalen of client-side TTS voldoende is om SSML te gebruiken in Thorium Web Reader

---

### 2. Scope

**In scope:**

- Browsers: Chrome, Edge, Firefox en Safari
- SSML-tags: `<break>`, `<emphasis>`, `<prosody>`
- Taal: Nederlands (`nl-NL`)

**Out of scope:**

- Mobiele platforms
- Server-side TTS zoals Google/Azure/AWS

---

### 3. Testopstelling

**Benodigdheden:**

- Windows-pc en Macbook
- Laatste versies van alle relevante browsers
- DevTools toegang (F12 → Console)
- Console-scripts (geleverd in bijlage A)

---

### 4. Testcases

| Test ID | SSML-tag | Beschrijving | Verwachte Resultaat |
| --- | --- | --- | --- |
| TC-01 | `<break>` | Pauze van 500ms tussen 2 zinnen | Tijdmeting toont ≥500ms tussen start/end |
| TC-02 | `<emphasis>` | Emphasis op woord 'belangrijk' | Hoorbare nadruk (intonatie) |
| TC-03 | `<prosody>` | Volume omhoog en langzamer spreken | Volume hoger, tempo trager |

---

### 5. Uitvoering

Per test:

1. Open `index.html` in een browser en druk op de knop "Speak Dutch Phrase"
2. Druk op knop
3. Observeer resultaat:
    - Bij `<break>`: meet tijd tussen `onstart` en `onend`
    - Bij `<emphasis>` en `<prosody>`: luister en beoordeel subjectief
4. Noteer bevindingen in Resultatenmatrix

---

### 6. Resultatenmatrix

| Browser | `<break>` | `<emphasis>` | `<prosody>` | Opmerkingen |
| --- | --- | --- | --- | --- |
| Chromium - Windows 11 | ❌ | ❌ | ❌ | Leest de XML code op. SSML wordt niet herkent door de WebAPI |
| Edge - Windows 11 | ❌ | ❌ | ❌ | Leest de XML code op. SSML wordt niet herkent door de WebAPI |
| Firefox - Windows 11 | ❌ | ❌ | ❌ | Leest de XML code op. SSML wordt niet herkent door de WebAPI |
| Safari  - MacOS 14.5 | ✅ | ⚠️ | ✅ | Hier wordt de SSMl wel opgelezen. Met emphasis hoor ik niet direct of er verandering is. De andere elementen werden wel goed uitgevoerd. |
| Chromium - MacOS 14.5 | ✅ | ⚠️ | ✅ | Hier wordt de SSMl wel opgelezen. Met emphasis hoor ik niet direct of er verandering is. De andere elementen werden wel goed uitgevoerd. |
| FireFox - MacOS 14.5 | ✅ | ⚠️ | ✅ | Hier wordt de SSMl wel opgelezen. Met emphasis hoor ik niet direct of er verandering is. De andere elementen werden wel goed uitgevoerd. |

Legenda: ✅ = werkt, ❌ = werkt niet, ⚠️ = gedeeltelijk/buggy

---

### 7. Analyse & Aanbeveling

De WebAPI ondersteunt geen SSML op windows apparaten, maar wel voor MacOS. In iedergeval MacOS versie hoger dan 14.5. Als SSML wilt werken voor iedereen is er een alternatieve methode nodig of een andere werkwijze zodat de eindgebruiker wel meekrijgt als er met nadruk wordt gesproken.

### 8. Bijlage A - Testscripts (JS)

```
const ssml = `
<speak xml:lang="nl-NL">
  Eerste zin. <break time="500ms"/> Tweede zin.
  <emphasis level="strong">Belangrijke tekst</emphasis>
  <prosody volume="+3dB" rate="slow">Trage luide tekst</prosody>
</speak>`;

const u = new SpeechSynthesisUtterance(ssml);
u.lang = 'nl-NL';
u.onstart = () => performance.mark("start");
u.onend = () => {
  performance.mark("end");
  performance.measure("duur", "start", "end");
  console.log("Duur:", performance.getEntriesByName("duur")[0].duration);
};
speechSynthesis.speak(u);
```

---
