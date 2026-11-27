# Rozhodnutí

Proč je projekt navržený tak, jak je, a co jsme zamítli.

- Záznamy se nepřepisují. Když se rozhodnutí změní, přidá se nový záznam a u starého se změní jen stav.
- Výjimkou je záznam ve stavu `návrh T-xxx`. Do schválení návrhu se smí upravit, po schválení se přepne na `Platí`. Když se návrh zruší, záznam se smaže.
- Nejnovější záznam je na konci.

Šablona:

```markdown
## D-000: Název
- **Datum:** RRRR-MM-DD
- **Stav:** návrh T-000 | Platí | Nahrazeno D-000
- **Rozhodnutí:** Co platí.
- **Důvod:** Proč.
- **Zamítnuto:** Jaké varianty a proč.
```
