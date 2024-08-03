# Property binding

Cuando se habla de property binding es que es una forma de bindear una propiedad en este caso, global con el valor de una variable. Angular realizar el properyBinding con [nombreDePropiedad]. En este caso, Angular utiliza el [editable] para bindear la propiedad de contenteditable de HTML. El resto de propiedades por ejemplo en div, pueden ser conseguidas en la siguiente pagina:

https://www.w3schools.com/tags/ref_standardattributes.asp

Ejemplo de Implementacion

```
import {Component} from '@angular/core';

@Component({
  selector: 'app-root',
  styleUrls: ['app.component.css'],
  template: `
    <div [contentEditable]="isEditable"></div>
  `,
  standalone: true,
})
export class AppComponent {
  isEditable = true;
}

```
