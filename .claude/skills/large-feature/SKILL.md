---
name: large-feature
description: Provede návrh a implementaci větší funkce nebo komponenty: požadavky, společný návrh toho, jak bude fungovat, kritiku, schválení uživatelem a implementaci. Spouští ho jen uživatel.
disable-model-invocation: true
argument-hint: <název funkce nebo komponenty>
---

Pracuj na: $ARGUMENTS

Postupuj po krocích. Před schválením návrhu neměň kód. Návrh zapisuj rovnou na místa, kde bude platit, se značkou `návrh` podle sekce `Dokumentace projektu` v `.claude/workflow/RULES.md`.

## 1. Příprava
Přečti `docs/REQUIREMENTS.md`, `docs/DECISIONS.md`, `docs/TASKS.md`, dokumenty dotčených komponent v `docs/components/` a kód, který s tím souvisí. Když se funkce dotkne externí závislosti, přečti její dokumentaci odkázanou v `docs/ARCHITECTURE.md`.

Založ nadřazený úkol funkce v `docs/TASKS.md` podle vzoru v souboru. Všechny značky `návrh` v dalších krocích odkazují na jeho ID a každé místo se značkou zapiš do jeho pole `Návrhy`.

## 2. Co se má udělat
Polož uživateli otázky k tomu, co má funkce dělat a co je mimo rozsah. Nevymýšlej si odpovědi. Pak navrhni požadavky a jejich akceptační kritéria podle pravidel v `docs/REQUIREMENTS.md` a po odsouhlasení je zapiš ve stavu `návrh`.

Projdi sekci `Rizika` v `CLAUDE.md`. Každé relevantní riziko pokryj kritériem a zapiš do pole `Rizika` nadřazeného úkolu. Riziko, které se funkce netýká, tam uveď s důvodem.

## 3. Jak to bude fungovat
1. **Varianty.** Navrhni v konverzaci 2–3 varianty řešení s kompromisy a doporuč jednu. Počkej, až uživatel vybere. Když je jen jedno rozumné řešení, řekni to a varianty nevymýšlej. Vybranou variantu zapiš do `docs/DECISIONS.md` ve stavu `Návrh (T-xxx)` i se zamítnutými variantami a důvody a záznam uveď v poli `Návrhy`.
2. **Návrh po částech.** Projdi s uživatelem postupně komponenty a jejich odpovědnosti, tok a pořadí kroků, data, stavy, chyby a výpadky, chování podle sekce `Principy` v `CLAUDE.md` a konfiguraci. Ke každé části se ptej na to, co z dokumentace a kódu neplyne. Nepiš celý návrh najednou.
3. **Zápis.** Odsouhlasenou část zapiš se značkou `návrh` do dokumentu komponenty. Nová komponenta dostane dokument podle `docs/components/_template.md` a řádek se značkou v `docs/ARCHITECTURE.md`. Novou nebo změněnou externí závislost zapiš se značkou do `Externí závislosti` v `docs/ARCHITECTURE.md`.

## 4. Kritika
Nech návrh zkontrolovat agentem `design-critic`. Prompt sestav z pole `Návrhy` nadřazeného úkolu: obsah všech bloků `návrh` včetně rozhodnutí a požadavky a kritéria funkce. Jednoznačné nálezy zapracuj. O těch, které mění rozhodnutí nebo rozsah, rozhodne uživatel.

## 5. Schválení
Shrň uživateli návrh podle pole `Návrhy`, požadavky, změny po kritice a otevřené otázky. Zastav se a počkej na výslovné schválení. Dotaz ani dílčí souhlas nejsou schválení implementace.

Po schválení:
- požadavky přepni na `schváleno` s datem a jménem,
- rozhodnutí funkce v `docs/DECISIONS.md` přepni na `Platí`,
- rozděl práci na podúkoly s polem `Rodič` a vazbou na kritéria. Každé kritérium funkce pokryj aspoň jedním podúkolem.

## 6. Implementace
Implementuj po podúkolech. Když během práce zjistíš, že je návrh špatně, zastav se a domluv změnu s uživatelem.

Každý podúkol:
- ověří svá kritéria,
- spustí všechny kontroly ze sekce `Příkazy` v `CLAUDE.md` (přeskočený test neber jako úspěch),
- přepíše svoje bloky `návrh` na platný text,
- vyplní `Ověření` a jde do `dokonceno`.

## 7. Uzavření
Spusť `/code-review` a oprav potvrzené nálezy.

Zkontroluj, že v dokumentaci projektu nezůstala žádná značka `návrh` nadřazeného úkolu. Požadavky funkce přepni na `platí` a nadřazený úkol na `dokonceno`.

Nic necommituj. Na konci uveď, co je hotové, výsledky kontrol a co zůstalo otevřené.
