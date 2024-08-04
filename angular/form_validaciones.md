# Validacion de forms

## 1. Para realizar validaciones se utilizaran un par de modulos

```
import {ReactiveFormsModule, Validators} from '@angular/forms';
@Component({...})
export class AppComponent {}
```

## 2. Uso de los modulos ReactiveFormsModule y Validators en los forms

Para poder usarlo en los formGroups. Se hace de la siguiente forma

Si hay mas de una validacion se deben colocar en un array

```
profileForm = new FormGroup({
  name: new FormControl('', Validators.required),
  email: new FormControl('', [Validators.required, Validators.email]),
});
```

## 3. Chequeo de validacion en el template

donde si el form no es valido no permitira el submit.

```
<button type="submit" [disabled]="!profileForm.valid">Submit</button>
```

## Ejemplo completo

```
import {Component} from '@angular/core';
import {FormGroup, FormControl} from '@angular/forms';
import {ReactiveFormsModule, Validators} from '@angular/forms';

@Component({
  selector: 'app-root',
  template: `
    <form [formGroup]="profileForm">
      <input type="text" formControlName="name" name="name" />
      <input type="email" formControlName="email" name="password" />
      <button type="submit" [disabled]="!profileForm.valid">Submit</button>
    </form>
  `,
  standalone: true,
  imports: [ReactiveFormsModule],
})
export class AppComponent {
  profileForm = new FormGroup({
    name: new FormControl('', Validators.required),
    email: new FormControl('', Validators.required),
  });
}

```
