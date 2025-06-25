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

- Windows-pc, Macbook en Android-telefoon
- Laatste versies van alle relevante browsers
- **Browser**: DevTools toegang (F12 → Console)
- Console-scripts (geleverd in bijlage A)

---

### 4. Testcases

#### Break Element Tests

| Test ID | SSML-tag | Beschrijving | Verwachte Resultaat |
| --- | --- | --- | --- |
| TC-01a | `<break time="250ms">` | Pauze van 250ms tussen zinnen | Hoorbare pauze van ~250ms |
| TC-01b | `<break time="500ms">` | Pauze van 500ms tussen zinnen | Hoorbare pauze van ~500ms |
| TC-01c | `<break time="1s">` | Pauze van 1 seconde tussen zinnen | Hoorbare pauze van ~1 seconde |
| TC-01d | `<break time="2s">` | Pauze van 2 seconden tussen zinnen | Hoorbare pauze van ~2 seconden |
| TC-01e | `<break strength="none">` | Geen pauze | Geen hoorbare pauze |
| TC-01f | `<break strength="x-weak">` | Extra zwakke pauze | Zeer korte pauze |
| TC-01g | `<break strength="weak">` | Zwakke pauze | Korte pauze |
| TC-01h | `<break strength="medium">` | Gemiddelde pauze | Gemiddelde pauze |
| TC-01i | `<break strength="strong">` | Sterke pauze | Lange pauze |
| TC-01j | `<break strength="x-strong">` | Extra sterke pauze | Zeer lange pauze |

#### Prosody Element Tests

| Test ID | SSML-tag | Beschrijving | Verwachte Resultaat |
| --- | --- | --- | --- |
| TC-02a | `<prosody rate="x-slow">` | Extra langzaam spreken | Zeer traag tempo |
| TC-02b | `<prosody rate="slow">` | Langzaam spreken | Traag tempo |
| TC-02c | `<prosody rate="medium">` | Normaal tempo | Standaard spreeksnelheid |
| TC-02d | `<prosody rate="fast">` | Snel spreken | Verhoogd tempo |
| TC-02e | `<prosody rate="x-fast">` | Extra snel spreken | Zeer hoog tempo |
| TC-02f | `<prosody rate="50%">` | 50% van normaal tempo | Halvering van snelheid |
| TC-02g | `<prosody rate="200%">` | 200% van normaal tempo | Verdubbeling van snelheid |
| TC-02h | `<prosody pitch="x-low">` | Extra lage toonhoogte | Zeer lage stem |
| TC-02i | `<prosody pitch="low">` | Lage toonhoogte | Lage stem |
| TC-02j | `<prosody pitch="medium">` | Normale toonhoogte | Standaard stem |
| TC-02k | `<prosody pitch="high">` | Hoge toonhoogte | Hoge stem |
| TC-02l | `<prosody pitch="x-high">` | Extra hoge toonhoogte | Zeer hoge stem |
| TC-02m | `<prosody pitch="+50%">` | 50% hoger dan normaal | Verhoogde toonhoogte |
| TC-02n | `<prosody pitch="-20%">` | 20% lager dan normaal | Verlaagde toonhoogte |
| TC-02o | `<prosody volume="silent">` | Stilte | Geen geluid |
| TC-02p | `<prosody volume="x-soft">` | Extra zacht | Zeer laag volume |
| TC-02q | `<prosody volume="soft">` | Zacht | Laag volume |
| TC-02r | `<prosody volume="medium">` | Normaal volume | Standaard volume |
| TC-02s | `<prosody volume="loud">` | Luid | Hoog volume |
| TC-02t | `<prosody volume="x-loud">` | Extra luid | Zeer hoog volume |
| TC-02u | `<prosody volume="+6dB">` | 6dB luider | Verhoogd volume |
| TC-02v | `<prosody volume="-6dB">` | 6dB zachter | Verlaagd volume |

#### Emphasis Element Tests

