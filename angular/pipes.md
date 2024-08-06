# Pipes

Los pipes son funciones que se utilizan para transformar la data en los templates. Los pipes son funciones puras, por lo que no causan efectos secundarios. Ademas que los que ya vienen definidos en angular, se pueden crear custom pipes.

Cabe recalcar que estos pipes deben ser importados en el componente para usarse.

Los pasos para usar un pipe son:

1. Importar el pipe que se va a utilizar

```
@Component({
    ...
    imports: [LowerCasePipe]
})
```

2. Anadir el pipe a los imports

```
@Component({
    ...
    imports: [LowerCasePipe]
})
```

3. Anadirlo en el template

```
template: `{{username | lowercase }}`
```

Ejemplo

```
import {UpperCasePipe} from '@angular/common';
@Component({
    ...
    template: `{{ loudMessage | uppercase }}`,
    imports: [UpperCasePipe],
})
class AppComponent {
    loudMessage = 'we think you are doing great!'
}
```

Ejemplo 2

```
import {Component} from '@angular/core';
import {LowerCasePipe} from '@angular/common';

@Component({
  selector: 'app-root',
  template: `
    {{ username | lowercase }}
  `,
  standalone: true,
  imports: [LowerCasePipe],
})
export class AppComponent {
  username = 'yOunGTECh';
}

```

## Pipes con parametros

Algunos pipes permiten pasarles parametros. Esto se produce con los ":"

---

Ejemplo con date

birthday = new Date(2023, 3, 2);

```
template: `{{ date | date:'medium' }}`;
```

La salida en este caso es:

### **Jun 15, 2015, 9:43:11 PM.**

---

Ejemplo con DecimalPipe

num = 103.1234;

```
template: `
    ...
    <li>Number with "decimal" {{ num | number:"3.2-2" }}</li>
`
```

Salida

### 103.12

---

Ejemplo con CurrencyPipe

cost = 4560.34;

```
template: `
    ...
    <li>Currency with "currency" {{ cost | currency }}</li>
`
```

Salida:

### $4,560.34

## Creacion de una Custom Pipe

Un Pipe es una clase con el decorador de **@Pipe({})**

En este ejemplo el Pipe acepta un string y retorna un string con estrellas alrededor del mismo.

el nmbre usado en el decorador @Pipe sera el que se utilizara en el template. Aqui seria "star". Y en la funcion con el PipeTransform es donde estara la logica.

```
import {Pipe, PipeTransform} from '@angular/core';
@Pipe({
  standalone: true,
  name: 'star',
})
export class StarPipe implements PipeTransform {
  transform(value: string): string {
    return `⭐️ ${value} ⭐️`;
  }
}
```

The StarPipe accepts a string value and returns that string with stars around it. Take note that:

the name in the @Pipe decorator configuration is what will be used in the template
the transform function is where you put your logic
