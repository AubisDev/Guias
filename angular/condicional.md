# Condicinales

## Para mostrar informacion condicionalmente

```
import {Component} from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    @if (isServerRunning) {
    <span>Yes, the server is running</span>
    } @else {
    <span>No, the server is not running</span>
    }
  `,
  standalone: true,
})
export class AppComponent {
  isServerRunning = true;
}

```

Utilizando el decorador @If (condicion){ logica... } y en caso contrario @Else {} Podemos mostrar una informacion de forma condicional.
