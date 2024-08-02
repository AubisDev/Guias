# Angular

## Componentes

### Como luce un componente de Angular?

```
import {Component} from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    Hello
  `,
  styles: `
    :host {
      color: blue;
    }
  `,
  standalone: true,
})
export class AppComponent {}

```

**@Component**: Este decorador proporciona metadatos sobre el componente. Los metadatos son datos sobre los datos, y en este caso, describen cómo Angular debe tratar este componente.

**selector**: Es el nombre que se utilizará en las plantillas HTML para insertar este componente en otras partes de la aplicación. En este caso, el selector es app-root, lo que significa que este componente será la raíz de la aplicación.

**template**: Aquí se define la plantilla HTML del componente. La plantilla es la vista que el usuario verá. En este ejemplo simple, la plantilla solo muestra la palabra "Hello".

**styles** : Estilos css etc.

**standalone**: Esta opción indica que el componente es independiente y no necesita ser declarado en un módulo. Es una característica de Angular 14+ que simplifica la creación de componentes.

## El porque de su estructura

- Encapsulación: Cada componente encapsula su propia lógica y vista, lo que hace que la aplicación sea más modular y fácil de mantener.

- Reutilización: Los componentes pueden ser reutilizados en diferentes partes de la aplicación, lo que reduce la duplicación de código.

- Jerarquía: Los componentes pueden estar anidados unos dentro de otros, creando una jerarquía de componentes que refleja la estructura de la aplicación.

- Declarativa: La sintaxis de las plantillas es declarativa, lo que significa que se describe lo que se quiere mostrar, en lugar de cómo se debe mostrar.

- Tipado: TypeScript proporciona un sistema de tipos que ayuda a prevenir errores y a mejorar la legibilidad del código.

## Metadatos?

Los metadatos en un componente de Angular son como una receta que le indican a Angular cómo debe tratar ese componente. A través de ellos, le proporcionamos información esencial para que Angular pueda crear, renderizar y gestionar el componente de manera correcta.

En este caso metadatos se refiere a lo que datos proporcionados en el componente como styles, template, etc...

## Standalone

Cuando se establece standalone: true en un componente, se indica a Angular que este componente puede funcionar de forma independiente, sin necesidad de ser declarado en un módulo. Esto significa que el componente puede ser utilizado directamente en cualquier otra parte de la aplicación.

**Casos de uso**

- Componentes pequeños y simples: Son ideales para componentes que tienen una funcionalidad muy específica y no dependen de otros componentes de forma compleja.

- Componentes reutilizables: Si un componente va a ser utilizado en múltiples partes de la aplicación, standalone puede facilitar su reutilización.

- Prototipado rápido: Para crear prototipos rápidamente, standalone permite construir componentes de forma aislada.
