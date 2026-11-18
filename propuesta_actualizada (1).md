# Sistema web de gestión de pedidos para la Pastelería 16 de Agosto

**Propuesta de Proyecto Integrador**  
Programa Académico Desconcentrado: Técnico Superior en Informática  
UMSA · Sede Colquencha

Autor: Maura Mamani Fernandez
Fecha: noviembre de 2026

---

##  Tipo de proyecto

**Proyecto integrador de desarrollo de software.** El proyecto plantea ampliar el trabajo realizado en el módulo de Programación Web mediante el diseño y desarrollo de un sistema que permita administrar los pedidos de la Pastelería 16 de Agosto.

El trabajo parte de un sitio web comercial que ya fue desarrollado y publicado. La propuesta se enfoca en complementar esa primera versión con una solución para registrar, organizar, consultar y dar seguimiento a los pedidos, incluyendo las fechas de entrega y la información de los pagos.

No se trata únicamente de una página informativa: se busca construir una herramienta funcional que responda a necesidades del negocio y que esté acompañada de su documentación, pruebas y puesta en funcionamiento.

---

## EL punto de partida


La página actual permite mostrar el catálogo de productos, consultar precios y horarios, buscar y filtrar productos, seleccionar artículos para realizar un pedido y utilizar componentes interactivos. También incluye un tablero visual para organizar productos según su estado de preparación, un armador de bandejas personalizadas, preferencias de visualización y consulta de ubicación.

El catálogo documentado contiene productos como pasteles, masitas, alfajores, bizcochos, galletas y queques. Entre sus funciones técnicas se encuentran HTML5, CSS3, JavaScript, jQuery, archivos JSON, `localStorage`, Fetch API, Drag & Drop y Canvas 2D.

Sin embargo, el sitio publicado en GitHub Pages es principalmente el frontend comercial. Para contar con un sistema de gestión que almacene los pedidos de manera persistente y permita consultarlos posteriormente, se propone desarrollar un módulo adicional conectado a una base de datos.

| Situación actual | Trabajo propuesto |
|---|---|
| Sitio web comercial publicado y funcional. | Integrar un módulo de gestión de pedidos. |
| Catálogo y datos de productos organizados en archivos JavaScript y JSON. | Diseñar una base de datos para almacenar clientes, productos y pedidos. |
| Formulario e interacción para solicitar productos. | Implementar el registro y la consulta persistente de pedidos. |
| Componentes visuales para organizar productos. | Incorporar seguimiento de pedidos, fechas de entrega y control de adelantos y saldos. |
| Publicación del frontend en GitHub Pages. | Desarrollar y desplegar el módulo que requiera PHP y MySQL en un servicio compatible. |

---

##  El cliente y del negocio

La **Pastelería 16 de Agosto** es un emprendimiento familiar ubicado en la plaza principal del municipio de Colquencha, en la Av. Samuel 002. La propietaria identificada para el proyecto es **Karen**.

El negocio ofrece productos de pastelería artezanales y repostería  como las  masitas, alfajores, bizcochos, galletas y queques. 
El sitio web desarrollado  ayudara a difundir los productos, mostrar sus precios y horarios de atención y facilitar el contacto para realizar encargos.

**como trabaja hoy**
El sistema será utilizado por el propietario karen  y el personal encargado de atender los pedidos de la Pastelería 16 de Agosto.
Actualmente los pedidos se realiza manualmente en un cuaderno fisico lo que implica a revisar los apuntes  para encontrar los pedidos y sus carateristcas de cada pedido y las  fechas de entrega, con el nuevo sistema, el usuario podrá registrar cada pedido y consultar directamente los pedidos pendientes mediante una búsqueda por fecha.


**Fuente de esta información** la infomacion se obtubo a la  entrevista  previa que se realiso al propietario de la Pastelería 16 de Agosto el viernes 13 de noviembre de 2026. en la cual prorciono la  información sobre el registro  que realiza de manera manual de los  pedidos y  las fechas de entrega . las  perdidas  económicos   son ocacionada  por el extravío de las  hojas del cuaderno.

---

##  Formulación del problema

