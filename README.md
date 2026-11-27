> **Šablona workflow.** Dává projektu jednotná pravidla a dokumentaci pro práci s Claude Code.
>
> 1. Dostaň obsah tohoto repa do repa projektu jedním ze dvou způsobů. Oba do `.claude/workflow/sync-point` zapíšou hash commitu šablony.
>    - Na GitHubu stáhni **Code → Download ZIP** a rozbal ho do repa projektu.
>    - Z klonu šablony spusť `git archive HEAD | tar -x -C <cesta k projektu>`.
> 2. V Claude Code spusť `/setup-workflow <název projektu>`.
> 3. Vyber, co chceš vyplnit: `CLAUDE.md` s tímto README, `docs/REQUIREMENTS.md`, `docs/ARCHITECTURE.md` se specy. Soubory se vyplňují v tomhle pořadí, požadavky jsou volitelné. Claude se ptá, ukáže návrh a zapíše ho až po tvém schválení.
>
> Změny chování projektu se potom navrhují přes `/design <téma>`. Schválený úkol implementuje `/implement <T-xxx>`, jeden podúkol v jedné relaci. Nové změny šablony přenese do projektu `/update-workflow`: u každého commitu se zeptá, jestli ho chceš převzít. Potřebuje připojený GitHub MCP, nebo `gh` CLI. Sdílená pravidla workflow jsou v `.claude/workflow/RULES.md`, projekt je nemění. Commity dělá člověk. Skill `/setup-workflow <název projektu>` tuhle poznámku odstraní.

# <projekt>

<Jedna nebo dvě věty: co projekt dělá.>

## Spuštění

<Co je potřeba nainstalovat a jak projekt spustit.>

## Dokumentace

- `CLAUDE.md`: pravidla a příkazy pro práci v projektu.
- `.claude/workflow/RULES.md`: sdílená pravidla workflow.
- `docs/REQUIREMENTS.md`: co projekt musí umět.
- `docs/ARCHITECTURE.md`: přehled projektu, seznam speců a externí závislosti.
- `docs/specs/`: jak fungují části projektu, funkce a toky.
- `docs/DECISIONS.md`: důvody rozhodnutí.
- `docs/TASKS.md`: aktuální práce.
