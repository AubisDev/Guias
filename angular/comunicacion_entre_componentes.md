# Comunicacion entre componentes

## Comunicacion Padre -> Hijo

Es para enviar informacion de un componente padre a un componente hijo.

En Angular, esto se hace con el decorador @Input(). Como en el ejemplo, donde tenemos 2 componentes diferentes como son: user.components y app.components

Vamos a utilizar en app.component el user.component. Para ello entonces, en el elemento hijo vamos a crear una propiedad que en este caso es el name, al cual se le colocara el decorador @Input(). Esto lo que indicara es que al momento que se llame este component en el padre, este le tiene que mandar un valor.

### user.component.ts

```
import {Component, Input} from '@angular/core';

@Component({
  selector: 'app-user',
  template: `
    <p>The user's name is {{ name }}</p>
  `,
  standalone: true,
})
export class UserComponent {
  @Input() name = '';
}

```

### app.component.ts

```
import {Component} from '@angular/core';
import {UserComponent} from './user.component';

@Component({
  selector: 'app-root',
  template: `
    <app-user name="Simran" />
  `,
  standalone: true,
  imports: [UserComponent],
})
export class AppComponent {}

```

## Comunicacion Hijo -> Padre

Es para enviar informacion de un componente hijo a un componente padre.

En Angular, esto se hace con el decorador @Output(). Como en el ejemplo, donde tenemos 2 componentes diferentes como son: user.components y app.components

Vamos a utilizar en app.component el app.component. Para ello entonces, en el child component se va a crear una propiedad con el decorador @Output() cuyo valor sera un new EventEmitter<TypeDelNuevoElemento>(); y la funcion que se va indiacar ese cambio. Esa funcion va a llamar a la propiedad con EventEmitter y se le agregara el emit(valor)

Entonces este claro debe tener un event que produzca esa funcion, en este caso un button, que contiene el binding de click (click)="addItem"

En el caso del componente padre donde lo vamos a utilizar el child.component.ts se va a crear la verdadera funcion que realizara el trabajo.

Se puede observar que se crea la funcuion addItem que ejecuta una accion. Es esa funcion que se colocara como valor al utilizar el child, de la forma:

<app-child (addItemEvent)="addItem($event)" />

donde $event sera la espera del emisor hijo

### child.component.ts

```
import {Component, Output, EventEmitter} from '@angular/core';

@Component({
  selector: 'app-child',
  styles: `.btn { padding: 5px; }`,
  template: `
    <button class="btn" (click)="addItem()">Add Item</button>
  `,
  standalone: true,
})
export class ChildComponent {
  @Output() addItemEvent = new EventEmitter<string>();

  addItem() {
    this.addItemEvent.emit('🐢');
  }
}

```

### app.component.ts

```
import {Component} from '@angular/core';
import {ChildComponent} from './child.component';

@Component({
  selector: 'app-root',
  template: `
    <app-child (addItemEvent)="addItem($event)" />
    <p>🐢 all the way down {{ items.length }}</p>
  `,
  standalone: true,
  imports: [ChildComponent],
})
export class AppComponent {
  items = new Array();

  addItem(item: string) {
    this.items.push(item);
  }
}

```
