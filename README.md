# 🦖 ARK: Survival Ascended – Singleplayer Mod & Game.ini Manager (v10.16)

A lightweight, **100% client-side** single-file HTML utility for managing your `GameUserSettings.ini` Mod Load Order, `Game.ini` Engram/Crafting Overrides, UE5 Spawn Commands, and Additive Loot Pools (`ConfigOverrideSupplyCrateItems` with `bAppendItemSets=True`) in **ARK: Survival Ascended**.

---

## 🚀 Launch in Browser (GitHub Pages) or Download Offline

- **[EN]** **[Launch App in Browser (English Version)](https://lucasjtoth.github.io/ark-asa-mod-manager/)** | **[📥 Download Offline .html (Releases)](https://github.com/lucasjtoth/ark-asa-mod-manager/releases)**
- **[CZ]** **[Spustit aplikaci v prohlížeči (Česká verze)](https://lucasjtoth.github.io/ark-asa-mod-manager/cz.html)** | **[📥 Stáhnout offline .html (Releases)](https://github.com/lucasjtoth/ark-asa-mod-manager/releases)**

*(Tip: Both the English and Czech web versions share your browser's local memory, so your linked files, saved profiles, and draft loot pools carry over automatically! Works best in Chrome, Edge, Brave, or Opera).*

---

## 💡 What Is This Tool? (Singleplayer & Server Use)

This project was built via **vibecoding** (AI-assisted development) out of real-world frustration with managing large Singleplayer mod lists, hunting down mod IDs, fixing Load Order crashes, and manually digging through mod files to find `_C` class names for `Game.ini`.

The entire application lives inside a **single standalone `.html` file** — no installation, no accounts, and no internet connection required. Using the modern **File System Access API**, you can link it directly to your local ARK files on disk.

- **Built for Singleplayer, usable on Dedicated Servers:** While designed around local Singleplayer file paths (`GameUserSettings.ini`, `Game.ini`, `library.json`, and folder `83374`), **experienced server admins can easily use it too**. All generated rules (`ActiveMods=`, `OverrideNamedEngramEntries`, `ConfigOverrideItemCraftingCosts`, and `ConfigOverrideSupplyCrateItems`) follow 100% standard UE5/ASA syntax. Simply scan the mods installed on your PC client, configure your rules visually, and copy-paste the generated output blocks straight into your server's config files (Nitrado, self-hosted, etc.).

---

## ✨ Key Features (3-in-1 Workspace)

### 📦 1. Mod Manager & Smart Load Order (`GameUserSettings.ini` + `library.json`)
- **Direct Catalog Sync & Uninstalled Mod Detection:** Reads your installed CurseForge mods directly from `library.json` (including mod names, authors, summaries, and thumbnails) and automatically hides pure *Custom Cosmetics* and standalone *Maps* that do not belong in `ActiveMods=`. If a mod in `ActiveMods=` was uninstalled in-game (wiping it from `library.json`), the app flags it with a warning badge, displays its remembered previous name, and lets you remove missing IDs in 1 click.
- **7 Logical Load Order Tiers:** Automatically categorizes mods into 7 priority tiers (*1. Overhaul ➔ 2. Official Events ➔ 3. Stacking & Core Loot ➔ 4. Creatures, Spawns & Taming ➔ 5. Structures, Storage & Logistics ➔ 6. Rebalance, Weapons & QoL ➔ 7. Decor, Furniture & Music*).
- **1-Click Sorting & Profiles:** Auto-sort your entire load order with one click, reorder via Drag & Drop, save custom mod profiles in your browser, and toggle official seasonal events (*Fear Ascended, Winter Wonderland, Summer Bash*, etc.) via the **Official Event Switcher**.

### ⚙️ 2. Local Manifest Scanner (`83374`) + Engrams, Crafting & Spawns (`Game.ini`)
- **Zero Missing Mods:** Scans `Manifest_UFSFiles_Win64.txt` across all your installed mods in folder `83374`, filters out raw engine assets (textures, meshes, audio, animations), and extracts a clean catalog of modded Items, Structures, Resources, Engrams, and Creatures.
- **Built-In Vanilla & DLC Catalog:** Includes base game and expansion items, weapons, armor, saddles, structures, and resources filtered by the DLCs and maps you actually own (**🎟️ My DLCs & Maps**).
- **1-Click Engram & Recipe Overrides:** Hide engrams (`🔒 Hide`), set **0 EP / Level 1**, set crafting costs to **1x Thatch**, or build custom crafting recipes using any vanilla or modded resources (with smart warnings for map-exclusive resources and QoL grinder compatibility such as CS/B+/M+).
- **Batch Spawner:** Copy full UE5 Blueprint spawn commands (`cheat giveitem "Blueprint'..."` / `SpawnDino`), pipe-separated (`|`) batch commands, or download `exec spawn_batch.txt` files.

### 🎁 3. Visual Loot Pool Manager: Beacons, Caves, Treasures, Dino Drops & Mystery Crates (`Game.ini`)
- **Safe Additive Loot (`ConfigOverrideSupplyCrateItems` + `bAppendItemSets=True`):** Appends custom item sets to selected supply crates and dino drops without overwriting or breaking default vanilla loot tables, and automatically merges multiple pools assigned to the same crate into a single valid `ItemSets=(...)` line.
- **Comprehensive Drop Targets:** Supports standard & Double (Ringed) Beacons, Cave/Ocean/Desert crates, Giant Beaver Dams, Extinction OSDs, *Lost Colony* & *Genesis Part 1* crates, **Bob's Tall Tales Buried Treasures**, **Alpha Predator & Carnivore Dino Drops** (including auto-detected modded and event dino drops), plus a dedicated 2-step configurator for the **Mystery Crates** mod.
- **Hidden Engram ➔ Loot Blueprint Workflow:** Hide an engram in Tab 2 and click **📜 Add to Loot (BP)** to make it drop as a craftable Blueprint in crates. Built-in smart safeguards ensure resources/consumables never drop as broken blueprints and apply quality tiers (*Ramshackle – Ascendant*) only to weapons, armor, and saddles.
- **Draft Pools & Undo/Redo:** Save work-in-progress pools as **Drafts** (excluded from `Game.ini` until activated) and use up to 10 steps of **Undo / Redo** (`Ctrl+Z` / `Ctrl+Y`).

---

## 🤝 How It Differs from Beacon (When to Use Which)

**Beacon** is an amazing, industry-standard configuration suite for ARK servers. This manager is **not** meant to replace Beacon's deep server-management ecosystem — instead, it was designed as a fast, zero-setup companion or lightweight alternative tailored specifically for **local Singleplayer modding workflows**:

**Why use this tool alongside (or for quick local tasks instead of) Beacon:**
- **Instant local mod scanning (`83374`):** Because this tool directly scans the `Manifest_UFSFiles_Win64.txt` files on your hard drive, every mod you download is immediately available in the catalog — including brand-new, niche, or freshly updated mods without needing to manually look up or import class strings.
- **Singleplayer `GameUserSettings.ini` Load Order:** It directly reads your local CurseForge `library.json` and helps you organize your `ActiveMods=` load order into 7 logical priority tiers.
- **Zero-install browser workflow:** Everything runs in a single `.html` file and non-invasively updates only your active mods, engram overrides, crafting recipes, and additive loot lines while leaving the rest of your `Game.ini` (breeding, stats, XP multipliers) untouched.

**When you should use Beacon instead:**
- **Full Loot Table Replacement (without `bAppendItemSets=True`):** If you want to completely wipe vanilla supply crates from scratch and use a detailed drop-probability simulator, Beacon is the best tool for the job. This manager uses `ConfigOverrideSupplyCrateItems` strictly with `bAppendItemSets=True` (safely *appending* your custom item sets to existing vanilla loot).
- **Wild Dino Biome Spawn Editing (`NPCSpawnEntries`):** Adjusting which wild creatures spawn in specific map biomes is not supported here.
- **Visual Sliders for Server Multipliers & Direct Cloud/Nitrado Deploys:** For visual rate sliders (breeding, XP, stats) and automated FTP/API server deployments, use Beacon *(though this manager includes built-in raw text editors for quick manual edits to both `.ini` files)*.

---

## 🔒 Security & Privacy (100% Client-Side, No `.exe`, Zero Telemetry)

- **No `.exe` or compiled binaries:** The entire application is a single, human-readable `.html` file. You can right-click and open it in Notepad or VS Code at any time to inspect every single line of code.
- **Zero data collection or network requests:** This utility has no backend server, no analytics, and zero network requests (`fetch` / `XMLHttpRequest`) in its code. Nothing ever leaves your computer. All profiles and settings are stored strictly in your browser's local memory (`localStorage` / `IndexedDB`). *(The only external URLs referenced are official CurseForge mod thumbnail images on `media.forgecdn.net`).*
- **Strict Browser Sandbox (File System Access API):** Because it runs inside your browser's security sandbox, the tool **cannot** browse your computer on its own. It can only access the exact files/folders you explicitly select in the Windows file picker dialog:
  - **Strictly Read-Only:** `library.json` and your `83374` mods folder (`Manifest_UFSFiles_Win64.txt`) are never modified.
  - **Direct Write (Optional):** Only `GameUserSettings.ini` and `Game.ini` are updated when you click *Save*. If you prefer not to grant browser write permissions, you can use the **📂 Upload Once** button and download the generated `.ini` files manually.
- **100% Offline Ready:** You can download the `.html` file, disconnect from the internet completely, and run it locally from your desktop.

---

## [CZ] ČESKÝ POPIS A NÁVOD

### O co jde a jak to vzniklo
Tento nástroj vznikl čistě z praxe jako **vibecoded** fanouškovská utilita (vyvinutá ve spolupráci s AI na míru reálnému hraní). Celá aplikace je **jeden jediný `.html` soubor** – nic se neinstaluje, nikam se nepřihlašujete, nepotřebujete internet ani žádný účet. Soubor jednoduše otevřete v prohlížeči (Chrome, Edge, Brave, Opera) – nebo kliknete na webový odkaz výše – a přes moderní File System Access API ho přímo propojíte se svou složkou ARKu na disku.

Byl od základu postavený pro **Singleplayer hráče**, které nebaví slepě lovit IDčka modů, trápit se s tím, proč jim hra padá kvůli špatnému pořadí modů (Load Order), nebo ručně luštit a vypisovat třídy (`_C`) z cizích modů do `Game.ini`.

### 💡 Singleplayer vs. Dedikovaný server
Nástroj primárně počítá s lokálními soubory Singleplayeru (`GameUserSettings.ini`, `Game.ini`, `library.json` a složka modů `83374`). **Teoreticky ho ale bez problémů využije i admin dedikovaného serveru, který ví, co dělá:**
- Veškerá vygenerovaná pravidla pro `Game.ini` (`OverrideNamedEngramEntries`, `ConfigOverrideItemCraftingCosts`, `ConfigOverrideSupplyCrateItems`) i seznam `ActiveMods=` používají 100% standardní syntaxi Unreal Enginu 5 / ASA.
- Pokud máte mody stažené u sebe v PC (ve svém klientovi), můžete si v manageru naskenovat svou složku `83374`, naklikat si recepty, engramy a loot pooly, a výsledné vygenerované bloky ze spodního okna (nebo přes tlačítko *Kopírovat vygenerované řádky*) jednoduše zkopírovat na svůj server (Nitrado, vlastní stroj atd.).

### ✨ Co všechno program umí (3 hlavní pilíře)

- **1. Mod Manager & Chytrý Load Order (`GameUserSettings.ini` + `library.json`)**
  - Načte vaše stažené mody přímo z `library.json` (včetně názvů, autorů a ikonek) a automaticky skryje čistou kosmetiku (*Custom Cosmetics*) a samostatné mapy, které do `ActiveMods=` v GUS.ini nepatří. Pokud v `ActiveMods=` zůstane ID modu, který byl odinstalován ve hře (a zmizel z `library.json`), program ho zvýrazní varováním, zobrazí jeho dříve známý název a nabídne jeho odebrání jedním klikem.
  - Automaticky roztřídí mody do **7 logických skupin (Tiers 1–7)**: *1. Overhaul* ➔ *2. Official Events* ➔ *3. Stacking & Core Loot* ➔ *4. Creatures & Spawns* ➔ *5. Structures & Storage* ➔ *6. Weapons & QoL* ➔ *7. Decor & Music*.
  - Umožňuje seřadit mody jedním klikem, přetahovat je myší (Drag & Drop), ukládat si různé profily modů v prohlížeči a jedním klikem zapínat oficiální sezónní eventy (*Fear Ascended, Winter Wonderland, Summer Bash* atd.).
- **2. Lokální skener modů (`83374`) + Editor Engramů, Receptů a Spawnů (`Game.ini`)**
  - Naskenuje soubory `Manifest_UFSFiles_Win64.txt` přímo z vašich nainstalovaných modů na disku, odfiltruje balast (textury, zvuky, animace) a vytáhne čistý katalog všech předmětů, staveb, surovin, engramů a dinosaurů – i z úplně nových nebo malých modů.
  - Obsahuje i kompletní vestavěný katalog **Vanilla ARK & DLC** položek (zbraně, brnění, sedla, suroviny, artefakty) s filtrem podle toho, jaká DLC a mapy reálně vlastníte (*🎟️ Moje DLC & Mapy*).
  - Jedním klikem můžete skrýt engramy (`🔒 Skrýt`), nastavit jim 0 EP / Level 1, změnit crafting recept na `1x Thatch` nebo v editoru naklikat vlastní recept z jakýchkoliv vanilla či modovaných surovin (včetně chytrého hlídání exkluzivních surovin z jiných map a kontroly, zda máte aktivní QoL Grinder mod jako CS/B+).
  - Generuje plné UE5 spawn příkazy (`cheat giveitem "Blueprint'..."` / `SpawnDino`), umí je spojit přes svislítko (`|`) pro hromadné spawnování nebo vyexportovat jako dávkový `exec spawn_batch.txt` soubor.
- **3. Loot Manager: Beacony, Jeskyně, Bobovy Poklady, Dino Dropy & Mystery Crates (`Game.ini`)**
  - Využívá bezpečnou direktivu `ConfigOverrideSupplyCrateItems` s parametrem `bAppendItemSets=True` (a automatickým slučováním více balíčků pro stejnou truhlu do jednoho řádku) – přidává vaše vlastní loot balíčky do truhel a dropů, aniž by rozbil nebo smazal původní vanilla loot.
  - Podporuje běžné i dvojité (Ringed) Beacony, jeskynní a oceánské bedny, OSD, bedny z *Lost Colony* a *Genesis 1*, **zakopané poklady z Bob's Tall Tales** (*Buried Treasures*), **dropy z Alfa predátorů a dinosaurů** (včetně automaticky detekovaných dino dropů z vašich modů a eventů) a má přímou dvoukrokovou integraci pro populární mod *Mystery Crates*.
  - **Chytrá pojistka pro skryté engramy a Blueprinty:** Můžete v Záložce 2 skrýt jakýkoliv engram a jedním klikem (*📜 Do Lootu (BP)*) ho poslat do beden jako 100% Blueprint. Pojistka automaticky pohlídá, aby se suroviny nebo konzumovatelné věci nikdy nesnažily padnout jako nefunkční blueprint, a kvalitu (*Ramshackle – Ascendant*) aplikuje jen na zbraně, zbroj a sedla.
  - **Koncepty (Drafts) a historie kroků:** Rozdělaný loot pool si můžete uložit nanečisto (*Uložit jako koncept*), takže se nezapíše do `Game.ini`, dokud ho neaktivujete, a nechybí ani historie kroků Zpět/Vpřed (`Ctrl+Z` / `Ctrl+Y`).

### 🤝 Jak se liší od programu Beacon (Kdy použít který nástroj)

Program **Beacon** je špičkový a v komunitě zaslouženě populární nástroj pro hloubkovou správu serverů. Tento manager nemá ambici s Beaconem soupeřit – vznikl jako rychlá, odlehčená alternativa (nebo doplněk) šitá na míru lokálnímu **Singleplayer hraní s mody**:

**V čem je tento nástroj praktický pro lokální hraní:**
- **Okamžitý sken všech vašich modů na disku (`83374`):** Protože program čte soubory `Manifest_UFSFiles_Win64.txt` přímo z vašeho disku, během pár vteřin v katalogu vidíte všechny předměty, stavby i dinosaury z jakéhokoliv (i úplně nového nebo malého) modu, který jste si stáhli, bez nutnosti ručně dohledávat a importovat třídy.
- **Správa Load Orderu (`GameUserSettings.ini`) a `library.json`:** Načítá přímo váš lokální katalog stažených modů z CurseForge (`library.json`) a pomáhá udržovat správné pořadí modů v `ActiveMods=` pomocí 7 prioritních skupin.
- **Okamžitý běh v prohlížeči bez instalace:** Jde o jeden `.html` soubor, který neinvazivně upravuje pouze řádky s mody, engramy, recepty a přidaným lootem, zatímco zbytek vašeho `Game.ini` (breeding, staty, XP) nechává nedotčený.

**Kdy naopak sáhnout po programu Beacon:**
- **Kompletní přepis (úplné nahrazení) vanilla lootu (bez `bAppendItemSets=True`):** Pokud chcete kompletně smazat a od nuly přepsat celý původní obsah dropu včetně detailní simulace pravděpodobností, Beacon je na to ideální. Tento manager používá `ConfigOverrideSupplyCrateItems` výhradně s `bAppendItemSets=True` (tedy bezpečné *přidávání* vlastních setů k existujícímu lootu).
- **Úprava spawnů divokých dinosaurů v biomech (`ConfigAddNPCSpawnEntriesContainer`):** Úpravu toho, jací dinosauři se v jakém biomu spawní, tento nástroj neobsahuje.
- **Grafické posuvníky herních násobičů a přímý Nitrado/FTP upload:** Pro vizuální ladění rychlostí ochočování, líhnutí či statů a přímé nahrávání na server přes API využijte Beacon *(své stávající hodnoty v `Game.ini` a `GUS.ini` ale můžete kdykoliv zkontrolovat a upravit přes vestavěný Textový editor přímo v této aplikaci)*.

### 🔒 Bezpečnost a soukromí (100% Offline & Open-Source v prohlížeči)
- **Žádný `.exe` instalátor, žádný skrytý kód:** Celá aplikace je jeden obyčejný, čitelný `.html` soubor. Kdokoliv si ho může před spuštěním otevřít v Poznámkovém bloku (Notepad) a zkontrolovat každičký řádek kódu.
- **Nulová síťová komunikace (Žádné odesílání dat):** Nástroj neobsahuje žádné serverové skripty, analytiku, telemetrii ani příkazy pro odesílání dat po síti (`fetch` / `XMLHttpRequest`). Všechna vaše data, cesty k souborům a profily zůstávají výhradně ve vašem prohlížeči (`localStorage` / `IndexedDB`) a na vašem disku. *(Jediné, co si prohlížeč ze sítě načte, jsou oficiální náhledové ikonky modů z adresy `media.forgecdn.net`, pokud máte připojený internet).*
- **Přísný Sandbox prohlížeče (File System Access API):** Aplikace běží v bezpečnostním pískovišti (sandboxu) vašeho prohlížeče. Nemá přístup k vašemu disku ani k operačnímu systému – vidí **výhradně a jen ty konkrétní soubory**, které jí sami v dialogovém okně ručně vyberete a povolíte:
  - **Pouze pro čtení (Read-Only):** Soubor `library.json` a složka modů `83374` (`Manifest_UFSFiles_Win64.txt`). Aplikace z nich pouze načítá seznam modů a tříd, nikdy do nich nic nezapisuje ani je nemění.
  - **Zápis na vyžádání:** Pouze soubory `GameUserSettings.ini` a `Game.ini` – a to jen ve chvíli, kdy sami kliknete na tlačítko *Uložit / Save* (a prohlížeč se vás napoprvé zeptá, zda zápis povolujete). Pokud přímý zápis povolit nechcete, můžete soubory nahrát přes tlačítko *📂 Nahrát jednorázově* a upravené `.ini` si klasicky stáhnout přes prohlížeč.

---

## 👤 Author & License

- **Author:** **@LuJimTo** — [CurseForge Profile](https://www.curseforge.com/members/lujimto/)
- **Disclaimer:** Provided *"AS IS"* without warranty of any kind. Always create a backup copy of your `Saved/Config` folder before modifying `GameUserSettings.ini` and `Game.ini`, and never edit `.ini` files while ARK is running!
- **License:** Licensed under the **[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)](https://creativecommons.org/licenses/by-nc-sa/4.0/)**.
