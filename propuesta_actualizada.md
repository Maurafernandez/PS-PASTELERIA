# Sistema web de gestión de pedidos para la Pastelería 16 de Agosto

**Propuesta de Proyecto Integrador**  
Programa Académico Desconcentrado: Técnico Superior en Informática  
UMSA · Sede Colquencha

- **Estudiante:** Maura Mamani Fernandez
- **Cliente:** Karen, propietaria de la Pastelería 16 de Agosto
- **Ubicación del negocio:** Plaza principal de Colquencha, Av. Samuel 002
- **Fecha:** noviembre de 2026

---

## 1. Tipo de proyecto

**Proyecto integrador de desarrollo de software.** El proyecto plantea ampliar el trabajo realizado en el módulo de Programación Web mediante el diseño y desarrollo de un sistema que permita administrar los pedidos de la Pastelería 16 de Agosto.

El trabajo parte de un sitio web comercial que ya fue desarrollado y publicado. La propuesta se enfoca en complementar esa primera versión con una solución para registrar, organizar, consultar y dar seguimiento a los pedidos, incluyendo las fechas de entrega y la información de los pagos.

No se trata únicamente de una página informativa: se busca construir una herramienta funcional que responda a necesidades del negocio y que esté acompañada de su documentación, pruebas y puesta en funcionamiento.

---

## 2. Antecedentes y punto de partida

En el módulo de Programación Web se desarrolló el sitio comercial de la Pastelería 16 de Agosto, publicado en GitHub Pages:

**Sitio web existente:**  
https://maurafernandez.github.io/PROYECTO-PASTELERIA-16/

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

## 3. Descripción del cliente y del negocio

La **Pastelería 16 de Agosto** es un emprendimiento ubicado en la plaza principal del municipio de Colquencha, en la Av. Samuel 002. La propietaria identificada para el proyecto es **Karen**.

El negocio ofrece productos de pastelería y repostería, entre ellos pasteles, masitas, alfajores, bizcochos, galletas y queques. También se contempla la preparación de bandejas de pasteles personalizados con diferentes sabores.

El sitio web desarrollado en el módulo anterior se planteó para ayudar a difundir los productos, mostrar sus precios y horarios de atención y facilitar el contacto para realizar encargos.

**Fuente de los datos generales:** memoria técnica del sitio web de la Pastelería 16 de Agosto, elaborada en octubre de 2026.

> **Nota para completar con la entrevista:** la memoria técnica no especifica de manera verificable cuántas personas trabajan actualmente en el negocio, el año exacto de inicio de actividades ni todos los pasos que sigue la propietaria para registrar cada encargo. Estos datos deben confirmarse directamente con la cliente antes de presentar la versión definitiva.

---

## 4. Formulación del problema

La Pastelería 16 de Agosto necesita contar con una forma más organizada de administrar los pedidos que realizan sus clientes. El sitio web comercial ya permite presentar los productos y ofrece un formulario para solicitar encargos; sin embargo, la memoria técnica del proyecto no acredita que exista una base de datos conectada que conserve los pedidos y permita administrarlos de manera permanente.

Cuando la información de los encargos no se encuentra centralizada, puede resultar más difícil revisar qué productos se deben preparar, para qué fecha se necesitan y qué pagos se han realizado. Además, si los datos quedan únicamente en registros manuales o temporales, existe el riesgo de que no estén disponibles cuando se necesiten.

Por esta razón, se propone desarrollar un sistema web que permita registrar los datos del cliente, los productos solicitados, las cantidades, las fechas de entrega y los importes económicos relacionados con cada pedido. El sistema facilitará la consulta de los encargos y su seguimiento hasta la entrega.

### 4.1. Dificultades que se busca atender

1. **Organización de los pedidos.** Se necesita reunir los datos de cada encargo en un registro ordenado para evitar depender de anotaciones dispersas.
2. **Consulta por fecha de entrega.** Se requiere identificar con facilidad qué pedidos deben prepararse o entregarse en un día determinado.
3. **Seguimiento del estado.** Es conveniente distinguir los pedidos pendientes, en preparación y entregados.
4. **Control de pagos.** Se necesita registrar el precio total, los adelantos recibidos y el saldo pendiente de cada pedido.
5. **Conservación de la información.** Una base de datos permitirá guardar los registros para consultarlos posteriormente y realizar copias de respaldo.

