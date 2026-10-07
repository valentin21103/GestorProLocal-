# GestorPro — Instaladores

Acá viven **solo los instaladores** de GestorPro (versión local, de escritorio).
El código fuente está en otro lado: `gestorFrontPRO_` (front) y `GestorBackPRO_` (back), ambos privados.

## Para qué sirve este repo

Las apps instaladas chequean acá si hay una versión nueva. El archivo que miran es el
`latest.yml` de cada release: ahí figuran la versión, el nombre del instalador y su hash.

Por eso el repo es **público**: `electron-updater` descarga ese archivo sin credenciales.
Si fuera privado recibiría un 404 y los clientes nunca se enterarían de que hay actualización.

## Cómo se publica una versión

Desde `GestorPro-Front`:

```bash
npm run publish:release   # requiere GH_TOKEN con scope repo
```

Sube tres archivos, y los tres hacen falta:

| Archivo | Para qué |
|---|---|
| `GestorPro-Setup-x.y.z.exe` | el instalador |
| `...exe.blockmap` | permite bajar solo lo que cambió, no los 143 MB enteros |
| `latest.yml` | **el que dispara la actualización**. Sin esto no pasa nada |

> La versión de `package.json` tiene que subir sí o sí. El updater compara números: si la
> publicada es igual a la instalada, no actualiza nada.

## Descargar a mano

La última versión siempre está en
[Releases](https://github.com/valentin21103/GestorProLocal-/releases/latest).
