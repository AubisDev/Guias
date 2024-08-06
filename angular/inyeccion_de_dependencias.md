# Inyeccion de dependencias

La inyeccion de depedencias se usara para utilizar servicios, clases, strings, booleanos, o cualquier otro valor como dependencias. Las dependecias es un patron de diseno que y mecanismo para crear y entregar en algunas partes de la aplicacion que lo requieran, incrementando la modularizacion y flexibilidad.

Existe una forma de crear un injectable pero varias para consurmirla.

## Creacion de un Servicio Injectable

Para crear un servicio inyectable simplemente hay que anadir el decorador Injectable y luego configurar donde estara disponible el mismo con el providedIn.

Si a providedIn se le coloca como valor 'root'. Este inyectable estara disponible en toda la aplicacion.

Existe otras formas de declarar el scope del servicio inyectable pero root es el mas utilizado.

Para mas informacion: https://angular.dev/guide/di/dependency-injection'

---

Ejemplo

Servicio inyectable general

```
@Injectable({
    providedIn: 'root'
})
class UserService {
    // methods to retrieve and return data
}
```

Ejemplo mas completo:

```
import {Injectable} from '@angular/core';

@Injectable({
  providedIn: 'root',
})
export class CarService {
  cars = ['Sunflower GT', 'Flexus Sport', 'Sprout Mach One'];

  getCars(): string[] {
    return this.cars;
  }

  getCar(id: number) {
    return this.cars[id];
  }
}
```

## Como consumir los servicios inyectables

Existe dos formas de consurmirlo.

1. En la primera forma es creando una variable que usara el servicio y luego usando el inject para colocar el valor donde queremos.

Aqyui vemos que se usa la variable carService con el inject y en el constructor asignamos el valor a la variable que necesitamos con los valores del inyectable.

```
import {Component, inject} from '@angular/core';
import {CarService} from './car.service';

@Component({
  selector: 'app-root',
  template: `
    <p>Car Listing: {{ display }}</p>
  `,
  standalone: true,
})
export class AppComponent {
  display = '';
  carService = inject(CarService);

  constructor() {
    this.display = this.carService.getCars().join(' ⭐️ ');
  }
}
```

2. Mediante el constructor de la clase

En esta forma, se llama el servicio mediante el constructor y se le asigna en valor dentro de los bracket de este.

```
import {Component} from '@angular/core';
import {CarService} from './car.service';

@Component({
  selector: 'app-root',
  template: `
    <p>Car Listing: {{ display }}</p>
  `,
  standalone: true,
})
export class AppComponent {
  display = '';

  constructor(private carService: CarService) {
    this.display = this.carService.getCars().join(' ⭐️ ');
  }
}

```