| Test ID | SSML-tag | Beschrijving | Verwachte Resultaat |
| --- | --- | --- | --- |
| TC-03a | `<emphasis level="none">` | Geen nadruk | Normale intonatie |
| TC-03b | `<emphasis level="reduced">` | Verminderde nadruk | Minder nadruk dan normaal |
| TC-03c | `<emphasis level="moderate">` | Gemiddelde nadruk | Duidelijke nadruk |
| TC-03d | `<emphasis level="strong">` | Sterke nadruk | Krachtige nadruk |
| TC-03e | `<emphasis>` (default) | Standaard nadruk | Normale nadruk |

---

### 5. Uitvoering

Per test:

1. Open `index.html` in een browser
2. Klik op de gewenste testknop (bijv. "Break 250ms", "Rate: slow", "Level: strong")
3. Observeer het resultaat:
    - Bij `<break>`: luister naar de pauze en controleer timing in console (F12)
    - Bij `<prosody>`: beoordeel hoorbare veranderingen in rate, pitch of volume
    - Bij `<emphasis>`: luister naar eventuele nadruk of intonatieverandering
    - Bij complexe combinaties: beoordeel of alle elementen correct worden uitgevoerd
4. Noteer bevindingen in de Resultatenmatrix (✅ = werkt, ❌ = werkt niet)

**Aandachtspunten tijdens testen:**
- Console toont SSML-code en timing informatie
- Let op verschil tussen SSML-interpretatie vs. letterlijk voorlezen van XML
- Test elke knop individueel voor accurate resultaten

---

### 6. Resultaten

**PC/Laptop: Windows 11 en MacOS 14.5**

#### Break Element Attributen (Testcases TC-01a t/m TC-01j)

| Browser | `time="250ms"` | `time="500ms"` | `time="1s"` | `time="2s"` | `strength="none"` | `strength="x-weak"` | `strength="weak"` | `strength="medium"` | `strength="strong"` | `strength="x-strong"` |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Chromium - Windows 11 | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Edge - Windows 11 | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Firefox - Windows 11 | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Safari - MacOS 14.5 | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Chromium - MacOS 14.5 | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Firefox - MacOS 14.5 | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |

#### Prosody Element Attributen (Testcases TC-02a t/m TC-02v)

| Browser | `rate="x-slow"` | `rate="slow"` | `rate="medium"` | `rate="fast"` | `rate="x-fast"` | `rate="50%"` | `rate="200%"` | `pitch="x-low"` | `pitch="low"` | `pitch="medium"` | `pitch="high"` | `pitch="x-high"` | `pitch="+50%"` | `pitch="-20%"` |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Chromium - Windows 11 | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Edge - Windows 11 | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Firefox - Windows 11 | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Safari - MacOS 14.5 | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Chromium - MacOS 14.5 | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Firefox - MacOS 14.5 | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |

| Browser | `volume="silent"` | `volume="x-soft"` | `volume="soft"` | `volume="medium"` | `volume="loud"` | `volume="x-loud"` | `volume="+6dB"` | `volume="-6dB"` | Combined Attributes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Chromium - Windows 11 | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Edge - Windows 11 | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Firefox - Windows 11 | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Safari - MacOS 14.5 | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Chromium - MacOS 14.5 | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Firefox - MacOS 14.5 | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |

#### Emphasis Element Attributen (Testcases TC-03a t/m TC-03e)

| Browser | `level="none"` | `level="reduced"` | `level="moderate"` | `level="strong"` | Default (no level) |
| --- | --- | --- | --- | --- | --- |
| Chromium - Windows 11 | ❌ | ❌ | ❌ | ❌ | ❌ |
| Edge - Windows 11 | ❌ | ❌ | ❌ | ❌ | ❌ |
| Firefox - Windows 11 | ❌ | ❌ | ❌ | ❌ | ❌ |
| Safari - MacOS 14.5 | ❌ | ❌ | ❌ | ❌ | ❌ |
| Chromium - MacOS 14.5 | ❌ | ❌ | ❌ | ❌ | ❌ |
| Firefox - MacOS 14.5 | ❌ | ❌ | ❌ | ❌ | ❌ |

#### Opmerkingen per Browser

