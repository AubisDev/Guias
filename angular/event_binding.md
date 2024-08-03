# Event Binding

El event binding es parecido que el properyBiding, pero para los tipicos eventos de HTML. Angular a diferencia que con las propiedades hace el binding con las (nombreDeEvent).

En este ejemplo se utilizar la funciona onMouseOver() { //Logica }

y se coloca en la etiqueta HTML como (mouseover)="onMouseOver()"

cabe decir que mouseover, es el Evento al que reaccionara el componente. y onMouseOver es la funcion que se va a realizar.

Cabe mencionar que haciendo this.message = valor; estamos cambiando el valor de la propiedad message de la clase AppComponent

```
import {Component} from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    <section (mouseover)="onMouseOver()">
      There's a secret message for you, hover to reveal:
      {{ message }}
    </section>
  `,
  standalone: true,
})
export class AppComponent {
  message = '';

  onMouseOver() {
    this.message = 'Way to go 🚀';
  }
}

```