La Pastelería 16 de Agosto necesita contar con una forma más organizada de administrar los pedidos que realizan sus clientes. El sitio web comercial ya permite presentar los productos y ofrece un formulario para solicitar encargos; sin embargo, la memoria técnica del proyecto no acredita que exista una base de datos conectada que conserve los pedidos y permita administrarlos de manera permanente.

Cuando la información de los encargos no se encuentra centralizada, puede resultar más difícil revisar qué productos se deben preparar, para qué fecha se necesitan y qué pagos se han realizado. Además, si los datos quedan únicamente en registros manuales o temporales, existe el riesgo de que no estén disponibles cuando se necesiten.

Por esta razón, se propone desarrollar un sistema web que permita registrar los datos del cliente, los productos solicitados, las cantidades, las fechas de entrega y los importes económicos relacionados con cada pedido. El sistema facilitará la consulta de los encargos y su seguimiento hasta la entrega.

###  Dificultades que se busca atender

1. **Organización de los pedidos.** Se necesita reunir los datos de cada encargo en un registro ordenado para evitar depender de anotaciones dispersas.
2. **Consulta por fecha de entrega.** Se requiere identificar con facilidad qué pedidos deben prepararse o entregarse en un día determinado.
3. **Seguimiento del estado.** Es conveniente distinguir los pedidos pendientes, en preparación y entregados.
4. **Control de pagos.** Se necesita registrar el precio total, los adelantos recibidos y el saldo pendiente de cada pedido.
5. **Conservación de la información.** Una base de datos permitirá guardar los registros para consultarlos posteriormente y realizar copias de respaldo.

Estas necesidades constituyen el enfoque de la propuesta. Las cantidades exactas de pedidos extraviados, pérdidas económicas o confusiones de pago no están confirmadas en la memoria técnica y no se presentan como datos comprobados.

###  Árbol de problemas

```text
EFECTOS
- Dificultad para hacer seguimiento de los encargos.
- Posibles confusiones sobre fechas de entrega y pagos.
- Tiempo adicional para buscar o verificar información.

                    ↑

PROBLEMA CENTRAL
La gestión de los pedidos de la Pastelería 16 de Agosto
requiere un registro centralizado que permita organizar,
consultar y controlar cada encargo.

                    ↑

CAUSAS
- No se cuenta todavía con una base de datos integrada
  al sitio web comercial.
- Se necesita reunir en un solo registro los datos del
  cliente, productos, fechas y pagos.
- Hace falta una consulta organizada por fecha y estado.
```

### Problema central

> La Pastelería 16 de Agosto no cuenta todavía con un módulo de gestión conectado a una base de datos que centralice la información de los pedidos, sus fechas de entrega y sus pagos, lo que dificulta realizar un seguimiento ordenado de cada encargo.

---

##  Objetivos

###  Objetivo general

Desarrollar un sistema web de gestión de pedidos para la Pastelería 16 de Agosto que permita registrar, almacenar, organizar y consultar la información de los clientes, productos, fechas de entrega y pagos, facilitando el seguimiento de cada encargo y mejorando el control de la información del negocio.

###  Objetivos específicos

1. Analizar las necesidades de la propietaria respecto al registro, seguimiento y consulta de los pedidos.
2. Diseñar una base de datos que almacene la información de los clientes, productos, pedidos, fechas de entrega y pagos.
3. Implementar un módulo para registrar los pedidos con los datos necesarios del cliente y las características de los productos solicitados.
4. Desarrollar consultas y filtros que permitan visualizar los pedidos por fecha de entrega y estado.
5. Incorporar el registro de adelantos, pagos realizados y saldos pendientes de cada pedido.
6. Realizar pruebas para comprobar el registro, almacenamiento, modificación y consulta correcta de la información.

---

##  Justificación

###  Justificación práctica

El sistema permitirá reunir en un solo lugar la información de los pedidos de la Pastelería 16 de Agosto. La propietaria podrá registrar los datos del cliente, los productos solicitados, las cantidades y las fechas de entrega. También podrá revisar qué encargos están pendientes, cuáles se encuentran en preparación y cuáles ya fueron entregados.

El registro de adelantos y saldos pendientes ayudará a tener un mejor control de los pagos relacionados con cada pedido. De esta manera, se busca reducir las dificultades que pueden presentarse al consultar información guardada en distintos registros.

###  Justificación técnica

