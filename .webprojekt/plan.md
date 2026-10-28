# Weboldal-generálási terv: Eliza Beauty Salon, 1 koncepció

## Kontextus
A brief jóváhagyva (`eliza-alapanyag/.webprojekt/brief.md`). A felhasználó **1 koncepció-irányt** kért (a skill alapból 3-at kínálna). A projekt gyökere: `D:\GRAFIKUS\CLAUDE CODE\Eliza projekt\eliza-alapanyag\eliza-alapanyag\` (itt van a `.webprojekt/`, a `logo/`, a `szovegek.md` és az `Eliza projekt képek/`). A cél egy böngészőben megnyitható, kész érzetű **főoldal-prototípus**.

## Brand brief összefoglaló
Egyszemélyes Ráday utcai kozmetika: Sipos Eliza mesterkozmetikus (14 év, 1300+ vendég) arcfiatalító és anti-akné kezeléseket végez természetes hatóanyagokkal. A fő célcsoport a 35–55 éves igényes nő, a mellékcsoport az aknés tini és az anyukája. Fő cselekvés az időpontkérés (űrlap vagy telefon). A megkülönböztető: 50%-os elégedettségi garancia, személyes, privát, fájdalommentes kezelés. A hangvétel tegező, meleg, egyes szám első személyű.

## Koncepció irány: „Aranyszál”

**Paletta** (a design system szerint kötelező): Rózsafa `#8E4A5A` (primary) · Sötét kakaó `#2E2626` (secondary) · Homokarany `#C9A27E` (accent). Háttér: Krém `#FAF6F2` · felület: Púder `#F1E6DF` · szöveg: `#2E2626` · másodlagos szöveg: `#6B5F5C`.
**Fontok** (kötelező): Cormorant Garamond 500/600 (+ dőlt) a címsorokhoz, Jost 400/500 a szövegtörzshöz. A kickerek Jost 500 nagybetűvel, ahogy a design system előírja.

**Vizuális megközelítés:** A logóban a „BEAUTY SALON” felirat két oldalán futó vékony homokarany vonalból lesz az oldal visszatérő motívuma, egy finom **aranyszál**. Görgetéskor ez a szál „rajzolódik” végig az oldalon (SVG stroke-animáció), összeköti a szakaszokat, és ezen fűződik fel a 4 lépéses folyamat is (valódi sorrend, ezért kaphat számozást). Ugyanez a szál jelenik meg:
1. a menüpontok aláhúzásában,
2. a szakaszok elválasztóiban,
3. az idézetjelek mellett,
4. a garanciapecsét körvonalában,
5. a lábléc zárásában, ahol egy pontban végződik.

Az elrendezés tágas és editorial, aszimmetrikus (7/5-ös és 5/7-es osztások). A képek 16 px-es lekerekítéssel, egymásra lógó rétegekben jelennek meg. A mozgás lassú és kimért.

**Miért illik:** A „szál” a gondoskodás folytonosságát fejezi ki, ami Eliza ígérete: diagnosztika, kezelés, otthoni rutin, egy kézben. A motívum közvetlenül a meglévő logóból jön, így az oldal a logóval együtt egy egységes arculatot ad, nem sablont.

### Szakaszok a főoldalon (szöveg a `szovegek.md`-ből, szó szerint)
1. **Fejléc:** logó, menü aranyszál-aláhúzással, telefonszám, „Időpontot kérek” kapszulagomb. Görgetésre összezsugorodik, és áttetsző krém, elmosott háttér kerül alá. Mobilon teljes képernyős menü kattintható telefonnal.
2. **Hero** (7/5): kicker, H1, a teljes bevezető szöveg, **egy gomb** („Megnézem a kezeléseket”), ahogy a felhasználó kérte. Jobbra egy magas fotó (`arckezeles2`), mögötte eltolt púder blokk, a fotó szélén pedig lassan forgó **garanciapecsét** („Elégedettségi garancia · 50% visszatérítés”). Ez az egyetlen magától mozgó elem. Az elemek lépcsőzetesen jelennek meg.
3. **Vélemények:** Fruzsi és Magdi két nagy, editorial idézete, egymáshoz képest eltolva, homokarany idézőjelekkel.
4. **Előnyök:** bal oldalon a cím és a bevezető (sticky), jobbra a 4 előny vékony vonalas ikonokkal. A garancia kiemelve.
5. **Kezelés-ízelítő** (a sablon „Szolgáltatások” szekciójához): Belico, Mesotica és További kezelések rövid kártyái a Kezelések oldal valódi szövegéből, link a Kezelések oldalra. Nem kerül bele kitalált állítás.
6. **Bemutatkozás** (invertált, sötét kakaó szakasz): Eliza nagy portréja (`Eliza.png`) kilóg a szakasz tetején. Mellette a szöveg és a 14+ / 1300+ / 350+ számlálók homokaranyban (kontraszt 6,3), valamint a „Tovább olvasok” gomb.
7. **Folyamat:** 4 lépés vízszintesen az aranyszálra fűzve (mobilon függőlegesen).
8. **Felhívás:** teljes szélességű kép (`arckezeles4`), rárétegzett krém szövegpanellel és „Időpontot kérek” gombbal.
9. **GYIK:** 4 kérdés harmonikában, a nyitás animálva.
10. **Hírlevél:** CSS-sel rajzolt „Arcápolási Kisokos” füzetmakett és az űrlap (csak látványelem).
11. **Időpontkérő** (púder háttér): űrlap, mellette telefon, e-mail és nyitvatartás.
12. **Lábléc** (sötét kakaó): fehér logó, bemutatkozás, elérhetőség, oldalak, adatkezelés, az aranyszál pontban zárul.

**Minőségi minimum:** reszponzív 375 px-ig, látható billentyűzetfókusz, `prefers-reduced-motion` figyelembe vétele, tegező hangvétel (a brief szerint, a skill alapértelmezett magázása helyett), em dash nélkül, magyar „idézőjelek”.

## Megvalósítás
1. **Irány-fájlok:** `.webprojekt/iranyok.json` (1 irány, slug: `aranyszal`), `.webprojekt/plan.md`, state → `directions_complete`.
2. **Projekt felállítása** (`statikus-setup.md` szerint): `images/` mappa. A képeket PowerShell + System.Drawing segítségével 1800 px szélesre méretezem JPG-be (`images/arckezeles1.jpg` stb., `images/eliza.jpg`), a logókat bemásolom `images/logo/` alá. Lesz `.gitignore`, `git init` és első commit, state → `scaffold_complete`.
3. **Prototípus:** 1 sub-agent (opus) a `subagent-utasitas.md` sablonjával, kitöltött `<head>`-del. Kimenet: `koncepcio-1-aranyszal.html`.
4. **Navigátor:** `index.html` egy kártyával, state → `prototypes_complete`.

## Ellenőrzés
- Megnyitom a `koncepcio-1-aranyszal.html`-t a beépített böngészőben, és képernyőképet készítek desktop és mobil (375 px) méretben is. Ellenőrzöm, hogy betöltődnek-e a fontok és az ékezetek, és hogy a képek útvonala jó-e.
- A konzolban nem lehet hiba. Átnézem a GYIK-harmonikát, a mobilmenüt és a horgonylinkeket (#idopont).
- Ha valami hibás, javítom, és a végén megnyitom az `index.html`-t.
