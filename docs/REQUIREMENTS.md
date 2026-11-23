# Požadavky

Co projekt musí umět. Jak to dělá, popisují `ARCHITECTURE.md` a `components/`, proč `DECISIONS.md`, práci `TASKS.md`.

- Nadpis záznamu je pouze ID (`## FR-001`, `## NFR-001`); název je v poli `Název`.
- Nové ID = nejvyšší existující ID stejného typu + 1. ID nepřečíslovávej a nepoužívej znovu.
- Akceptační kritéria jsou pod svým požadavkem (`AC-001.1`) a nemají vlastní stav. Každý FR má aspoň jedno. Kritérium má podmínky, očekávaný výsledek a konkrétní způsob ověření.
- NFR musí jít změřit: hodnota a podmínky měření. Když je měření v popisu, kritérium nepotřebuje. Hodnota bez podmínek měření je otevřená otázka, ne požadavek.
- Stavy: `návrh` → `schváleno` → `platí`; později `nahrazeno FR-xxx` nebo `zrušeno` s důvodem. `schváleno` znamená, že to kód ještě nedělá. `platí` znamená, že kritéria jsou ověřená v dokončeném úkolu.
- Hodnota, která se liší podle prostředí nebo nasazení, v požadavku není, je v konfiguraci: „konfigurovatelné, výchozí X“. Kritérium uvede, s jakou hodnotou se ověřuje.
- Požadavek, který projekt přebírá z dokumentace externí závislosti, na ni odkáže a nekopíruje ji.
- Oprava chyby ani refaktoring nový požadavek nezakládají.

## Vzor záznamu (není požadavek, nevyčerpává ID)

```markdown
## FR-001

- Název: Stručný lidský název.
- Popis: Co projekt dělá z pohledu uživatele nebo jiného systému.
- Původ: Kdo nebo co požadavek vzneslo (uživatel, T-xxx, D-xxx).
- Stav: návrh
- Schváleno: (po schválení) RRRR-MM-DD, kdo.
- AC:
  - AC-001.1: Podmínky: výchozí stav nebo vstup. Výsledek: pozorovatelné chování. Ověření: test, postup nebo měření.

## NFR-001

- Název: Stručný lidský název.
- Popis: Měřitelná vlastnost: hodnota a podmínky měření.
- Původ: Kdo nebo co požadavek vzneslo.
- Stav: návrh
- Schváleno: (po schválení) RRRR-MM-DD, kdo.
- AC: (jen když měření není v popisu)
```

## Mimo rozsah

- <Co projekt výslovně nedělá.>

## Předpoklady

- <Neověřené vstupy, na kterých požadavky stojí. Nejsou to požadavky.>

## Záznamy
