# Architektura projektu

Přehled toho, jak projekt funguje uvnitř. Soubor se načítá v každém sezení, proto je krátký. Podrobnosti popisují specy v `specs/`.

## Přehled

<Stručný popis a diagram hlavních částí projektu a toků mezi nimi. Podrobnosti jsou ve specech, tady na ně jen odkaž.>

## Specy

Co který spec pokrývá a kde je jeho kód. Spec, který je zatím jen navržený, má u názvu `(návrh T-xxx)`.

| Spec | Co pokrývá | Kód |
|---|---|---|
| [<název>](specs/<spec>.md) | <jedna věta> | `<cesta>` |

## Externí závislosti

Služby, API a systémy mimo projekt. U každé jen to, co ji projekt používá nebo co jí poskytuje, a odkaz na její dokumentaci. Jak s ní projekt zachází, popisuje spec toku, který ji používá. Závislost, která je zatím jen navržená, má u názvu `(návrh T-xxx)`, změna existující má pod sebou blok `> **návrh T-xxx:** …`.

- <název> ([dokumentace](<odkaz>)): <co ji projekt používá nebo co jí poskytuje>.

## Otevřené otázky

- <Co ještě není rozhodnuté.>
