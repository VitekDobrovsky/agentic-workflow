# Rozhodnutí

Proč je projekt navržený tak, jak je, a co jsme zamítli. Aktuální popis je v `ARCHITECTURE.md`, krátký seznam pevných pravidel v `CLAUDE.md`.

- Záznamy se nepřepisují. Když se rozhodnutí změní, přidá se nový záznam a u starého se změní jen stav.
- Výjimkou je záznam ve stavu `Návrh (T-xxx)` z `/large-feature`. Do schválení funkce se smí upravit, po schválení se přepne na `Platí`. Když se funkce zruší, záznam se smaže.
- Nejnovější záznam je na konci.

Šablona:

```markdown
## D-000: Název
- **Datum:** RRRR-MM-DD
- **Stav:** Návrh (T-000) | Platí | Nahrazeno D-000
- **Rozhodnutí:** Co platí.
- **Důvod:** Proč.
- **Zamítnuto:** Jaké varianty a proč.
```