| Browser | Opmerkingen |
| --- | --- |
| Chromium - Windows 11 | Geen SSML ondersteuning. Leest XML markup letterlijk op als tekst. |
| Edge - Windows 11 | Geen SSML ondersteuning. Leest XML markup letterlijk op als tekst. |
| Firefox - Windows 11 | Geen SSML ondersteuning. Leest XML markup letterlijk op als tekst. |
| Safari - MacOS 14.5 | Volledige ondersteuning voor break en prosody elementen. Alle time/strength breaks werken. Alle rate en volume attributen functioneren correct. Emphasis wordt niet ondersteund. |
| Chromium - MacOS 14.5 | Volledige ondersteuning voor break en prosody elementen. Alle time/strength breaks werken. Alle rate en volume attributen functioneren correct. Emphasis wordt niet ondersteund. |
| Firefox - MacOS 14.5 | Volledige ondersteuning voor break en prosody elementen. Alle time/strength breaks werken. Alle rate en volume attributen functioneren correct. Emphasis wordt niet ondersteund. |

**Android 14 Phone**

#### Break Element Attributen (Testcases TC-01a t/m TC-01j)

| Browser | `time="250ms"` | `time="500ms"` | `time="1s"` | `time="2s"` | `strength="none"` | `strength="x-weak"` | `strength="weak"` | `strength="medium"` | `strength="strong"` | `strength="x-strong"` |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Chromium | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Edge | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Firefox | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |

#### Prosody Element Attributen (Testcases TC-02a t/m TC-02v)

| Browser | `rate="x-slow"` | `rate="slow"` | `rate="medium"` | `rate="fast"` | `rate="x-fast"` | `rate="50%"` | `rate="200%"` | `pitch="x-low"` | `pitch="low"` | `pitch="medium"` | `pitch="high"` | `pitch="x-high"` | `pitch="+50%"` | `pitch="-20%"` |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Chromium | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Edge | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Firefox | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |

| Browser | `volume="silent"` | `volume="x-soft"` | `volume="soft"` | `volume="medium"` | `volume="loud"` | `volume="x-loud"` | `volume="+6dB"` | `volume="-6dB"` | Combined Attributes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Chromium | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Edge | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Firefox | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |

#### Emphasis Element Attributen (Testcases TC-03a t/m TC-03e)

| Browser | `level="none"` | `level="reduced"` | `level="moderate"` | `level="strong"` | Default (no level) |
| --- | --- | --- | --- | --- | --- |
| Chromium - Windows 11 | ❌ | ❌ | ❌ | ❌ | ❌ |
| Edge - Windows 11 | ❌ | ❌ | ❌ | ❌ | ❌ |
| Firefox - Windows 11 | ❌ | ❌ | ❌ | ❌ | ❌ |
| Safari - MacOS 14.5 | ❌ | ❌ | ❌ | ❌ | ❌ |
| Chromium - MacOS 14.5 | ❌ | ❌ | ❌ | ❌ | ❌ |
| Firefox - MacOS 14.5 | ❌ | ❌ | ❌ | ❌ | ❌ |

#### Opmerkingen Android

| Browser | Opmerkingen |
| --- | --- |
| Chromium | Volledige ondersteuning voor break elementen (time en strength). Rate attributen werken volledig. Pitch en volume attributen niet ondersteund. Emphasis werkt niet. |
| Edge | Volledige ondersteuning voor break elementen (time en strength). Rate attributen werken volledig. Pitch en volume attributen niet ondersteund. Emphasis werkt niet. |
| Firefox | Volledige ondersteuning voor break elementen (time en strength). Rate attributen werken volledig. Pitch en volume attributen niet ondersteund. Emphasis werkt niet. |

Legenda: ✅ = werkt, ❌ = werkt niet, ⚠️ = gedeeltelijk/buggy

---

### 7. Analyse & Aanbeveling

#### **Hoofdbevindingen**

Uit de testresultaten blijkt dat SSML-ondersteuning via de Web Speech API sterk afhankelijk is van het gebruikte platform en de browser-engine.

**Windows 11**
- ❌ Geen enkele browser (Chrome, Edge, Firefox) interpreteert SSML correct
- ➡️ XML-tags worden letterlijk uitgesproken