Estas necesidades constituyen el enfoque de la propuesta. Las cantidades exactas de pedidos extraviados, pérdidas económicas o confusiones de pago no están confirmadas en la memoria técnica y no se presentan como datos comprobados.

### 4.2. Árbol de problemas

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

### 4.3. Problema central

> La Pastelería 16 de Agosto no cuenta todavía con un módulo de gestión conectado a una base de datos que centralice la información de los pedidos, sus fechas de entrega y sus pagos, lo que dificulta realizar un seguimiento ordenado de cada encargo.

---

## 5. Objetivos

### 5.1. Objetivo general

Desarrollar un sistema web de gestión de pedidos para la Pastelería 16 de Agosto que permita registrar, almacenar, organizar y consultar la información de los clientes, productos, fechas de entrega y pagos, facilitando el seguimiento de cada encargo y mejorando el control de la información del negocio.

### 5.2. Objetivos específicos

1. Analizar las necesidades de la propietaria respecto al registro, seguimiento y consulta de los pedidos.
2. Diseñar una base de datos que almacene la información de los clientes, productos, pedidos, fechas de entrega y pagos.
3. Implementar un módulo para registrar los pedidos con los datos necesarios del cliente y las características de los productos solicitados.
4. Desarrollar consultas y filtros que permitan visualizar los pedidos por fecha de entrega y estado.
5. Incorporar el registro de adelantos, pagos realizados y saldos pendientes de cada pedido.
6. Realizar pruebas para comprobar el registro, almacenamiento, modificación y consulta correcta de la información.

---

## 6. Justificación

### 6.1. Justificación práctica

El sistema permitirá reunir en un solo lugar la información de los pedidos de la Pastelería 16 de Agosto. La propietaria podrá registrar los datos del cliente, los productos solicitados, las cantidades y las fechas de entrega. También podrá revisar qué encargos están pendientes, cuáles se encuentran en preparación y cuáles ya fueron entregados.

El registro de adelantos y saldos pendientes ayudará a tener un mejor control de los pagos relacionados con cada pedido. De esta manera, se busca reducir las dificultades que pueden presentarse al consultar información guardada en distintos registros.

### 6.2. Justificación técnica

Se propone desarrollar una aplicación web que pueda utilizarse desde un navegador en una computadora o teléfono celular. Para el almacenamiento permanente de la información se plantea utilizar **PHP 8 y MySQL**. Durante el desarrollo se podrá utilizar **XAMPP** como entorno de servidor local para programar y realizar las pruebas.

La propuesta complementa el frontend ya elaborado con tecnologías HTML5, CSS3 y JavaScript. PHP permitirá procesar las operaciones del sistema y MySQL almacenará los datos de forma estructurada. Para publicar el módulo será necesario utilizar un servicio de alojamiento compatible con PHP y MySQL, ya que GitHub Pages aloja páginas estáticas y no ejecuta PHP.

### 6.3. Justificación social

El sistema beneficiará principalmente a Karen, propietaria de la Pastelería 16 de Agosto, al facilitar la organización y consulta de los encargos. También puede favorecer a los clientes, porque permitirá llevar un mejor seguimiento de sus pedidos, fechas de entrega y pagos, contribuyendo a una atención más ordenada y confiable.

---

## 7. Factibilidad

### 7.1. Factibilidad técnica

El proyecto es técnicamente viable porque se cuenta con un frontend desarrollado y publicado que puede servir como punto de partida. Para el nuevo módulo se propone utilizar:

- **HTML5 y CSS3:** estructura y presentación de las pantallas.
- **JavaScript:** interacciones y validaciones en el navegador.
- **PHP 8:** procesamiento de registros, consultas y operaciones del sistema.
- **MySQL:** almacenamiento de clientes, productos, pedidos y pagos.
- **XAMPP:** entorno local para el desarrollo y las pruebas.
- **Navegador web:** acceso desde una computadora o teléfono celular.

