# Optimizacion de imagenes

Para la optimizacion de imagenes todo lo que era src o [src](imagen dinamica), sera cambiando por ngSrc.

Primero debemos importar el optimizador:

`import { NgOptimizedImage } from '@angular/common'`

Luego debemos colocarlo en el imports del componente a usarlo:

```
imports: [
  NgOptimizedImage,
  // ...
],
```

y se habilita colocando el ngSrc

`<img ngSrc="cat.jpg">`

## Imagenes con prioridad

Si queremos darle prioridad a la carga de una imagen debemos utilizar la propiedad de priority en la etiqueta img. Ejemplo:

`<img ngSrc="cat.jpg" width="400" height="200" priority>`

### Que produce darle esa prioridad?

Al darle prioridad coloca lo siguiente propiedades

```
Marking an image as priority applies the following optimizations:

Sets fetchpriority=high (read more about priority hints here)
Sets loading=eager (read more about native lazy loading here)
Automatically generates a preload link element if rendering on the server.
```

## Width y Height

Ademas podemos indicar un Width y un Height a la imagen si se quiere cunado se le aplica el ngSrc

`<img ngSrc="cat.jpg" width="400" height="200">`

## Fill para los background Image

En los casos dnde se quiere utilizar un fill no se debe colocar ni width ni height.

`<img ngSrc="cat.jpg" fill>`

## Placeholders

### Placeholders automaticos

`<img ngSrc="cat.jpg" width="400" height="200" placeholder>`

Adding placeholder attribute automatically requests a second, smaller version of the image using your specified image loader. This small image will be applied as a background-image style with a CSS blur while your image loads. If no image loader is provided, no placeholder image can be generated and an error will be thrown.

El tamano por defectos de los placeholders es de 30px. Si se quiere cambiar hay que realizar el siguiente agregado:

```
providers: [
  {
    provide: IMAGE_CONFIG,
    useValue: {
      placeholderResolution: 40
    }
  },
],
```

If you want sharp edges around your blurred placeholder, you can wrap your image in a containing <div> with the overflow: hidden style. As long as the <div> is the same size as the image (such as by using the width: fit-content style), the "fuzzy edges" of the placeholder will be hidden.

### Placeholders sin blur

`<img 
  ngSrc="cat.jpg" 
  width="400" 
  height="200" 
  placeholder 
  [placeholderConfig]="{blur: false}"
/>`

### Responsive images

Para responsive images revisar el Link para un mejor ejemplo

## Loaders

Angular tiene un imageLoader base si se quiere utilizar, que es el siguiente:

```
providers: [
  provideImgixLoader('https://my.base.url/'),
],
```

## Custom Loader

To use a custom loader, provide your loader function as a value for the IMAGE_LOADER DI token. In the example below, the custom loader function returns a URL starting with https://example.com that includes src and width as URL parameters.

```
providers: [
  {
    provide: IMAGE_LOADER,
    useValue: (config: ImageLoaderConfig) => {
      return `https://example.com/images?src=${config.src}&width=${config.width}`;
    },
  },
],

```

## NOTA

### **IMPORTANT: For the "fill" image to render properly, its parent element must be styled with position: "relative", position: "fixed", or position: "absolute".**

## LINK

https://angular.dev/guide/image-optimization
