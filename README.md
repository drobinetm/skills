# skills

Colección de skills de Claude Code. Cada skill vive en su propia carpeta bajo `skills/`, con su `SKILL.md` (entrada del skill) y su propio `README.md` (qué hace, cómo instalarlo, contenido).

## Skills disponibles

| Skill | Descripción |
|-------|-------------|
| [venuenexa-guide](skills/venuenexa-guide/README.md) | Guía de sesión por rol para el proyecto VenueNexa (Ingenius): tareas PV1-Tnn, bitácora y horas. |

## Instalación

Copia (o enlaza) la carpeta del skill que quieras a tu directorio de skills:

```bash
# Global (todos los proyectos)
cp -r skills/<nombre-del-skill> ~/.claude/skills/

# Por proyecto
cp -r skills/<nombre-del-skill> <repo>/.claude/skills/
```

## Estructura

```
skills/
  <nombre-del-skill>/
    SKILL.md        # frontmatter (name, description) + flujo
    README.md       # documentación propia del skill
    references/     # material que se lee bajo demanda
```

## Añadir un skill nuevo

1. Crea `skills/<nombre>/` con `SKILL.md` y `README.md`.
2. Añade una fila a la tabla de este README.

## Licencia

MIT — ver [LICENSE](LICENSE).
