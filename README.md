# MyVoiceInput

Diktování do libovolného textového pole na macOS. Podržíš **pravý Cmd**,
mluvíš, pustíš — text se objeví tam, kde máš kurzor.

Vzniklo pro psaní promptů v češtině, tedy v jazyce, který velké diktovací
nástroje odbývají. Přepis obstarává ElevenLabs Scribe.

Zdrojový kód je v samostatném repozitáři; tady jsou hotové balíčky,
aby se aplikace mohla sama aktualizovat.

## Instalace krok za krokem

Zabere to pár minut. Potřebuješ účet u ElevenLabs — aplikace sama nic
nepřepisuje, posílá zvuk jejich modelu.

### 1. Stáhni a nainstaluj

Z [posledního vydání](../../releases/latest) stáhni `MyVoiceInput-vX.Y.dmg`,
otevři ho a přetáhni aplikaci na zástupce Aplikace.

Balíček je podepsaný Developer ID a notarizovaný Applem, takže se otevře
bez varování o neznámém vývojáři. Univerzální binárka, macOS 13 a novější,
Intel i Apple Silicon.

### 2. Spusť ji a povol dvě oprávnění

Při prvním spuštění si macOS vyžádá obojí. **Povol oboje, jinak aplikace
nedělá nic užitečného:**

| oprávnění | k čemu | co se stane bez něj |
|---|---|---|
| **Mikrofon** | nahrání hlasu | nahraje se ticho a přijde hláška, že nic neslyšela |
| **Zpřístupnění** | zachycení podržené klávesy | v liště zůstane `○ ?` a klávesa nereaguje |

Zpřístupnění se povoluje v **Nastavení → Soukromí a zabezpečení →
Zpřístupnění**. Je to oprávnění sledovat klávesnici — aplikace jím **čte
výhradně změny modifikátorů**, ne psaný text; běžné klávesy neodposlouchává
vůbec.

Ikona se objeví v horní liště, žádné okno se neotevře. Aplikace se zároveň
sama zaregistruje ke spuštění po přihlášení; v menu to jde vypnout.

### 3. Založ si účet u ElevenLabs

Registrace na [elevenlabs.io](https://elevenlabs.io). Nový účet dostává
**10 000 kreditů měsíčně zdarma a nevyžaduje platební kartu.**

### 4. Vytvoř API klíč

Na [elevenlabs.io/app/settings/api-keys](https://elevenlabs.io/app/settings/api-keys)
vytvoř nový klíč a zkopíruj ho. Ukáže se jen jednou.

### 5. Vlož klíč do aplikace

V menu v liště **Set API key…** a vlož ho. Uloží se do Klíčenky macOS.

Starší verze četly klíč ze souboru `~/.config/elevenlabs/key`. To už
neplatí — stačí menu.

### 6. Vyzkoušej

Podrž **pravý Cmd** déle než 0,4 s, objeví se panel s křivkou hlasitosti,
mluv, pusť. Text se vloží tam, kde máš kurzor.

Práh 0,4 s tam je proto, že aplikace nesleduje běžné klávesy a nepozná
pravý Cmd použitý ve zkratce — rychlé `Cmd+C` jím neprojde.

## Co to stojí

Přepis Scribe v2 stojí **$0,22 za hodinu zvuku**. Používáš-li slovník
vlastních výrazů, účtuje se **$0,05 za hodinu navíc**, tedy $0,27.
Při čtvrt hodině diktování denně jsou to jednotky centů.

## Nastavení v menu

| Volba | |
|---|---|
| Language | 36 jazyků; výchozí je jazyk systému |
| Trigger key | pravý/levý ⌘, ⌥, ⌃ nebo ⇧ |
| Play sounds | pípnutí při startu nahrávání, při vložení a při chybě |
| Paste automatically | vložit pod kurzor, nebo jen do schránky |
| Remove filler words | odstraní vatu a falešné starty |
| Edit vocabulary… | slovník vlastních jmen a odborných výrazů |
| Set API key… | uloží klíč do Klíčenky; prázdné pole ho smaže |
| Usage | spotřeba kreditů jen za přepis |
| Check for Updates… | podepsané vydání, ověřuje se Team ID |
| Launch at login | |

**Slovník je nejúčinnější páka na kvalitu.** Bez něj vychází z
`Journeyman` → `German`, z `Cloudflare Worker` → `Cloud for Work`,
ze `safetensors` → `Sage Sensor`. Se slovníkem všechno správně, na stejné
nahrávce.

## Známé omezení

**Čísla rozbíjí každý engine, a nestabilně.** Jeden běh trefí částku
a rozbije paragraf, druhý naopak, na stejné nahrávce. U paragrafů a částek
si diktovaný text čti po sobě.

## Hlášení chyb

Přes [issues](../../issues). Pomůže verze z menu **About MyVoiceInput…**
a konec logu `~/Library/Logs/MyVoiceInput.log`.

## Licence a příspěvky

MIT. Když ti to šetří čas, můžeš
[přispět na kafe](https://buymeacoffee.com/jenicek666) — dobrovolně, nic
se tím neodemyká.