La publicación del módulo de gestión deberá realizarse en un hosting que admita PHP y MySQL. El sitio estático actual puede mantenerse publicado en GitHub Pages y enlazarse con el módulo alojado en ese servicio.

### 7.2. Factibilidad operativa

El sistema estará dirigido principalmente a la propietaria y a las personas que atienden los pedidos. Se plantea una interfaz sencilla, con operaciones principales como registrar un pedido, consultar los encargos del día, actualizar su estado y revisar los pagos.

Antes de su puesta en funcionamiento se deberá explicar a la cliente cómo registrar y consultar la información. También será importante que los pedidos se ingresen al sistema en el momento en que se reciben, para mantener los datos actualizados.

**Riesgo operativo:** si los encargos continúan anotándose por separado y se registran en el sistema mucho tiempo después, la información podría quedar incompleta. Para reducir este riesgo, el módulo deberá ser accesible desde el dispositivo utilizado en el negocio y sus pantallas deberán ser fáciles de manejar.

### 7.3. Factibilidad económica

El desarrollo se realizará como parte del Proyecto Integrador del programa académico. Para la publicación se consideran los siguientes costos estimados que aparecen en el borrador inicial:

| Concepto | Costo anual estimado |
|---|---:|
| Hosting compartido compatible con PHP y MySQL | Bs 350 |
| Dominio .bo | Bs 250 |
| **Total estimado** | **Bs 600** |

Estos montos son estimaciones del borrador y deberán verificarse con proveedores antes de contratar el servicio. El costo final puede variar según el plan de alojamiento, el dominio elegido y las condiciones del proveedor.

No se incluye como ahorro comprobado una cantidad de pedidos perdidos ni una pérdida económica específica, porque esos datos no están respaldados por la memoria técnica disponible.

---

## 8. Alcances y límites

### 8.1. Alcance

El sistema propuesto contempla las siguientes funciones:

- Registrar los datos básicos del cliente.
- Registrar pedidos con productos, cantidades y fecha de entrega.
- Consultar los pedidos almacenados.
- Filtrar los pedidos por fecha de entrega y estado.
- Actualizar el estado de un pedido, por ejemplo: pendiente, en preparación o entregado.
- Registrar el precio total, los adelantos y los saldos pendientes.
- Consultar el catálogo de productos administrado desde la base de datos.
- Realizar copias de respaldo de la información almacenada.

### 8.2. Límites

Para mantener el proyecto dentro de un alcance realizable, no se contempla inicialmente lo siguiente:

- **Facturación electrónica.** El sistema llevará el control interno de los importes y pagos, pero no emitirá facturas electrónicas ni se integrará con sistemas tributarios.
- **Control completo de inventario e insumos.** El enfoque principal será la gestión de pedidos; no se desarrollará un módulo integral de almacén o control de materias primas.
- **Notificaciones automáticas.** No se enviarán mensajes automáticos por WhatsApp, SMS o correo electrónico. Esta función podrá considerarse en una ampliación futura.
- **Múltiples sucursales.** La propuesta está orientada al local de la Pastelería 16 de Agosto en Colquencha.
- **Pasarela de pagos en línea.** El sistema registrará los pagos comunicados por el negocio, pero no procesará transacciones bancarias.

---

## 9. Requerimientos principales del sistema

### 9.1. Requerimientos funcionales

| Código | Requerimiento |
|---|---|
| RF-01 | El sistema permitirá registrar los datos de un cliente. |
| RF-02 | El sistema permitirá registrar un pedido y asociarlo a un cliente. |
| RF-03 | El sistema permitirá seleccionar productos y especificar cantidades. |
| RF-04 | El sistema permitirá registrar la fecha de entrega del pedido. |
| RF-05 | El sistema permitirá consultar los pedidos registrados. |
| RF-06 | El sistema permitirá filtrar pedidos por fecha y estado. |
| RF-07 | El sistema permitirá actualizar el estado de cada pedido. |
| RF-08 | El sistema permitirá registrar adelantos y calcular o mostrar el saldo pendiente. |
| RF-09 | El sistema permitirá consultar los productos disponibles en el catálogo. |
| RF-10 | El sistema permitirá generar una copia de respaldo de los registros. |

