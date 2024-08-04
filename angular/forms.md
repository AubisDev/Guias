# Formularios

## Definimos un input a utilizar

```
<label for="framework">
  Favorite Framework:
  <input id="framework" type="text" />
</label>
```

## Importamos el FormsModule

Para habilitar el data binding de un input debemos importarlo en el componente que se va a utilizar

```
import {Component} from '@angular/core';
import {FormsModule} from '@angular/forms';
@Component({
  ...
  standalone: true,
  imports: [FormsModule],
})
export class UserComponent {}
```

## Agregar el data binding al input con la directiva ngModel

```
<label for="framework">
  Favorite Framework:
  <input id="framework" type="text" [(ngModel)]="favoriteFramework" />
</label>
```

Ejemplo mas completo

doinde favoriteFramework es la variable que se va modificar y donde se guardara la informacion del input.

```
import {Component} from '@angular/core';
import {FormsModule} from '@angular/forms';

@Component({
  selector: 'app-user',
  template: `
    <p>Username: {{ username }}</p>
    <p>{{ username }}'s favorite framework: {{ favoriteFramework }}</p>
    <label for="framework">
      Favorite Framework:
      <input id="framework" type="text" [(ngModel)]="favoriteFramework" />
    </label>
  `,
  standalone: true,
  imports: [FormsModule],
})
export class UserComponent {
  favoriteFramework = '';
  username = 'youngTech';
}
```

### **Note: The syntax [()] is known as "banana in a box" but it represents two-way binding: property binding and event binding**

## Accediendo al valor de los inputs

### Mostrar el valor del input en el template

Esto se hace con {{ nombreVariable }} en este ejemploi es favoriteFramework

```
@Component({
  selector: 'app-user',
  template: `
    ...
    <p>Framework: {{ favoriteFramework }}</p>
    <label for="framework">
      Favorite Framework:
      <input id="framework" type="text" [(ngModel)]="favoriteFramework" />
    </label>
  `,
})
export class UserComponent {
  favoriteFramework = '';
}
```

## Referencia al valor actual de la variable del input en la clase

```
...
@Component({
  selector: 'app-user',
  template: `
    ...
    <button (click)="showFramework()">Show Framework</button>
  `,
  ...
})
export class UserComponent {
  favoriteFramework = '';
  ...
  showFramework() {
    alert(this.favoriteFramework);
  }
}
```

## Ejemplo completo

```
import {Component} from '@angular/core';
import {FormsModule} from '@angular/forms';

@Component({
  selector: 'app-user',
  template: `
    <p>Username: {{ username }}</p>
    <p>Framework: {{ favoriteFramework }}</p>
    <label for="framework">
      Favorite Framework:
      <input id="framework" type="text" [(ngModel)]="favoriteFramework" />
    </label>
    <button (click)="showFramework()">Show Framework</button>
  `,
  standalone: true,
  imports: [FormsModule],
})
export class UserComponent {
  favoriteFramework = '';
  username = 'youngTech';

  showFramework() {
    alert(this.favoriteFramework);
  }
}

```
