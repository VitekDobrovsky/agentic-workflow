# Úkoly projektu

Požadavky jsou v `REQUIREMENTS.md`, popis projektu v `ARCHITECTURE.md` a `components/`, důvody rozhodnutí v `DECISIONS.md`. Otevřené otázky žijí v `ARCHITECTURE.md`.

- Nadpis záznamu je pouze ID (`## T-001`); název je v poli `Název`.
- Nové ID = nejvyšší existující ID + 1. ID nepřečíslovávej a nepoužívej znovu.
- Úkol, který závisí čistě na práci člověka, má za ID písmeno H (`T-001H`).
- Pořadí v souboru není závislost; závislosti jsou pouze v poli `Závislosti`.
- Implementační úkol má ve `Vazby` kritéria `AC-xxx.y`, která splní. Oprava chyby nebo refaktoring odkazuje na kritérium, které oprava splní, nebo nemá vazbu. Ostatní úkoly odkazují na `D-xxx`, nebo nemají vazbu.
- `dokonceno` vyžaduje vyplněné pole `Ověření` se skutečným výsledkem. Úkol, který měnil chování komponenty, má upravený její dokument a jeho značky `návrh (T-xxx)` jsou přepsané na platný text.
- Funkce z `/large-feature` má nadřazený úkol s `Typ: funkce`. Podúkoly mají pole `Rodič`. Nadřazený úkol je `dokonceno`, až když v dokumentaci projektu nezůstala žádná jeho značka `návrh` a jeho požadavky jsou ve stavu `platí`.
- Blokovaný úkol má důvod a podmínku odblokování; zrušený zachová důvod a jeho značky `návrh` se smažou.
- Dokončené a zrušené úkoly zůstávají v tomto souboru.

## Vzor záznamu (není úkol, nevyčerpává ID)

```markdown
## T-001

- Název: Stručný lidský název.
- Cíl: Pozorovatelný výsledek.
- Rodič: T-xxx, nebo žádný.
- Vazby: AC-xxx.y, D-xxx, nebo žádné.
- Rozsah: Co se mění; co je výslovně mimo úkol.
- Závislosti: T-xxx, nebo žádné.
- Riziko: Hlavní relevantní riziko.
- Hotovo když: Kritéria z `Vazby` jsou ověřená; případné další podmínky.
- Ověření:
  - Plán: Jaké kontroly se provedou a jak.
  - Výsledek: (vyplnit po provedení) revize, příkaz/postup, výstup,
    prostředí, neprovedené kontroly, odchylky.
- Stav: nezahajeno
- Poznámky: (volitelné) důvod blokace/zrušení, odkaz na akceptaci.
```

## Vzor nadřazeného úkolu funkce

```markdown
## T-010

- Název: Stručný lidský název funkce.
- Typ: funkce
- Požadavky: FR-xxx, NFR-xxx.
- Návrhy: Všechna místa se značkou `návrh (T-010)`, např.
  `docs/components/<komponenta>.md#<sekce>` a rozhodnutí D-xxx.
- Rizika: Každé relevantní riziko ze sekce `Rizika` v `CLAUDE.md` → AC-xxx.y,
  nebo „netýká se“ s důvodem.
- Podúkoly: T-xxx (vznikají po schválení).
- Stav: nezahajeno
- Poznámky: (volitelné)
```

## Záznamy
