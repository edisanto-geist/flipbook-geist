# Flipbook estático (PDF.js + StPageFlip)

## Cómo usarlo

1. Poné tus PDFs dentro de la carpeta `pdfs/`.
2. Editá el array `LIBROS` arriba de todo en `index.html`:

```js
const LIBROS = [
  { id: "skorpios", nombre: "Skorpios Chile", archivo: "pdfs/skorpios.pdf" },
  { id: "embrujo",  nombre: "Embrujo Mexicano", archivo: "pdfs/embrujo.pdf" },
];
```

- `id`: identificador corto, sin espacios (se usa en la URL).
- `nombre`: lo que se ve en el selector desplegable.
- `archivo`: ruta relativa al PDF dentro de `pdfs/`.

3. Listo. No hay build, no hay dependencias para instalar.

## Subir a GitHub Pages

```bash
git init
git add .
git commit -m "flipbook"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/TU_REPO.git
git push -u origin main
```

Después: Settings → Pages → Source → "main" branch, carpeta `/ (root)`. Te va a quedar publicado en:

```
https://TU_USUARIO.github.io/TU_REPO/
```

## Compartir un libro puntual

Cualquier libro se puede linkear directo agregando `?file=ID`:

```
https://TU_USUARIO.github.io/TU_REPO/?file=skorpios
```

Útil para mandarle a una agencia el link de un solo paquete sin que tenga que elegir del menú.

## Notas

- Todo se renderiza en el navegador del visitante (PDF.js convierte cada página a imagen al vuelo), así que **no necesitás backend ni subir nada a un servicio externo**.
- PDFs muy largos (50+ páginas) tardan un poco más en cargar la primera vez porque renderiza todas las páginas. Si tenés catálogos grandes y querés que cargue más rápido, se puede optimizar para que renderice solo las páginas visibles (lazy loading) — avisame si llegás a necesitarlo.
- El efecto de "doblez" y sombra se ajusta con `maxShadowOpacity` en el código.
- Anda bien en mobile (swipe para pasar página).
