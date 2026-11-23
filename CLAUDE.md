> **Šablona workflow.** Tento projekt ještě není nastavený. Než začneš s jinou prací, upozorni uživatele, ať spustí `/setup-workflow <název projektu>`. Skill tuhle poznámku odstraní.

# <projekt>

<Jedna nebo dvě věty: co projekt dělá a co do něj nepatří.>

Architektura projektu: viz @docs/ARCHITECTURE.md
Požadavky: `docs/REQUIREMENTS.md`. Komponenty: `docs/components/`. Důvody rozhodnutí: `docs/DECISIONS.md`. Aktuální práce: `docs/TASKS.md`. Tyto soubory si přečti, až když je potřebuješ.

## Klíčová rozhodnutí (neměnit bez domluvy)
- <Rozhodnutí, která musí agent znát vždy.>

## Principy
- <Pravidla, která musí splnit každý návrh, např. „funguje bez internetu“ nebo „nic specifického pro zákazníka v kódu, vše v konfiguraci“. Podle nich hodnotí návrhy agent `design-critic`.>

## Názvosloví
- <Pojmy, které používá tento projekt.>

## Rizika
- <Konkrétní situace, kde může projekt selhat. Podle nich hodnotí návrhy agent `design-critic`.>

## Stack
- <Jazyk, hlavní knihovny, správa balíčků, kde projekt běží.>

## Příkazy
- Testy: `<příkaz>`
- Typy: `<příkaz>`
- Lint a formát: `<příkaz>`

## Pravidla workflow
@.claude/workflow/RULES.md
