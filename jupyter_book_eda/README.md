# Publicar el EDA como Jupyter Book en GitHub Pages

Este proyecto genera un sitio web (como `https://<usuario>.github.io/<repo>/intro.html`)
a partir de tu notebook **ya ejecutado**. No re-ejecuta el notebook: usa las salidas y
gráficas guardadas dentro del `.ipynb` (por eso no necesita los CSV en el repositorio).

## Archivos
- `intro.md` — página principal del libro (será `intro.html`).
- `eda_bancario.ipynb` — tu notebook ejecutado (reemplázalo cuando lo actualices, mismo nombre).
- `_toc.yml` — tabla de contenido (define que `intro` es la portada).
- `_config.yml` — configuración (título, autor, `execute_notebooks: off`).
- `requirements.txt` — dependencia para compilar (`jupyter-book<2`).
- `.github/workflows/deploy.yml` — compila y publica automáticamente en cada `push`.

## Pasos (opción recomendada: automática con GitHub Actions)

1. Copia **todos** estos archivos a la carpeta de tu repositorio (respeta la carpeta
   `.github/workflows/`).
2. En `_config.yml` cambia `repository.url` por la URL de tu repo (y el autor/título si quieres).
3. Sube los cambios:
   ```bash
   git add .
   git commit -m "Publicar EDA como Jupyter Book"
   git push origin main
   ```
4. En GitHub: **Settings → Pages → Build and deployment → Source = "GitHub Actions"**.
5. Ve a la pestaña **Actions**; cuando el workflow termine (marca verde), tu sitio queda en:
   `https://<TU_USUARIO>.github.io/<TU_REPO>/intro.html`

> Cada vez que hagas `push` con el notebook actualizado, el sitio se reconstruye solo.

## Opción alternativa (manual, desde tu PC)

```bash
pip install "jupyter-book<2" ghp-import
jupyter-book build .
ghp-import -n -p -f _build/html
```
Luego en **Settings → Pages → Source = "Deploy from a branch" → rama `gh-pages` → `/(root)`**.
El sitio queda en la misma URL.

## Notas
- El repositorio debe ser **público** para GitHub Pages gratuito.
- Si tu rama por defecto es `master` en vez de `main`, cambia `branches: [main]` en el
  workflow (o renombra la rama).
- Para compilar localmente y verlo antes de publicar: `jupyter-book build .` y abre
  `_build/html/intro.html`.
