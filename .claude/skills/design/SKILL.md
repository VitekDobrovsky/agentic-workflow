---
name: design
description: Navrhne změnu chování projektu, malou i větší funkci: rozsah, požadavky, návrh ve specech, kritiku, schválení uživatelem a úkol k implementaci. Kód nemění. Spouští ho jen uživatel.
disable-model-invocation: true
argument-hint: <téma>
---

Navrhuješ: $ARGUMENTS

Neměň kód. Návrh zapisuj rovnou na místa, kde bude platit, jako `návrh T-xxx` podle `docs/specs/_template.md`. Otázky uživateli klaď po jedné a ke každé řekni, co doporučuješ a proč. Nevymýšlej si odpovědi.

## 1. Příprava
Přečti tabulku speců v `docs/ARCHITECTURE.md`, specy, které se tématu týkají, `docs/REQUIREMENTS.md`, `docs/DECISIONS.md`, `docs/TASKS.md` a související kód. Když se změna dotkne externí závislosti, přečti její dokumentaci odkázanou v `docs/ARCHITECTURE.md`.

## 2. Rozsah
Zeptej se, co má změna dělat a co je mimo rozsah. Pak urči velikost a ověř ji s uživatelem:
- **Funkce**: mění se chování, které vidí uživatel nebo jiný systém. Má požadavky.
- **Malá změna**: mění se jen chování uvnitř projektu. Požadavky nemá.

Když se během návrhu ukáže, že malá změna mění chování, které je vidět navenek, řekni to uživateli a pokračuj jako funkce.

Malá změna, která se netýká sekcí `Rizika` a `Principy` v `CLAUDE.md` ani externí závislosti, jde zkráceně:
1. Ukaž celý návrh najednou: změny speců, případná rozhodnutí a úkol s `Hotovo když` a `Ověření → Plán`. Ptej se jen na to, co z dokumentace a kódu neplyne. Když se ukáže, že se změna některé z těch oblastí týká, řekni to a pokračuj plnou cestou.
2. Zastav se a počkej na výslovné schválení. Dotaz ani dílčí souhlas nejsou schválení. Do té doby nic nezapisuj.
3. Zapiš návrhy podle `docs/specs/_template.md`, rozhodnutí ve stavu `Platí` a úkol ve stavu `nezahajeno` s datem a tím, kdo návrh schválil, v `Poznámky`. Pokračuj krokem 9.

Jinak založ úkol ve stavu `navrh` podle vzoru v `docs/TASKS.md`: u funkce nadřazený úkol, u malé změny běžný úkol. Všechny návrhy nesou jeho ID.

## 3. Požadavky (jen funkce)
Navrhni požadavky a jejich akceptační kritéria podle pravidel v `docs/REQUIREMENTS.md` a po odsouhlasení je zapiš ve stavu `návrh`.

Projdi sekci `Rizika` v `CLAUDE.md`. Každé relevantní riziko pokryj kritériem a zapiš do pole `Rizika` nadřazeného úkolu. Riziko, které se funkce netýká, tam uveď s důvodem.

## 4. Návrh po částech
Projdi s uživatelem postupně části projektu a jejich odpovědnosti, tok a pořadí kroků, data, stavy, chyby a výpadky, chování podle sekce `Principy` v `CLAUDE.md` a konfiguraci. Části, kterých se změna netýká, vynech. Ke každé části se ptej na to, co z dokumentace a kódu neplyne. Nepiš celý návrh najednou.

- Když se volí mezi řešeními, ukaž varianty s kompromisy a doporuč jednu. Vybranou zapiš do `docs/DECISIONS.md` jako návrh i se zamítnutými variantami a důvody. Zapisuj jen rozhodnutí, u kterých se dá později ptát, proč ne jinak.
- Novou nebo změněnou externí závislost zapiš jako návrh do `Externí závislosti` v `docs/ARCHITECTURE.md`. Jak s ní projekt zachází, zapiš do specu toku, který ji používá.
- Odsouhlasenou část zapiš jako návrh do dotčeného specu. Když se téma překrývá s existujícím specem, navrhni rozšířit ten, nebo posunout hranici mezi nimi. Nový spec vznikne podle `_template.md` a dostane řádek v `docs/ARCHITECTURE.md`. Když přejmenuješ nebo smažeš sekci, oprav odkazy na ni v `docs/`.

## 5. Kritika
Nech návrh zkontrolovat agentem `design-critic`. Prompt musí obsahovat všechny návrhy úkolu včetně rozhodnutí, požadavky a kritéria a změny externích závislostí. Jednoznačné nálezy zapracuj. O těch, které mění rozhodnutí nebo rozsah, rozhodne uživatel.

## 6. Schválení návrhu
Shrň uživateli návrh (všechna místa návrhu), požadavky, změny po kritice a otevřené otázky. Zastav se a počkej na výslovné schválení. Dotaz ani dílčí souhlas nejsou schválení.

## 7. Rozdělení práce
Malá změna, která se vejde do jedné relace, zůstane jedním úkolem. Jinak z úkolu udělej nadřazený úkol podle vzoru v `docs/TASKS.md` a navrhni podúkoly s polem `Rodič`:
- Podúkol je svislý řez: dá se samostatně ověřit a vejde se do jedné relace. Nerozděluj práci po vrstvách.
- Každé kritérium funkce pokryje aspoň jeden podúkol.
- Každý návrh patří právě jednomu podúkolu, který ho uvede v `Rozsah` (`<spec>.md#<sekce>`). Návrh, který se do jednoho podúkolu nevejde, rozděl na víc bloků.
- Co musí být hotové dřív, patří do `Závislosti`.

Ukaž uživateli podúkoly, jejich kritéria a závislosti. Zeptej se, jestli rozdělení není moc hrubé nebo jemné a jestli sedí závislosti. Počkej na schválení.

## 8. Zápis
Zapisuj v tomto pořadí:
1. podúkoly, nebo u úkolu bez podúkolů `Hotovo když` a `Ověření → Plán`,
2. požadavky přepni na `schváleno` s datem a jménem,
3. rozhodnutí úkolu v `docs/DECISIONS.md` přepni na `Platí`,
4. úkol přepni z `navrh` na `nezahajeno` a do `Poznámky` zapiš datum a kdo návrh schválil. Tím je úkol uvolněný k implementaci.

## 9. Závěr
Uveď změněné soubory, úkol a co zůstalo otevřené. Řekni, že implementaci spustí `/implement T-xxx`.
