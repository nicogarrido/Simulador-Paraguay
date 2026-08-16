# Guía de inicio

Cómo dejar el entorno funcionando para trabajar en local y publicar con GitHub
Desktop. Se hace una sola vez; después el ciclo de trabajo son tres pasos.

---

## Qué hace cada pieza

| Herramienta | Para qué |
|---|---|
| **Quarto** | Convierte los archivos `.qmd` en el sitio HTML |
| **GitHub Desktop** | Sube los cambios sin usar la terminal |
| **GitHub Pages** | Publica el sitio en una dirección web |

El flujo es: se escribe en Markdown, Quarto genera el HTML dentro de `docs/`, y
GitHub Desktop sube ambas cosas. GitHub Pages publica lo que hay en `docs/`.

---

## Instalación

### 1. Quarto

Descargar de [quarto.org/docs/get-started](https://quarto.org/docs/get-started/)
e instalar con las opciones por defecto.

Para verificar, abrir una terminal y escribir:

```
quarto --version
```

Si devuelve un número de versión, quedó bien instalado.

> Si trabajás con RStudio, Quarto ya viene incluido desde la versión 2022.07 y
> podés renderizar con el botón **Render** en lugar de la terminal.

### 2. GitHub Desktop

Descargar de [desktop.github.com](https://desktop.github.com/) e iniciar sesión
con tu cuenta.

---

## Puesta en marcha

### 1. Crear el repositorio

En [github.com/new](https://github.com/new):

- **Nombre:** `Simulador-Paraguay`
- **Visibilidad:** Público
- **No** marcar ninguna casilla de inicialización

### 2. Clonarlo en tu computadora

En GitHub Desktop: **File → Clone repository**, elegir el repositorio recién
creado y la carpeta local donde querés trabajar.

Esa carpeta es tu espacio de trabajo. Todo lo que edites ahí adentro queda
sincronizado.

### 3. Copiar la base

Copiar el contenido de este paquete dentro de la carpeta clonada. Debe quedar
así:

```
Simulador-Paraguay/
├── _quarto.yml
├── estilos.scss
├── index.qmd
├── guia-de-estilo.qmd
├── .gitignore
├── README.md
├── LICENSE
├── recursos/
└── docs/
```

### 4. Personalizar

Reemplazar `USUARIO` por tu nombre de usuario de GitHub en dos archivos:
`_quarto.yml` (en `site-url` y en el enlace de GitHub) y `README.md`.

### 5. Primera publicación

En GitHub Desktop:

1. Escribir un mensaje en el recuadro de abajo a la izquierda, por ejemplo
   *"Base del sitio"*.
2. Clic en **Commit to main**.
3. Clic en **Push origin**.

### 6. Activar GitHub Pages

En el repositorio en GitHub: **Settings → Pages**.

- En *Source*, elegir **Deploy from a branch**
- Rama: `main`
- Carpeta: **`/docs`**
- Guardar

En un par de minutos el sitio queda disponible en
`https://USUARIO.github.io/Simulador-Paraguay`.

---

## El ciclo de trabajo

Una vez configurado, cada vez que quieras modificar algo:

### 1. Escribir

Editar los archivos `.qmd` con cualquier editor de texto. RStudio, VS Code o el
Bloc de notas sirven igual.

### 2. Generar el HTML

En la terminal, parado en la carpeta del proyecto:

```
quarto render
```

O bien, mientras escribís:

```
quarto preview
```

Este último abre el sitio en el navegador y lo actualiza solo cada vez que
guardás un archivo. Es la forma más cómoda de trabajar. Se corta con `Ctrl+C`.

### 3. Publicar

En GitHub Desktop: escribir el mensaje, **Commit to main**, **Push origin**.

---

## Agregar una página nueva

1. Crear el archivo, por ejemplo `modulo-1.qmd`, con un encabezado:

```yaml
---
title: "Módulo 1 · Fundamentos"
---
```

2. Agregarlo al menú lateral en `_quarto.yml`:

```yaml
  sidebar:
    contents:
      - index.qmd
      - modulo-1.qmd        # ← nueva página
      - guia-de-estilo.qmd
```

3. Renderizar y publicar.

Para organizar por secciones, se pueden anidar:

```yaml
  sidebar:
    contents:
      - index.qmd
      - section: "Taller"
        contents:
          - modulo-1.qmd
          - modulo-2.qmd
      - section: "Metodología"
        contents:
          - agregacion-sectorial.qmd
```

---

## Publicar el simulador

El archivo `.xlsm` está excluido en `.gitignore` a propósito: los binarios
grandes hacen crecer el historial de Git de forma permanente.

En el repositorio en GitHub, ir a **Releases → Create a new release**:

- **Tag:** `v1.0.0`
- **Título:** `Simulador MIP Paraguay v1.0`
- Adjuntar el `.xlsm` en *Attach binaries*

Para cada versión nueva, un Release nuevo describiendo los cambios.

---

## Problemas frecuentes

**`quarto: command not found`**
Quarto no quedó en el PATH. Cerrar y volver a abrir la terminal. Si persiste,
reinstalar marcando la opción de agregarlo al PATH.

**GitHub Desktop no muestra los archivos de `docs/`**
Verificar que `.gitignore` no incluya `docs/`. Esa carpeta debe versionarse:
es lo que publica GitHub Pages.

**El sitio no aparece después de activar Pages**
Puede tardar unos minutos la primera vez. Verificar en la pestaña *Actions* del
repositorio si el despliegue terminó.

**Las fórmulas matemáticas se ven como código**
Si abrís el HTML con doble clic desde el disco, MathJax no carga porque
necesita conexión. En el sitio publicado se ven bien. Para verlas en local,
usar `quarto preview`.

**Cambié los estilos y no se reflejan**
El navegador cachea el CSS. Recargar con `Ctrl+F5`.
