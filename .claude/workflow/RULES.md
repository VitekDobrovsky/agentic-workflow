# Pravidla workflow

Sdílená pravidla šablony agentic-workflow. Projekt je nemění, změny přicházejí přes `/update-workflow`. Co je specifické pro projekt, patří do `CLAUDE.md`.

## Názvosloví workflow
- **Projekt**: tohle repo.
- **Externí závislost**: služba, API nebo systém mimo projekt, který projekt používá nebo který používá projekt.

## Dokumentace projektu
Každý fakt je na jednom místě. Soubory si přečti, až když je potřebuješ:
- `docs/REQUIREMENTS.md`: co projekt musí umět (požadavky a akceptační kritéria).
- `docs/ARCHITECTURE.md`: krátký přehled projektu, seznam speců a externí závislosti.
- `docs/specs/<spec>.md`: jak funguje část projektu, funkce nebo tok. Nový spec vychází z `_template.md`, který popisuje i to, jak se ve specu zapisuje návrh. Sekce, které se ho netýkají, vynech. První věta říká, co spec pokrývá a co do něj nepatří, aby se specy nepřekrývaly.
- `docs/DECISIONS.md`: proč. `docs/TASKS.md`: práce.

Fakt, který už je v jiném specu, neopakuj a odkaž na jeho sekci (`<spec>.md#<sekce>`) v textu, kde ho používáš. Když sekci přejmenuješ nebo smažeš, oprav odkazy na ni v `docs/`.

Externí závislost je v `docs/ARCHITECTURE.md` jen s tím, co ji projekt používá nebo co jí poskytuje, a s odkazem na její dokumentaci. Jak s ní projekt zachází uvnitř, tedy limity, opakování, mapování na vlastní stavy a reakce na chyby a výpadky, patří do specu toku, který ji používá. Z její dokumentace nic nekopíruj, odkaž na ni.

Dokumentace popisuje, jak projekt funguje teď. Co ještě není v kódu, je označené jako `návrh`. Jak, popisuje každý soubor sám. Návrh neber jako popis aktuálního chování. Když měníš chování projektu, uprav ve stejné změně i dotčené specy a přepiš své návrhy na platný text. Zastaralý text smaž, historie je v gitu.

## Změna rozhodnutí
Přidej záznam do `docs/DECISIONS.md`. Pokud se tím mění aktuální chování nebo klíčové rozhodnutí, uprav i dotčený spec, `docs/ARCHITECTURE.md` nebo `CLAUDE.md`.

## Návrh a implementace
Změna chování popsaného ve specu nebo změna externí závislosti se navrhuje přes `/design` a implementuje přes `/implement`. Neimplementuj ji bez schváleného návrhu. Oprava, která vrací chování podle specu, a refaktoring jdou bez nich. Opravu chyby začni testem, který chybu zopakuje a selže.

## Jazyk
- Kód a komentáře anglicky.
- Dokumentace česky.

## Git
- Nikdy nic necommituj (ani nepushuj). Commity dělají výhradně lidé.
