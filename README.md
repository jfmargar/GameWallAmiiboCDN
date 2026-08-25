# GameWallAmiiboCDN

Imágenes de amiibo que consume GameWall, servidas por CDN a través de jsDelivr.

Este repo solo contiene assets estáticos. No hay código ni build: se actualiza
subiendo imágenes nuevas y publicando un tag.

## Estructura

```
images/amiibo/icon_{head}-{tail}.webp            variante optimizada compatible con la app
images/amiibo/high-res/icon_{head}-{tail}.png    PNG original sin recodificar
manifest.json                           id de amiibo -> nombre de fichero
```

## Cómo se construye la URL

El nombre del fichero se deriva del id del amiibo, sin necesidad de guardar
ninguna URL en Firestore. El id son 16 dígitos hex (`head` + `tail`):

```
id 0438000103000502  ->  icon_04380001-03000502.webp
```

Y la URL completa, fijando siempre un tag para que la caché sea inmutable:

```
https://cdn.jsdelivr.net/gh/<usuario>/GameWallAmiiboCDN@<tag>/images/amiibo/icon_04380001-03000502.webp
```

Para obtener la variante de alta resolución se conserva el mismo nombre y se añade `high-res/`:

```text
https://cdn.jsdelivr.net/gh/<usuario>/GameWallAmiiboCDN@<tag>/images/amiibo/high-res/icon_04380001-03000502.png
```

## Publicar una versión

Los tags son inmutables a propósito: la app cachea las imágenes para siempre y
solo vuelve a descargarlas cuando cambia el tag. Nunca sirvas desde `@main`.

```bash
git tag v2026.08.24 && git push --tags
```

Después, actualiza el tag activo en la app (o en el documento de configuración
de Firestore, si se decide moverlo ahí).

## Origen y créditos

Las imágenes provienen del catálogo comunitario
[8bitDream/AmiiboAPI](https://github.com/8bitDream/AmiiboAPI), que a su vez las
acredita a [amiibo.life](http://amiibo.life). El código de aquel proyecto es
MIT (© 2017 Nevin Vu); esa licencia cubre el código, no las imágenes, que son
propiedad de Nintendo.
