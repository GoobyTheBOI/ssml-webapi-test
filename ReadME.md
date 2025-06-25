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

**PC/Laptop: Windows 11 en MacOS 14.5**

#### Break Element Attributen

| Browser | `time="250ms"` | `time="500ms"` | `time="1s"` | `time="2s"` | `strength="none"` | `strength="x-weak"` | `strength="weak"` | `strength="medium"` | `strength="strong"` | `strength="x-strong"` |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Chromium - Windows 11 | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Edge - Windows 11 | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Firefox - Windows 11 | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Safari - MacOS 14.5 | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Chromium - MacOS 14.5 | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Firefox - MacOS 14.5 | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |

#### Prosody Element Attributen

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

#### Emphasis Element Attributen

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

#### Break Element Attributen

| Browser | `time="250ms"` | `time="500ms"` | `time="1s"` | `time="2s"` | `strength="none"` | `strength="x-weak"` | `strength="weak"` | `strength="medium"` | `strength="strong"` | `strength="x-strong"` |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Chromium | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Edge | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Firefox | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |

#### Prosody Element Attributen

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

#### Emphasis Element Attributen

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


### 8. Bijlage A - Testscripts (JS)

```
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