### 9.2. Requerimientos no funcionales

- **Usabilidad:** las pantallas deberán ser claras y fáciles de utilizar.
- **Compatibilidad:** deberá funcionar en navegadores web actuales.
- **Adaptabilidad:** la interfaz deberá ajustarse a computadoras y teléfonos celulares.
- **Integridad:** los formularios deberán validar los datos obligatorios antes de guardar.
- **Persistencia:** los registros deberán permanecer almacenados en la base de datos.
- **Seguridad básica:** el acceso a las funciones administrativas deberá protegerse y las entradas deberán validarse en el servidor.
- **Respaldo:** se deberá contar con un procedimiento para realizar copias de seguridad de la base de datos.

---

## 10. Datos que debe administrar el sistema

De acuerdo con los objetivos de la propuesta, la información principal se organizará en los siguientes grupos:

| Grupo de datos | Información prevista |
|---|---|
| Clientes | Nombre, teléfono y datos de contacto necesarios para identificar al cliente. |
| Productos | Nombre, categoría, descripción y precio. |
| Pedidos | Cliente, fecha de registro, fecha de entrega, detalle de productos, cantidades y estado. |
| Pagos | Precio total, adelanto, pagos adicionales y saldo pendiente. |

Los campos definitivos se ajustarán después de confirmar con la propietaria qué información necesita registrar para cada encargo.

---

## 11. Preguntas pendientes para validar con la cliente

La memoria técnica del sitio web no contiene respuestas verificadas a todas las preguntas sobre el procedimiento actual de los pedidos y los pagos. Por eso, antes de cerrar el análisis se recomienda confirmar con Karen los siguientes puntos:

1. ¿Cómo registra actualmente los pedidos y qué datos anota de cada cliente?
2. ¿Qué problemas o confusiones se presentan al registrar los pagos?
3. ¿Solicita un adelanto para confirmar los pedidos? Si es así, ¿qué porcentaje o monto acostumbra solicitar?
4. ¿Cuántos pedidos recibe aproximadamente por semana o por mes?
5. ¿Qué información necesita consultar con mayor frecuencia: pedidos por fecha, por cliente, por producto o por estado?
6. ¿Quiénes utilizarán el sistema y desde qué dispositivo?
7. ¿Necesita modificar un pedido después de haberlo registrado?
8. ¿Cómo desea identificar los pedidos que ya fueron pagados y los que todavía tienen saldo pendiente?

Las respuestas permitirán precisar los requerimientos y evitar incluir cifras o situaciones que todavía no han sido confirmadas.

---

## 12. Conclusión de la propuesta

La Pastelería 16 de Agosto ya cuenta con un sitio web comercial desarrollado para mostrar sus productos y facilitar los encargos. El siguiente paso es complementar esa plataforma con un sistema de gestión conectado a una base de datos, que permita conservar y organizar la información de los clientes, pedidos, fechas de entrega y pagos.

La implementación de este módulo permitirá disponer de consultas más ordenadas y facilitará el seguimiento de cada encargo desde su registro hasta su entrega. De esta manera, el Proyecto Integrador dará continuidad al trabajo realizado en Programación Web y responderá a las necesidades de administración identificadas para el negocio.

---

## 13. Referencia del proyecto previo

La información técnica del sitio web existente se basa en el documento **“Memoria Técnica del Proyecto – Pastelería 16 de Agosto”**, correspondiente a octubre de 2026. En dicho documento se describen el catálogo, los precios registrados, las tecnologías utilizadas, la arquitectura de archivos y las funciones implementadas.

**URL del sitio publicado:**  
https://maurafernandez.github.io/PROYECTO-PASTELERIA-16/
