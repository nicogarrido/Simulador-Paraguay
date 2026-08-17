# Cómo publicar y actualizar el simulador

El archivo pesa unos 270 KB, así que se versiona dentro del repositorio en lugar
de distribuirse por Releases. Eso permite tener un **enlace fijo** que nunca
cambia.

## El enlace

```
https://USUARIO.github.io/Simulador-Paraguay/simulador/Simulador-MIP-Paraguay.xlsm
```

Ese enlace se puede compartir por correo, ponerlo en una presentación o en el
material del taller. Seguirá funcionando después de cada actualización.

## Para actualizar a una versión nueva

1. Renombrar el archivo nuevo como **`Simulador-MIP-Paraguay.xlsm`**, exactamente
   así.
2. Copiarlo en la carpeta `simulador/` de la carpeta local, reemplazando el
   anterior.
3. `quarto render`
4. Commit y Push en GitHub Desktop.

El enlace no cambia. Quien lo tenga guardado descargará la versión nueva.

::: Importante
El nombre del archivo debe mantenerse idéntico. Si se le agrega un número de
versión —`Simulador-v19.xlsm`— el enlace anterior deja de funcionar y hay que
actualizar todos los lugares donde se compartió.
:::

## Dónde queda el historial

Git guarda cada versión anterior aunque el nombre no cambie. Para recuperar una:
en GitHub, entrar al archivo, luego **History**, elegir el commit y descargar
desde ahí.

Conviene escribir mensajes de commit descriptivos —«Simulador v18: reescalamiento
del bloque internacional»— para poder ubicar cada versión después.

## Sobre el peso del repositorio

Cada versión que se sube queda guardada en el historial de Git de forma
permanente. A 270 KB por versión, veinte actualizaciones suman unos 5 MB: es
perfectamente manejable.

Si el archivo creciera mucho —más de 5 MB por versión— convendría pasar al
esquema de Releases, donde los binarios no engordan el historial.

## Alternativa: enlace directo al archivo en GitHub

Si se prefiere no depender de GitHub Pages, el archivo también es accesible por:

```
https://github.com/USUARIO/Simulador-Paraguay/raw/main/simulador/Simulador-MIP-Paraguay.xlsm
```

Funciona igual y también es un enlace estable. La ventaja del primero es que
queda integrado al sitio del curso.
