# Componentes Parte 2

## Añadir variables o propiedades a un componente

```
import {Component} from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    Hello {{ city }}, {{ 1 + 1 }}
  `,
  standalone: true,
})
export class AppComponent {
  city = 'San Francisco';
}

```

Para crear una propiedad esta debe ser declarado en la parte de la clase.

Y para su uso dentro de template es con: {{ nombreDePropiedad }}

Dentro de estos {{  Aqui podria ir cualquier codigo u operacion de javascript  }}, como por ejemplo: {{ 1 + 1 }} y en pantalla se vera un 2

## Como puedo usar los componentes en otra parte de la aplicacion?

Supongamos que tengamos los siguientes componentes de Angular:

Componente 1

```
import {Component} from '@angular/core';

@Component({
  selector: 'app-user',
  template: `
    Username: {{ username }}
  `,
  standalone: true,
})
export class UserComponent {
  username = 'youngTech';
}
```

Componenten 2

```
@Component({
  selector: 'app-root',
  template: ``,
  standalone: true,
  imports: [],
})
export class AppComponent {}
```

Si se quiere utilizar el componente 2 en el componente 1 seria de la forma siguiente:

```
@Component({
  selector: 'app-root',
  template: `
    <section>
      <app-user />
    </section>
  `,
  standalone: true,
  imports: [UserComponent],
})
export class AppComponent {}

```

De como que los cambios son: importar el componente 1 que se va a usar en este caso componente 2.

Ademas que puede llamar o usar con las llaves de html en la parte de template. Como en este caso.
