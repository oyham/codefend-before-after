<h1 align="center">Codefend-ui-ux-redesign</h1>

Este repositorio presenta el antes y después de la interfaz de usuario (UI) y la experiencia del usuario (UX) que realicé para la empresa Codefend durante un concurso freelance. Se destacan las mejoras realizadas, los desafíos abordados y la evolución del diseño. 

## Singin / Signup

En las primeras dos capturas de pantalla se presenta el proceso de inicio de sesión (Signin) antes y después del rediseño.

### Before:
En la siguiente imagen, se observa que el formulario de inicio de sesión se encuentra en el lateral derecho de la pantalla, lo que resultaba en una presentación visual desalineada y poco estética. Esta ubicación afectaba la coherencia del diseño y la experiencia del usuario.

![0_before_localhost_3000_auth_signin(iPhone 12 Pro)](https://github.com/oyham/codefend-before-after/assets/97111287/656c258a-01d2-4e8c-8d18-c012f6eb0612)

### After:
Luego se implementaron cambios significativos para mejorar la presentación visual y la usabilidad. El formulario de inicio de sesión ha sido reubicado y ahora está centrado en la pantalla, proporcionando una apariencia más equilibrada y mejorando la accesibilidad para los usuarios.

![1_after_localhost_3000_auth_signin(iPhone 12 Pro)](https://github.com/oyham/codefend-before-after/assets/97111287/03f29b64-8ffc-4b8a-aef5-19669b0f9f29)

###### Notar que el logo de Codefend en la primera imagen no se visualizaba debido a problemas de posicionamiento y conflictos con estilos de elemenetos hijos.
---
### Before | After Signup: 

También sucedía el mismo problema con Signup, encontrandose este en el lateral derecho. Al posicionarlo correctamente, el formulario ocupaba todo el ancho de la pantalla, perdiendo el estilo original del fondo rojo de Codefend. Para solucionar esto, se aplico un maximo de anchura. Finalmente se posiciono correctamente el ultimo _el_ `<a>`.

![2_before_localhost_3000_auth_signup(iPhone 12 Pro)](https://github.com/oyham/codefend-before-after/assets/97111287/7cbfa977-b330-4d0e-beda-536ef7f8f975) ![3_after_localhost_3000_auth_signup(iPhone 12 Pro)](https://github.com/oyham/codefend-before-after/assets/97111287/66bd7439-f912-4c1a-8b31-75cd70ad7e2d)

![4_after_localhost_3000_auth_signup(iPhone 12 Pro)](https://github.com/oyham/codefend-before-after/assets/97111287/d336c1e1-03bb-48ad-a5f8-c8812c2d8a7a) ![5_after_localhost_3000_auth_signup(iPhone 12 Pro)](https://github.com/oyham/codefend-before-after/assets/97111287/2ae5e553-6bd9-4853-a651-26c139f57df2)

Para finalizar comprobe cómo se visualizaba en diferentes dispositivos (medidas), y encontre que en dispositivos de 360x740 el formulario ocupaba demasiado espacio vertical, asi que se le aplicó un overflow-y interno para una mejor experiencia de usuario.
![360x740exampleOverflowY](https://github.com/oyham/codefend-before-after/assets/97111287/115b3acc-fc26-43ef-8a1c-da86ba2336d3)

---
### Solucionando diferentes errores en medidas de escritorio:

#### Page endpointsApp.jsx:
El siguiente error se lanzaba en consola al iniciar sesión en la aplicación de Codefend:

![0_ssENPconsoleError](https://github.com/oyham/codefend-before-after/assets/97111287/78e88b9d-9b3c-48ea-8b73-3f014afe64c0)

Luego de solucionar este error la aplicación renderizó correctamente, pero habia un pequeño bug, donde un Loader se mostraba continuamente sin desaparecer, incluso después de que la operación debería haber finalizado.
Posibles causas:
- Un bucle infinito o una condición que impide que el código responsable de ocultar el Loader se ejecute correctamente.
- Un mal manejo de errores que impide que el código de cierre del Loader se ejecute en caso de fallo.
- Problemas con la gestión de eventos o asincronía que impiden la correcta finalización de la operación.

Esto se solucionó aplicando el siguiente código en el componente endpointsApps.jsx provenitente de src > Views > viewComponents.
```jsx
<Show when={!props.isLoading && props.endpoints[0].apps.length === 0}>
   <EmptyCard />
</Show>
```
### Before | After endpointApp:

![1_ssENP](https://github.com/oyham/codefend-before-after/assets/97111287/b8045e94-ea17-49f2-9f46-852cab27ce58) ![2_ssENP fixed](https://github.com/oyham/codefend-before-after/assets/97111287/1d6f3c3c-8321-4e6c-b27d-a9d48fe74623)

Finalmente se renderizó correctamente `<EmptyCard />`.

---
