# Com afegir un projecte nou al repo UB

> Instruccions per a mi i per a qualsevol assistent (p. ex. Claude Code) que treballi en una pràctica nova de la UB.
> **Regla:** cap pràctica de la uni té repo públic propi. Tot el que sigui públic viu dins de `Joanfmir/UB`.

## Regles

1. **Ubicació:** `UB/<ASSIGNATURA>/<nom-del-projecte>/`
   - `<ASSIGNATURA>` = sigles en majúscules (`IA`, `TNUI`, `ED`, `PIS`, `PAE`, `VA`, `DS`...). Si la carpeta no existeix, es crea.
   - `<nom-del-projecte>` = kebab-case descriptiu, p. ex. `practica2-arbres-binaris`.
2. **Res de repos públics separats.** Si un projecte té (o ha tingut) repo propi a GitHub, s'integra aquí conservant l'historial i el repo original es posa **privat** (no s'esborra, queda com a còpia).
3. **README:** cada projecte té el seu `README.md`, i s'afegeix una fila/enllaç a la taula del [README.md](README.md) arrel.
4. **Sense secrets ni fitxers pesats:** res de `.env`, claus, ni datasets > 50 MB (fes servir `.gitignore` o enllaça la font).

## Procediment

### A) Projecte nou, sense repo propi
```bash
cd UB
mkdir -p <ASSIGNATURA>/<nom-del-projecte>
# ... copiar/crear els fitxers ...
# actualitzar la taula del README.md arrel
git add . && git commit -m "Afegeix <ASSIGNATURA>/<nom-del-projecte>"
git push
```

### B) Projecte que ja té repo propi a GitHub (públic o privat)
```bash
cd UB
git subtree add --prefix=<ASSIGNATURA>/<nom-del-projecte> https://github.com/Joanfmir/<REPO>.git main
# actualitzar la taula del README.md arrel i fer commit
git push
gh repo edit Joanfmir/<REPO> --visibility private --accept-visibility-change-consequences
```

`git subtree add` (sense `--squash`) manté tot l'historial de commits del repo original.

### Revisió periòdica
Comprovar que no hi ha cap pràctica de la uni pública fora d'aquest repo:
```bash
gh repo list Joanfmir --visibility public --json name,description
```
Qualsevol repo d'assignatura que surti (a part de `UB`) s'ha d'integrar seguint el pas B.
