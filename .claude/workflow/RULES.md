# Pravidla workflow

Sdílená pravidla šablony agentic-workflow. Projekt je nemění, změny přicházejí přes `/update-workflow`. Co je specifické pro projekt, patří do `CLAUDE.md`.

## Názvosloví workflow
- **Projekt**: tohle repo.
- **Komponenta**: část projektu s vlastním dokumentem v `docs/components/`.
- **Externí závislost**: služba, API nebo systém mimo projekt, který projekt používá nebo který používá projekt.

## Dokumentace projektu
Každý fakt je na jednom místě:
- `docs/REQUIREMENTS.md`: co projekt musí umět (požadavky a akceptační kritéria).
- `docs/ARCHITECTURE.md`: krátký přehled projektu, seznam komponent a externí závislosti.
- `docs/components/<komponenta>.md`: jak komponenta funguje. Nový dokument vychází z `_template.md`.
- `docs/DECISIONS.md`: proč. `docs/TASKS.md`: práce.

Dokumentace popisuje, jak projekt funguje teď. Co je navržené, ale ještě není v kódu, má značku `návrh` s úkolem:
- nová sekce: `## <Název> (návrh, T-xxx)`,
- změna existující sekce: blok pod platným textem `> **Návrh (T-xxx):** …`, odstranění `> **Návrh (T-xxx):** odstranit.`,
- druhý návrh ke stejné sekci přidá vlastní blok a uvede `závisí na T-xxx`.

Text ve stavu `návrh` neber jako popis aktuálního chování. Když měníš chování komponenty, uprav ve stejné změně i její dokument a přepiš své značky `návrh` na platný text. Zastaralý text smaž, historie je v gitu.

## Změna rozhodnutí
Přidej záznam do `docs/DECISIONS.md`. Pokud se tím mění aktuální chování nebo klíčové rozhodnutí, uprav i dokument dotčené komponenty, `docs/ARCHITECTURE.md` nebo `CLAUDE.md`.

## Větší funkce
Větší funkce a komponenty se navrhují přes `/large-feature`. Neimplementuj je bez schváleného návrhu.

## Jazyk
- Kód a komentáře anglicky.
- Dokumentace česky.

## Git
- Nikdy nic necommituj (ani nepushuj). Commity dělají výhradně lidé.
