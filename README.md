# IDiS RT

**IDiS RT** (`IDiS.exe`) je runtime aplikácia firmy **Ineltech** diagnostického a vizualizačného systému
**IDiS**. Komunikuje so zariadením cez sériový (COM) port a zobrazuje projekt vytvorený v aplikácii
[**IDiS Designer**](https://github.com/tfeeee/Ineltech-IDiS_Designer).

Tento repozitár slúži na **distribúciu inštalačných balíkov a automatických aktualizácií** IDiS RT
pre zaškolený personál.

## Hlavné funkcie

- komunikácia so zariadením cez sériový COM port,
- zobrazenie obrazoviek (HMI) projektu a aktuálnych hodnôt,
- grafy priebehov v reálnom čase,
- história a záznam udalostí zariadenia,
- systémové zobrazenie pre servisné účely,
- automatická kontrola a inštalácia aktualizácií z GitHub Releases vrátane zoznamu zmien.

## Systémové požiadavky

- Windows 10 alebo novší (32-bitová aplikácia, beží aj na x64),
- administrátorské práva na inštaláciu,
- voľný sériový port (fyzický alebo USB–COM prevodník) na pripojenie zariadenia,
- prístup na internet pre automatické aktualizácie.

## Inštalácia

1. Otvorte stránku [Releases](https://github.com/tfeeee/Ineltech-IDiS/releases/latest).
2. Stiahnite súbor `IDiS-RT-<verzia>-internal-setup.exe`.
   Voliteľne overte jeho kontrolný súčet podľa priloženého súboru `.sha256`.
3. Spustite inštalátor a postupujte podľa sprievodcu. Voliteľne môžete vytvoriť zástupcu na ploche.

Predvolený inštalačný priečinok: `C:\Program Files (x86)\Ineltech\IDiS RT`

IDiS RT je vždy **samostatná inštalácia**. Inštalátor IDiS Designera ho v prípade potreby stiahne
z tohto repozitára a nainštaluje automaticky. IDiS RT je možné nainštalovať aj samostatne, bez Designera.

## Automatické aktualizácie

Aktualizácie sa spúšťajú zo **systémového menu okna** aplikácie (kliknutie na ikonu v titulku okna
alebo `Alt+Medzerník`) položkou **„Skontrolovať aktualizácie...“**.

- Aplikácia porovná nainštalovanú verziu s najnovším releasom v tomto repozitári.
- Pred inštaláciou zobrazí **zoznam zmien (changelog)** novej verzie.
- Stiahnutý balík sa overí kontrolným súčtom SHA-256 a až potom sa spustí inštalácia.

Zoznam zmien každej verzie je tiež priložený pri releasi ako súbor `IDiS-RT-<verzia>-changes.md`.

## Používateľské dáta a nastavenia

Nastavenia a dáta sa ukladajú pre každého používateľa Windows samostatne:

| Obsah | Umiestnenie |
|---|---|
| Nastavenia RT | `%LOCALAPPDATA%\Ineltech\IDiS\RT\IDiS.ini` |
| Hlavičky udalostí / histórie (voliteľné) | `%LOCALAPPDATA%\Ineltech\IDiS\RT\IDiSHiEV.con`, `IDiSHiCH.con` |
| Diagnostické logy | `%LOCALAPPDATA%\Ineltech\IDiS\RT\Logs` |
| Dočasné súbory | `%LOCALAPPDATA%\Ineltech\IDiS\RT\Temp` |
| Stiahnuté aktualizácie | `%LOCALAPPDATA%\Ineltech\IDiS\Updates\RT` |

Pri spustení sa chýbajúce položky nastavení doplnia z predvolenej šablóny dodanej s inštaláciou.
Existujúce hodnoty sa nikdy neprepisujú.

### Import nastavení zo staršej verzie

Ak sa pôvodný `IDiS.ini` nachádza pri EXE súbore staršej inštalácie, nastavenia sa naimportujú automaticky.
Z iného umiestnenia ich môžete naimportovať príkazom (spustite ako dotknutý používateľ, ideálne pred
prvým bežným spustením RT):

```powershell
& "C:\Program Files (x86)\Ineltech\IDiS RT\IDiS.exe" --import-settings "C:\cesta\k\starej\IDiS.ini"
```

Import nemení existujúce hodnoty ani pôvodný INI súbor.

## Odinštalovanie

Cez **Nastavenia → Aplikácie** (alebo Ovládací panel) odinštalujte položku **IDiS RT**.
Ak používate IDiS Designer, ten bez nainštalovaného RT nedokáže spúšťať projekty.
Používateľské dáta v `%LOCALAPPDATA%\Ineltech\IDiS` zostávajú zachované.

## Podpora

Aplikácia je určená pre interné použitie zaškoleným personálom. S problémami sa obracajte na
zodpovednú osobu vo firme Ineltech.
