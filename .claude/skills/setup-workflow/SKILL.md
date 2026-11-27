---
name: setup-workflow
description: Po krocích a se schválením uživatele vyplní CLAUDE.md, docs/REQUIREMENTS.md, docs/ARCHITECTURE.md se specy nového nebo existujícího projektu. Spouští ho jen uživatel.
disable-model-invocation: true
argument-hint: <název projektu>
---

Pracuj na projektu: $ARGUMENTS

Neměň kód. Nic nezapisuj, dokud uživatel neschválí návrh daného kroku.

## 1. Příprava
Přečti `CLAUDE.md`, `.claude/workflow/RULES.md`, `README.md`, `docs/REQUIREMENTS.md`, `docs/ARCHITECTURE.md`, `docs/specs/`, `docs/DECISIONS.md` a `docs/TASKS.md`. Když v repu už je kód, projdi ho.

Zjisti stav kroků:
- `CLAUDE.md` a `docs/ARCHITECTURE.md` jsou šablona, když v nich zůstaly placeholdery `<...>`.
- `docs/REQUIREMENTS.md` je prázdný, když pod `## Záznamy` nic není.
- Specy chybí, když v `docs/specs/` je jen `_template.md`.

## 2. Výběr
Stručně uživateli řekni, co skill dělá, a ukaž mu stav všech souborů. Zeptej se, co chce udělat: vyplnit `CLAUDE.md`, `docs/REQUIREMENTS.md`, `docs/ARCHITECTURE.md` se specy, nebo víc z nich.

Kroky mají pevné pořadí: `CLAUDE.md`, `docs/REQUIREMENTS.md`, `docs/ARCHITECTURE.md`. Krok `docs/REQUIREMENTS.md` je volitelný. Ostatní kroky nejde udělat, dokud není hotový předchozí povinný krok. Když chybí, řekni to uživateli a nabídni, že ho uděláš jako první. Když chce víc kroků, řekni mu, v jakém pořadí půjdou, a dělej je po jednom.

## 3. Postup každého kroku
1. **Otázky.** Ptej se po menších skupinách a počkej na odpovědi. Nevymýšlej si je. Co už jasně plyne z kódu nebo dokumentace, jen ověř.
2. **Návrh.** Ukaž uživateli konkrétní obsah. U vyplněného souboru nic nepřepisuj, navrhni konkrétní změny a zachovej to, co v něm platí.
3. **Doptání.** Co se při návrhu ukázalo nejasné, dořeš s uživatelem a návrh uprav.
4. **Schválení.** Zastav se a počkej na výslovné schválení. Dotaz ani dílčí souhlas nejsou schválení.
5. **Zápis.** Zapiš schválený obsah, řekni uživateli, co je hotové, a přejdi na další vybraný krok.

## 4. Krok CLAUDE.md
Zjisti:
- účel projektu a co do něj nepatří,
- kde běží a na čem,
- stack a příkazy pro testy, typy, lint a formát,
- klíčová rozhodnutí a pojmy specifické pro projekt,
- principy, které musí splnit každý návrh (například chování bez internetu, co patří do konfigurace, bezpečnost, kompatibilita),
- hlavní rizika: konkrétní situace, kde může projekt selhat.

Navrhni:
- `CLAUDE.md`: vyplň všechny sekce s placeholdery a odstraň poznámku o šabloně. Import `@.claude/workflow/RULES.md` na konci zachovej. V existujícím projektu ho doplň, pokud chybí.
- `README.md`: vyplň ho a odstraň poznámku o šabloně.
- `.claude/settings.json`: příkazy ze sekce `Příkazy` přidej do `permissions.allow`.

`.claude/workflow/RULES.md` neměň, jsou to sdílená pravidla šablony.

## 5. Krok REQUIREMENTS.md
Zjisti:
- klíčové chování projektu pro uživatele a jiné systémy,
- nefunkční požadavky, které jsou pro projekt důležité a jdou změřit,
- co je mimo rozsah a na jakých předpokladech požadavky stojí.

Navrhni jen klíčové chování, ne vyčerpávající seznam. Požadavky a kritéria piš podle pravidel v `docs/REQUIREMENTS.md`.

Po schválení dostanou požadavky, které kód už splňuje, stav `platí`, ostatní `schváleno`.

## 6. Krok ARCHITECTURE.md
Zjisti:
- hlavní části projektu a toky mezi nimi, kde jsou v kódu a data, která si předávají,
- jak funguje každá část nebo tok: kroky, data, stavy, chyby a výpadky,
- co se nastavuje pro konkrétní prostředí nebo nasazení,
- jaké externí služby, API a systémy projekt používá nebo komu něco poskytuje a jak s nimi pracuje,
- co se stane, když externí závislost vypadne nebo je pomalá.

Navrhni:
- `docs/ARCHITECTURE.md`: krátký přehled s diagramem, tabulku speců a externí závislosti s odkazem na jejich dokumentaci. Co zůstalo nejasné, dej do `Otevřené otázky`.
- Specy v `docs/specs/` podle `_template.md`: pro každou část projektu, funkci nebo tok, který stojí za vlastní popis. Specy se nesmí překrývat.

Před schválením nech návrh zkontrolovat agentem `design-critic`. Prompt musí obsahovat celý návrh. Jednoznačné nálezy zapracuj. O těch, které mění rozhodnutí nebo rozsah, rozhodne uživatel. Uživateli shrň změny po kritice.

## 7. Závěr
Na konci uveď změněné soubory a co zůstalo otevřené.
