<!--
Jak zapsat návrh (do nového specu tento komentář nekopíruj).
Co ještě není v kódu, nese `návrh T-xxx` s ID úkolu, který to implementuje. Tvar je všude stejný, aby šla všechna místa úkolu najít přes `grep -rn "návrh T-xxx" docs/`:
- nový spec: nadpis `# <Název> (návrh T-xxx)`,
- nová sekce: `## <Název> (návrh T-xxx)`,
- změna existující sekce: blok pod platným textem `> **návrh T-xxx:** …`, odstranění `> **návrh T-xxx:** odstranit.`,
- druhý návrh ke stejné sekci přidá vlastní blok a uvede `závisí na T-yyy`.
-->

# <Název>

<Jedna věta: co spec pokrývá a co do něj nepatří.>

Kód: `<cesta>`. Požadavky: <FR-xxx, NFR-xxx>.

## Jak funguje

<Jak to funguje.>

## Data

<Co se ukládá, kde a jak dlouho.>

## Stavy

<Stavy a přechody mezi nimi.>

## Chyby a výpadky

<Co se stane při chybě, výpadku nebo zpomalení závislosti a při restartu. Projdi i situace ze sekcí `Principy` a `Rizika` v `CLAUDE.md`.>

## Konfigurace

<Co se nastavuje pro konkrétní prostředí nebo nasazení.>