**macOS 14.5**
- ✅ Uitgebreide ondersteuning voor `<break>` en `<prosody rate>`
- ❌ Geen ondersteuning voor `<prosody pitch>`, `<volume>` en `<emphasis>`
- ➡️ Werkt stabiel in Safari, Chromium en Firefox

**Android 14 (Chromium/Edge/Firefox)**
- ✅ `<break>` en `<prosody rate>` worden correct uitgevoerd
- ❌ `<pitch>`, `<volume>` en `<emphasis>` worden genegeerd
- ➡️ Geschikt voor eenvoudige SSML maar niet voor expressieve spraak

---

#### **Aanbeveling**

Voor Thorium Web is een pure client-side implementatie van SSML **niet platform-onafhankelijk genoeg**. Daarom wordt een hybride strategie aanbevolen:

1. **Platformdetectie + fallback**
   Detecteer het platform/browser en bied waar mogelijk SSML aan (macOS). Gebruik op andere platformen alternatieven zoals pauzes, stringherhaling of synthetische nadruk.

2. **Beperk je tot breed ondersteunde elementen**
   Implementeer alleen SSML-tags met hoge compatibiliteit:
   - `<break>` (time en strength)
   - `<prosody rate>`
   Vermijd pitch, volume en emphasis tenzij server-TTS wordt toegepast.

3. **Onderzoek server-side TTS als uitbreidingsoptie**
   Overweeg een optionele integratie met cloud-TTS-diensten (zoals ElevenLabs, Google TTS of Azure), waarin volledige SSML-ondersteuning en betere expressiviteit mogelijk zijn.

4. **Alternatieve nadrukstrategieën**
   Omdat `<emphasis>` nergens werkt, kan nadruk worden gesimuleerd door:
   - Herhaling van het woord (bijv. _“echt, écht belangrijk”_)
   - Pauzes voor/na belangrijke woorden
   - Toonverandering via semantische herformulering

---

### **Conclusie**

De Web Speech API ondersteunt SSML onvoldoende op Windows-platforms, beperkt op Android, en redelijk op macOS. **Client-side SSML is daardoor geen betrouwbare basis voor brede inzet.** Voor Thorium Web is een **hybride oplossing** het meest toekomstbestendig: SSML waar mogelijk, met slimme fallback-methodes op andere platformen.


### 8. Bijlage A - Testscripts (HTML)

Zie `index.html` voor de volledige testsuite met:

- **Break Element Tests**: 10 buttons voor time/strength variaties
- **Prosody Element Tests**: 24 buttons voor rate/pitch/volume combinaties
- **Emphasis Element Tests**: 5 buttons voor alle emphasis levels
- **Complex Combinations**: 3 realistische scenario's