Se propone desarrollar una aplicación web que pueda utilizarse desde un navegador en una computadora o teléfono celular. Para el almacenamiento permanente de la información se plantea utilizar **PHP 8 y MySQL**. Durante el desarrollo se podrá utilizar **XAMPP** como entorno de servidor local para programar y realizar las pruebas.

La propuesta complementa el frontend ya elaborado con tecnologías HTML5, CSS3 y JavaScript. PHP permitirá procesar las operaciones del sistema y MySQL almacenará los datos de forma estructurada. Para publicar el módulo será necesario utilizar un servicio de alojamiento compatible con PHP y MySQL, ya que GitHub Pages aloja páginas estáticas y no ejecuta PHP.

###  Justificación social

El sistema beneficiará principalmente a Karen, propietaria de la Pastelería 16 de Agosto, al facilitar la organización y consulta de los encargos. También puede favorecer a los clientes, porque permitirá llevar un mejor seguimiento de sus pedidos, fechas de entrega y pagos, contribuyendo a una atención más ordenada y confiable.

---

##  Factibilidad

###  Factibilidad técnica

El proyecto es técnicamente viable porque se cuenta con un frontend desarrollado y publicado que puede servir como punto de partida. Para el nuevo módulo se propone utilizar:

- **HTML5 y CSS3:** estructura y presentación de las pantallas.
- **JavaScript:** interacciones y validaciones en el navegador.
- **PHP 8:** procesamiento de registros, consultas y operaciones del sistema.
- **MySQL:** almacenamiento de clientes, productos, pedidos y pagos.
- **XAMPP:** entorno local para el desarrollo y las pruebas.
- **Navegador web:** acceso desde una computadora o teléfono celular.

La publicación del módulo de gestión deberá realizarse en un hosting que admita PHP y MySQL. El sitio estático actual puede mantenerse publicado en GitHub Pages y enlazarse con el módulo alojado en ese servicio.

###  Factibilidad operativa

El sistema estará dirigido principalmente a la propietaria y a las personas que atienden los pedidos. Se plantea una interfaz sencilla, con operaciones principales como registrar un pedido, consultar los encargos del día, actualizar su estado y revisar los pagos.

Antes de su puesta en funcionamiento se deberá explicar a la cliente cómo registrar y consultar la información. También será importante que los pedidos se ingresen al sistema en el momento en que se reciben, para mantener los datos actualizados.

**Riesgo operativo:** si los encargos continúan anotándose por separado y se registran en el sistema mucho tiempo después, la información podría quedar incompleta. Para reducir este riesgo, el módulo deberá ser accesible desde el dispositivo utilizado en el negocio y sus pantallas deberán ser fáciles de manejar.

###  Factibilidad económica

El desarrollo se realizará como parte del Proyecto Integrador del programa académico. Para la publicación se consideran los siguientes costos estimados que aparecen en el borrador inicial:

| Concepto | Costo anual estimado |
|---|---:|
| Hosting compartido compatible con PHP y MySQL | Bs 350 |
| Dominio .bo | Bs 250 |
| **Total estimado** | **Bs 600** |

Estos montos son estimaciones del borrador y deberán verificarse con proveedores antes de contratar el servicio. El costo final puede variar según el plan de alojamiento, el dominio elegido y las condiciones del proveedor.

No se incluye como ahorro comprobado una cantidad de pedidos perdidos ni una pérdida económica específica, porque esos datos no están respaldados por la memoria técnica disponible.

---

##  Alcances y límites

###  Alcance

El sistema propuesto contempla las siguientes funciones:

- Registrar los datos básicos del cliente.
- Registrar pedidos con productos, cantidades y fecha de entrega.
- Consultar los pedidos almacenados.
- Filtrar los pedidos por fecha de entrega y estado.
- Actualizar el estado de un pedido, por ejemplo: pendiente, en preparación o entregado.
- Registrar el precio total, los adelantos y los saldos pendientes.
- Consultar el catálogo de productos administrado desde la base de datos.
- Realizar copias de respaldo de la información almacenada.

###  Límites

Para mantener el proyecto dentro de un alcance realizable, no se contempla inicialmente lo siguiente:

