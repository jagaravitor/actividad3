# Prueba Lectiva

Base SvelteKit con arquitectura `feature-first/domain-first` para integrar la API de Rick and Morty.

## Run

```bash
npm install
npm run dev
```

## Check

```bash
npm run check
npm run build
```

## CI/CD

El repositorio incluye un workflow en GitHub Actions para:

- validar el proyecto con `npm run check`
- compilar la app con `adapter-static`
- desplegar automaticamente en GitHub Pages desde la rama `main`

Para que el despliegue funcione, en GitHub debes dejar activado `Settings > Pages > Build and deployment > Source: GitHub Actions`.

## Estructura

- `src/lib/core`: cliente HTTP, configuracion y adaptadores.
- `src/lib/entities`: tipos y mapeos de dominio.
- `src/lib/features`: features por caso de uso.
- `src/routes`: composicion de rutas y carga de datos.
