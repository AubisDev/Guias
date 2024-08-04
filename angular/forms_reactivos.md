# Forms Reactives

Los forms reactivos se usan cuando se buscan controlar los inputs mediante pura programacion, en vez del automatizado con el template. Para ello..

## 1. Importar el ReactiveForms y colocarlo en el import del componente

```
import { ReactiveFormsModule } from '@angular/forms';
@Component({
  selector: 'app-root',
  standalone: true,
  template: `
    <form>
      <label>Name
        <input type="text" />
      </label>
      <label>Email
        <input type="email" />
      </label>
      <button type="submit">Submit</button>
    </form>
  `,
  imports: [ReactiveFormsModule],
})
```

## 2. En el mismo componente debemos crear un formGroup

```
import {ReactiveFormsModule, FormControl, FormGroup } from '@angular/forms';
...
export class AppComponent {
  profileForm = new FormGroup({
    name: new FormControl(''),
    email: new FormControl(''),
    // y asi seguir con los siguientes inputs que se necesiten
  });
}
```

## 3. Hacer el binding con la propiedad de formControlName

Aqui suceden dos cosas, una se asigna el FormGroup a la etiqueta form y se le coloca el nombre del formControlName a cada uno de los input

## 4. Para mostrar los datos en pantalla

```
...
<h2>Profile Form</h2>
<p>Name: {{ profileForm.value.name }}</p>
<p>Email: {{ profileForm.value.email }}</p>
```

## 5. Acceder al valor de FormGroup (Opcional)

Esto seria con el this.value.nombreInput

```
handleSubmit() {
 alert(
   this.profileForm.value.name + ' | ' + this.profileForm.value.email
 );
}
```

## 6. Se asigna el submit a la etiqueta form

```
<form
  [formGroup]="profileForm"
  (ngSubmit)="handleSubmit()">
```

## Ejemplo completo

```
import {Component} from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    <form>
      <label>
        Name
        <input type="text" formControlName="name" />
      </label>
      <label>
        Email
        <input type="email" formControlName="email" />
      </label>
      <button type="submit">Submit</button>
    </form>
  `,
  standalone: true,
  imports: [],
})
export class AppComponent {}

```