- **Facturación electrónica.** El sistema llevará el control interno de los importes y pagos, pero no emitirá facturas electrónicas ni se integrará con sistemas tributarios.
- **Control completo de inventario e insumos.** El enfoque principal será la gestión de pedidos; no se desarrollará un módulo integral de almacén o control de materias primas.
- **Notificaciones automáticas.** No se enviarán mensajes automáticos por WhatsApp, SMS o correo electrónico. Esta función podrá considerarse en una ampliación futura.
- **Múltiples sucursales.** La propuesta está orientada al local de la Pastelería 16 de Agosto en Colquencha.
- **Pasarela de pagos en línea.** El sistema registrará los pagos comunicados por el negocio, pero no procesará transacciones bancarias.

---
<!-- ── Cronograma (subtema 2.8) ──────────────────────────────────────── -->
## Cronograma de actividades

### Descomposición del trabajo

```
1. Propuesta
   1.1 Formulación del problema
   1.2 Objetivos y justificación
   1.3 Factibilidad, alcances y límites
   1.4 Cronograma

2. Análisis
   2.1 Instrumento de recolección y entrevista
   2.2 Marco teórico
   2.3 Requerimientos funcionales y no funcionales
   2.4 Historias de usuario

3. Construcción
   3.1 Modelo de datos y base de datos creada
   3.2 Endpoints de registro y consulta
   3.3 Frontend conectado al backend

4. Verificación y cierre
   4.1 Matriz de casos de prueba ejecutada
   4.2 Respaldo y plan de puesta en producción
   4.3 Documento final y defensa
```

### Cronograma

| Semana | Paquete | Entregable |
|---|---|---|
| 1 | 1.1 a 1.4 | Propuesta completa **(Lab 1)** |
| 2 | 2.1 a 2.4 | Marco teórico y requerimientos **(Lab 2)** |
| 3 | 3.1 a 3.3 | Sistema funcionando con base de datos **(Lab 3)** |
| 4 | 4.1 a 4.3 | Sistema respaldado y documento final |

<!-- ── Resumen e introducción (subtemas 2.1 y 2.2) ───────────────────── -->
## Resumen

La Pastelería 16 de Agosto es un emprendimiento familiar .Ubicado en la plaza principal del municipio de Colquencha, Actualmente la propietaria registra los pedidos de los clientes de forma manual en un cuaderno físico. Para revisar las reservas debe buscar entre las anotaciones la informacion  de cada cliente, los productos solicitados y las fechas de entregal, según la propietaria de la pasteleria el extravío de hojas del cuaderno puede ocasionar pérdidas económicas y dificultades para recuperar la información de cada pedido

El presente proyecto propone desarrollar un sistema web de gestión de pedidos que complemente el sitio comercial de la pastelería, el cual ya fue elaborado en modulo anterio, permitirá registrar clientes pedidos y almacenar los datos en una base de datos MySQL, consultar las reservas por fecha y controlar los  adelantos y saldos pendientes. Para su desarrollo se plantea utilizar PHP y MySQL.

Se realizarán pruebas de registro, consulta, actualización y almacenamiento de la información. Se espera facilitar la organización de los pedidos y reducir la dependencia del cuaderno físico.


## Introducción


El presente proyecto nace de la necesidad de mejorar la manera en que se organizan los pedidos de la Pastelería 16 de Agosto, un emprendimiento familiar ubicado en la plaza principal del municipio de Colquencha, en la avenida Samuel 002. Anteriormente, como parte del módulo de Programación Web, se desarrolló una página web para este negocio, donde los clientes pueden conocer los diferentes productos que ofrece la pastelería. Consultar sus precios y horarios de atención, Este trabajo representa un primer paso para aprovechar la tecnología y dar a conocer mejor el negocio.

Actualmente, la propietaria registra los pedidos en un cuaderno físico, lo que en ocasiones dificulta encontrar rápidamente la información de los clientes, los productos solicitados y las fechas de entrega. Frente a esta situación. Se propone desarrollar un sistema web que complemente la página existente y permita registrar, organizar y consultar los pedidos de una manera más sencilla. También permitirá llevar un mejor control de los adelantos y saldos pendientes, para ello se utilizarán PHP y MySQL, buscando que la propietaria pueda administrar los pedidos con mayor facilidad y dedicar menos tiempo a buscar información en sus apuntes.