De HTML-file bevat JavaScript functies die:
- SSML genereren per testcase
- Console logging voor timing metingen
- Visual display van gebruikte SSML-markup
- Nederlandse tekst (`nl-NL`) voor consistente testen

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SSML Comprehensive Test</title>
    <link
        href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap"
        rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f0f2f5;
            padding: 20px;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            background-color: #ffffff;
            padding: 32px;
            border-radius: 12px;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
        }

        .test-section {
            margin-bottom: 30px;
            padding: 20px;
            border: 1px solid #e5e7eb;
            border-radius: 8px;
        }

        button {
            background: linear-gradient(145deg, #6366f1, #4f46e5);
            color: white;
            padding: 10px 20px;
            border-radius: 6px;
            border: none;
            font-weight: 600;
            cursor: pointer;
            margin: 5px;
            transition: all 0.2s ease-in-out;
        }

        button:hover {
            background: linear-gradient(145deg, #4f46e5, #6366f1);
            transform: translateY(-1px);
        }

        .ssml-text {
            background-color: #f9fafb;
            padding: 10px;
            border-radius: 4px;
            font-family: monospace;
            font-size: 12px;
            margin-top: 10px;
            word-wrap: break-word;
        }
    </style>
</head>

<body>
    <div class="container">
        <h1 class="text-3xl font-bold text-center mb-8">SSML Comprehensive Test
            Suite</h1>

        <!-- Break Element Tests -->
        <div class="test-section">
            <h2 class="text-2xl font-semibold mb-4">Break Element Tests</h2>

            <h3 class="text-lg font-medium mb-2">Time-based breaks:</h3>
            <button onclick="testBreak('time', '250ms')">Break 250ms</button>
            <button onclick="testBreak('time', '500ms')">Break 500ms</button>
            <button onclick="testBreak('time', '1s')">Break 1 second</button>
            <button onclick="testBreak('time', '2s')">Break 2 seconds</button>

            <h3 class="text-lg font-medium mb-2 mt-4">Strength-based breaks:
            </h3>
            <button onclick="testBreak('strength', 'none')">Strength:
                none</button>
            <button onclick="testBreak('strength', 'x-weak')">Strength:
                x-weak</button>
            <button onclick="testBreak('strength', 'weak')">Strength:
                weak</button>
            <button onclick="testBreak('strength', 'medium')">Strength:
                medium</button>
            <button onclick="testBreak('strength', 'strong')">Strength:
                strong</button>
            <button onclick="testBreak('strength', 'x-strong')">Strength:
                x-strong</button>
        </div>

        <!-- Prosody Element Tests -->
        <div class="test-section">
            <h2 class="text-2xl font-semibold mb-4">Prosody Element Tests</h2>

            <h3 class="text-lg font-medium mb-2">Rate variations:</h3>
            <button onclick="testProsody('rate', 'x-slow')">Rate:
                x-slow</button>
            <button onclick="testProsody('rate', 'slow')">Rate: slow</button>
            <button onclick="testProsody('rate', 'medium')">Rate:
                medium</button>
            <button onclick="testProsody('rate', 'fast')">Rate: fast</button>
            <button onclick="testProsody('rate', 'x-fast')">Rate:
                x-fast</button>
            <button onclick="testProsody('rate', '50%')">Rate: 50%</button>
            <button onclick="testProsody('rate', '200%')">Rate: 200%</button>

            <h3 class="text-lg font-medium mb-2 mt-4">Pitch variations:</h3>
            <button onclick="testProsody('pitch', 'x-low')">Pitch:
                x-low</button>
            <button onclick="testProsody('pitch', 'low')">Pitch: low</button>
            <button onclick="testProsody('pitch', 'medium')">Pitch:
                medium</button>
            <button onclick="testProsody('pitch', 'high')">Pitch: high</button>
            <button onclick="testProsody('pitch', 'x-high')">Pitch:
                x-high</button>
            <button onclick="testProsody('pitch', '+50%')">Pitch: +50%</button>
            <button onclick="testProsody('pitch', '-20%')">Pitch: -20%</button>

            <h3 class="text-lg font-medium mb-2 mt-4">Volume variations:</h3>
            <button onclick="testProsody('volume', 'silent')">Volume:
                silent</button>
            <button onclick="testProsody('volume', 'x-soft')">Volume:
                x-soft</button>
            <button onclick="testProsody('volume', 'soft')">Volume:
                soft</button>
            <button onclick="testProsody('volume', 'medium')">Volume:
                medium</button>
            <button onclick="testProsody('volume', 'loud')">Volume:
                loud</button>
            <button onclick="testProsody('volume', 'x-loud')">Volume:
                x-loud</button>
            <button onclick="testProsody('volume', '+6dB')">Volume:
                +6dB</button>
            <button onclick="testProsody('volume', '-6dB')">Volume:
                -6dB</button>

            <h3 class="text-lg font-medium mb-2 mt-4">Combined prosody:</h3>
            <button onclick="testProsodyCombined()">Rate + Pitch +
                Volume</button>
        </div>

        <!-- Emphasis Element Tests -->
        <div class="test-section">
            <h2 class="text-2xl font-semibold mb-4">Emphasis Element Tests</h2>

            <button onclick="testEmphasis('none')">Level: none</button>
            <button onclick="testEmphasis('reduced')">Level: reduced</button>
            <button onclick="testEmphasis('moderate')">Level: moderate</button>
            <button onclick="testEmphasis('strong')">Level: strong</button>
            <button onclick="testEmphasis('')">Default emphasis</button>
        </div>

        <!-- Complex Combinations -->
        <div class="test-section">
            <h2 class="text-2xl font-semibold mb-4">Complex Combinations</h2>

            <button onclick="testComplexCombination1()">Story with all
                elements</button>
            <button onclick="testComplexCombination2()">Technical
                announcement</button>
            <button onclick="testComplexCombination3()">Emotional
                speech</button>
        </div>

        <!-- Display area for SSML -->
        <div id="ssmlDisplay" class="ssml-text" style="display: none;"></div>
    </div>

    <script>
        function speakSSML(ssml) {
            console.log('Speaking SSML:', ssml);
            document.getElementById('ssmlDisplay').textContent = ssml;
            document.getElementById('ssmlDisplay').style.display = 'block';

            const utterance = new SpeechSynthesisUtterance(ssml);
            utterance.lang = 'nl-NL';
            utterance.onstart = () => performance.mark("start");
            utterance.onend = () => {
                performance.mark("end");
                performance.measure("duration", "start", "end");
                console.log("Duration:", performance.getEntriesByName("duration")[0].duration);
            };
            speechSynthesis.speak(utterance);
        }

        function testBreak(type, value) {
            let ssml;
            if (type === 'time') {
                ssml = `<speak>Voor de pauze. <break time="${value}"/> Na de pauze van ${value}.</speak>`;
            } else {
                ssml = `<speak>Voor de pauze. <break strength="${value}"/> Na de pauze met sterkte ${value}.</speak>`;
            }
            speakSSML(ssml);
        }

        function testProsody(attribute, value) {
            const ssml = `<speak>Normale tekst. <prosody ${attribute}="${value}">Deze tekst heeft ${attribute} ingesteld op ${value}.</prosody> Weer normale tekst.</speak>`;
            speakSSML(ssml);
        }

        function testProsodyCombined() {
            const ssml = `<speak>Normale tekst. <prosody rate="slow" pitch="high" volume="loud">Deze tekst is langzaam, hoog en luid.</prosody> Weer normale tekst.</speak>`;
            speakSSML(ssml);
        }

        function testEmphasis(level) {
            let ssml;
            if (level === '') {
                ssml = `<speak>Normale tekst met <emphasis>standaard nadruk</emphasis> erin.</speak>`;
            } else {
                ssml = `<speak>Normale tekst met <emphasis level="${level}">nadruk niveau ${level}</emphasis> erin.</speak>`;
            }
            speakSSML(ssml);
        }

        function testComplexCombination1() {
            const ssml = `<speak>
                <emphasis level="strong">Welkom</emphasis> bij onze demonstratie.
                <break time="500ms"/>
                We gaan nu <prosody rate="slow">langzaam</prosody> beginnen.
                <break strength="medium"/>
                Daarna wordt het <prosody rate="fast" pitch="high">sneller en hoger</prosody>.
                <break time="1s"/>
                En we eindigen met <emphasis level="strong"><prosody volume="loud">krachtige nadruk</prosody></emphasis>!
            </speak>`;
            speakSSML(ssml);
        }

        function testComplexCombination2() {
            const ssml = `<speak>
                <emphasis level="moderate">Technische aankondiging:</emphasis>
                <break strength="strong"/>
                De server zal <prosody rate="slow" pitch="low">over vijf minuten</prosody> worden herstart.
                <break time="800ms"/>
                <emphasis level="strong">Sla uw werk op</emphasis> voordat dit gebeurt.
                <break strength="weak"/>
                <prosody volume="soft">Bedankt voor uw begrip.</prosody>
            </speak>`;
            speakSSML(ssml);
        }

        function testComplexCombination3() {
            const ssml = `<speak>
                <prosody rate="x-slow" pitch="low" volume="soft">Ik ben</prosody>
                <break time="300ms"/>
                <emphasis level="moderate">heel</emphasis>
                <break time="200ms"/>
                <prosody rate="fast" pitch="high" volume="loud"><emphasis level="strong">blij</emphasis></prosody>
                <break time="500ms"/>
                <prosody rate="medium" pitch="medium">om hier te zijn.</prosody>
            </speak>`;
            speakSSML(ssml);
        }
    </script>
</body>

</html>
```

---
