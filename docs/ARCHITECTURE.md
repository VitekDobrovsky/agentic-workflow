# Architektura projektu

Přehled toho, jak projekt funguje uvnitř. Soubor se načítá v každém sezení, proto je krátký. Jak funguje jednotlivá komponenta, popisuje její dokument v `components/`.

## Přehled

<Stručný popis a diagram hlavních částí.>

## Komponenty

Kde je komponenta v kódu a kde je její dokument. Komponenta, která je zatím jen navržená, má u názvu značku `(návrh, T-xxx)`.

| Komponenta | Kód | Dokument |
|---|---|---|
| <název> | `<cesta>` | [<komponenta>](components/<komponenta>.md) |

## Toky mezi komponentami

<Hlavní toky přes víc komponent a data, která si komponenty předávají. Tok uvnitř jedné komponenty patří do jejího dokumentu.>

## Externí závislosti

Služby, API a systémy mimo projekt. U každé: co projekt používá nebo poskytuje, odkaz na její dokumentaci a jak s ní projekt pracuje: limity, opakování, mapování na vlastní stavy a reakce na chyby a výpadky.

- <název> ([dokumentace](<odkaz>)): <jak s ní projekt pracuje>.

## Konfigurace

<Co se nastavuje pro konkrétní prostředí nebo nasazení. Podrobnosti jsou v dokumentech komponent.>

## Otevřené otázky

- <Co ještě není rozhodnuté.>
