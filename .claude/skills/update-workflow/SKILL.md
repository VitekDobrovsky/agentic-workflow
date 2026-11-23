---
name: update-workflow
description: Projde nové commity šablony agentic-workflow a po jednom je se schválením uživatele převezme do projektu, nebo přeskočí. Spouští ho jen uživatel.
disable-model-invocation: true
---

Přenášíš změny šablony `<vlastník>/agentic-workflow` (větev `main`) do tohoto projektu. Projekty si workflow upravují, proto se nic nepřepisuje automaticky. O každém commitu rozhoduje uživatel.

Neměň kód projektu. Nic nezapisuj, dokud uživatel neschválí plán daného commitu.

## 1. Příprava
Přečti `.claude/workflow/sync-point`. Obsahuje hash posledního commitu šablony, o kterém je rozhodnuto, ať byl převzatý, nebo přeskočený.

- Když je tohle repo samotná šablona `agentic-workflow`, řekni to uživateli a skonči.
- K šabloně přistupuj přes GitHub MCP, nebo přes `gh` CLI. Když není dostupné ani jedno, řekni to uživateli a skonči.
- Když soubor chybí nebo obsahuje `$Format:%H$`, šablona nebyla nainstalovaná přes ZIP ani `git archive`. Dohledej sync point:
  1. Přes GitHub projdi poslední commity na `main` šablony, od nejnovějšího.
  2. Porovnej s nimi sdílené soubory projektu: `.claude/workflow/RULES.md`, `.claude/skills/*` a `.claude/agents/*`.
  3. Když se všechny shodují s některým commitem, ukaž ho uživateli a po schválení zapiš jeho hash. Když se nic neshoduje, řekni uživateli, které soubory se liší, a zeptej se, který commit zapsat.

Přes GitHub najdi commity na `main` šablony novější než sync point a seřaď je od nejstaršího. Když sync point v historii `main` není, řekni to uživateli a zeptej se, od kterého commitu pokračovat. Když nové commity nejsou, řekni, že je projekt aktuální, a skonči.

Uživateli ukaž seznam nových commitů: hash, datum, zpráva.

## 2. Postup každého commitu
Commity zpracovávej po jednom a v pořadí.

1. **Shrnutí.** Přečti zprávu a diff commitu. Uživateli stručně řekni, co commit mění a proč, a jak se to má k aktuálnímu stavu projektu. Upozorni, když projekt dotčenou část upravil, nebo když commit staví na změně, která v projektu není. Drobné commity bez vlivu na chování (překlepy, formulace) můžeš nabídnout společně.
2. **Rozhodnutí.** Zeptej se, jestli commit převzít, nebo přeskočit. Když přeskočit, pokračuj bodem 6.
3. **Otázky.** Co z diffu a projektu neplyne a mění výsledek, dořeš s uživatelem. Nevymýšlej si odpovědi. Úpravy projektu zachovej, pokud uživatel neřekne jinak.
4. **Plán.** Navrhni konkrétní změny souborů v projektu. Když commit mění šablonu souboru, který projekt vyplnil (`CLAUDE.md`, `README.md`, `docs/*`), navrhni úpravu vyplněného obsahu a zachovej, co v něm platí. Když commit mění strukturu souboru s daty projektu (například záznamů v `docs/TASKS.md`), navrhni i převod existujících záznamů. Když commit nějaký dokument nebo adresář ruší, navrhni převod jen rozpracovaného obsahu a hotový obsah, který už je jinde, navrhni smazat. Co nejde z existujícího obsahu odvodit, nedoplňuj, zeptej se.
5. **Schválení a zápis.** Zastav se a počkej na výslovné schválení. Dotaz ani dílčí souhlas nejsou schválení. Pak plán proveď.
6. **Posun.** Zapiš hash commitu do `.claude/workflow/sync-point` a řekni uživateli, co je hotové.

Když commit mění tenhle skill, nová verze platí až od příštího spuštění. Řekni to uživateli.

## 3. Závěr
Nic necommituj. Na konci uveď převzaté a přeskočené commity, změněné soubory a aktuální sync point.
