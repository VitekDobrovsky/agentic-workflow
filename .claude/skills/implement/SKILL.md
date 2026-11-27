---
name: implement
description: Implementuje schválený úkol z docs/TASKS.md, u funkce jeden další podúkol: kód, kontroly, code review a přepis návrhů na platný text. Spouští ho jen uživatel.
disable-model-invocation: true
argument-hint: <T-xxx>
---

Implementuj: $ARGUMENTS

Jeden běh implementuje jeden úkol. Pak skonči, aby uživatel commitnul a další úkol začal v nové relaci.

## 1. Výběr úkolu
Když `git status` ukáže necommitnuté změny, zastav se a doporuč uživateli je nejdřív commitnout.

Přečti úkol v `docs/TASKS.md`. Když má podúkoly, vyber další nedokončený, jehož `Závislosti` jsou dokončené, a řekni uživateli který.

Zastav se a řekni uživateli proč, když úkol nebo jeho rodič:
- je ve stavu `navrh`: návrh není schválený, doporuč dokončit `/design`,
- je blokovaný, zrušený nebo dokončený,
- čeká na nedokončené `Závislosti`.

## 2. Příprava
Přečti návrhy úkolu (`grep -rn "návrh T-xxx" docs/` s ID nadřazeného úkolu; podúkol implementuje jen návrhy uvedené ve svém `Rozsah`), kritéria z `Vazby`, dotčené specy, rozhodnutí a související kód. Když úkol používá externí závislost, přečti její dokumentaci odkázanou v `docs/ARCHITECTURE.md`.

## 3. Implementace
Pro každé kritérium z `Vazby` nejdřív napiš test a ověř, že selže. Pak implementuj, dokud test neprojde. Kritérium, které nejde ověřit automatickým testem, ověř postupem z jeho `Ověření` a do `Ověření → Výsledek` zapiš jak. Spusť všechny kontroly ze sekce `Příkazy` v `CLAUDE.md`. Přeskočený test neber jako úspěch. Když kontroly opakovaně selhávají a příčina není jasná, zastav se a řekni to uživateli.

Když zjistíš, že je návrh špatně, zastav se a domluv změnu s uživatelem. Uprav návrh ve specu. Rozhodnutí ve stavu `Platí` nepřepisuj, přidej nové podle `docs/DECISIONS.md`.

## 4. Review
Spusť `/code-review` a oprav potvrzené nálezy. Pak znovu spusť kontroly.

## 5. Dokumentace
- Návrhy, které úkol implementoval, přepiš na platný text. U podúkolu jsou to návrhy z jeho `Rozsah`.
- Vyplň `Ověření` a úkol přepni na `dokonceno`.

Když byl tohle poslední podúkol, zkontroluj, že v dokumentaci projektu nezůstal žádný návrh nadřazeného úkolu. Požadavky funkce přepni na `platí` a nadřazený úkol na `dokonceno`.

## 6. Závěr
Uveď, co je hotové, výsledky kontrol a co zůstalo otevřené. Doporuč commit. Když zbývají podúkoly, řekni, že další spustí `/implement T-xxx` v nové relaci.
