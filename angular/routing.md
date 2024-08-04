# Rutas

## Habilitacion de Rutas

Para habilitar el routing en una aplicacion de angular debemos realizar una serie de pasos.

1. Crear el archivo **app.routes.ts** y dentro de este archivo colocar lo siguiente:

```
import {Routes} from '@angular/router';
export const routes: Routes = [];
```

2. Debemos ir a **app.config.ts** para configurar el router

```
import {ApplicationConfig} from '@angular/core';
import {provideRouter} from '@angular/router';
import {routes} from './app.routes';

export const appConfig: ApplicationConfig = {
  providers: [provideRouter(routes)],
};
```

3. Una vez configurado, para poder utilizarlo debemos usar el router outlet

Finally, to make sure your app is ready to use the Angular Router, you need to tell the app where you expect the router to display the desired content. Accomplish that by using the RouterOutlet directive from @angular/router.

Update the template for AppComponent by adding <router-outlet />

```
import {RouterOutlet} from '@angular/router';
@Component({
  ...
  template: `
    <nav>
      <a href="/">Home</a>
      |
      <a href="/user">User</a>
    </nav>
    <router-outlet />
  `,
  standalone: true,
  imports: [RouterOutlet],
})
export class AppComponent {}
```

## Crear rutas

### La creacion de rutas se hace en app.routes.ts

```
import {Routes} from '@angular/router';
import {HomeComponent} from './home/home.component';
export const routes: Routes = [
  {
    path: '',
    component: HomeComponent,
  },
];
```

otro ejemplo con titulo:

```
import {Routes} from '@angular/router';
import {HomeComponent} from './home/home.component';
export const routes: Routes = [
  {
    path: '',
    title: 'App Home Page',
    component: HomeComponent,
  },
];
```

## Creacion de Link para moverse entre rutas con RouterLink

Para poder moverse entre las rutas con el link, primero debemos importar el RouterLink de @angular/router

y colocando la ruta routerLink como en `<a routerLink="/">Home</a>`.

```
...
import { RouterLink, RouterOutlet } from '@angular/router';
@Component({
  standalone: true,
  imports: [RouterLink, RouterOutlet],
  ...
})
```

```
import { RouterLink, RouterOutlet } from '@angular/router';
@Component({
  ...
  standalone: true,
  template: `
    ...
    <a routerLink="/">Home</a>
    <a routerLink="/user">User</a>
    ...
  `,
  imports: [RouterLink, RouterOutlet],
})
```

Recuerdar que el contenido que cambia es lo que esta router outlet
