# EDA — Fuga y valor del cliente en una *fintech* colombiana

**Universidad del Norte · Machine Learning · Entrega 1**
Martínez Pulido, Valerie · Basto Martínez, Abrahan · Esguerra Fernández, Rubén

📖 **Sitio publicado:** https://rubenesg.github.io/prueba2026/

Análisis exploratorio y auditoría de calidad de datos sobre el conjunto público
[COFINFAD](https://data.mendeley.com/datasets/mhb4zn3258/1) (48.723 clientes, 54 variables
y 3.159.157 transacciones, 2023).

## Contenido

| Archivo | Descripción |
|---|---|
| `eda_bancario.ipynb` | Notebook ejecutado con todo el análisis (18 figuras, 12 tablas) |
| `docs/` | Sitio web ya compilado. Es lo que publica GitHub Pages |
| `_toc.yml`, `_config.yml`, `_static/custom.css` | Fuentes del libro (página única, a todo el ancho) |

## Recompilar (solo si se modifica el notebook)

```bash
pip install "jupyter-book<2"
jupyter-book build .
rm -rf docs && cp -r _build/html docs && touch docs/.nojekyll
git add -A && git commit -m "Actualizar sitio" && git push
```
