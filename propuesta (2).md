# Sistema de gestión de pedidos para la Pasteleria 16 de agosto

**Propuesta de Proyecto Integrador**
Programa Académico Desconcentrado "Técnico Superior en Informática"
UMSA · Sede Colquencha

Autor: [Maura Mamani Fernandez]
Fecha: noviembre de 2026

---

<!-- ── QUÉ TIPO DE PROYECTO ES ESTE (subtemas 1.1 a 1.5) ──────────────── -->
## Tipo de proyecto

**Proyecto integrador.** Se resuelve un problema concreto de un cliente real
construyendo un producto de software funcional, acompañado de la documentación
de ingeniería que respalda las decisiones tomadas.

No es una monografía: no se estudia el estado del arte de los sistemas de
pedidos, se construye uno. No es una investigación: no se responde una pregunta
abierta, se resuelve un problema conocido.

---

## El punto de partida

Este proyecto continúa el trabajo del módulo de Programación Web, en el que se
construyó el frontend: una página funcional, publicada, con los datos del
cliente en un archivo JSON.

Para completar el proyecto falta lo siguiente:

| Ya existe | Se construye este módulo |
|---|---|
| el frontend funcionando y publicado | la propuesta que lo justifica |
| los datos en un archivo JSON | una base de datos real |
| "funciona en mi máquina" | requerimientos, pruebas, costos y *deploy* (puesta en producción) |

<!-- ── EL CLIENTE ─────────────────────────────────────────────────────── -->
## El cliente

**Pasteleria 16 de agosto**,Av.Santa Cruz, Colquencha. Negocio familiar de
dos personas, en funcionamiento desde 2008. Vende pasteles, artesanales y repostería
al público y por encargo.

**Cómo trabaja hoy:** los encargos se anotan en un cuaderno sobre el mostrador.
Quien atiende escribe el nombre, el producto, la cantidad y la fecha de
entrega. No hay copia ni respaldo.

**Fuente de esta información:** entrevista con la propietaria, 12 de octubre de
2026, en el local. Se registró en notas y se validó con ella al día siguiente.

---

<!-- ── FORMULACIÓN DEL PROBLEMA (subtema 2.3) ────────────────────────── -->
## Formulación del problema

La Pasteleria de 16 de agosto , registra los pedidos por encargo en un cuaderno físico
ubicado sobre el mostrador.Quien atiende anota el nombre del cliente, el
producto, la cantidad y la fecha de entrega. sin enbargo estos datos perdidos ocurre por falta de la organizacion del propietario

Este registro presenta tres dificultades documentadas durante la entrevista del
13 de noviembre de 2026:

**Pérdida de pedidos.** Se registra en cuaderno. Al año tres hojas se perdieron, Entre ellas se encontraba los 10 pedidos que no fueron preparados en la fecha requirida.. La propietaria identificó los casos al
recibir reclamos de clientes.

 e

**Imposibilidad de consulta.** Para saber qué hay que hornear un día
determinado, es necesario recorrer el cuaderno hoja por hoja, porque los
pedidos se anotan en orden de llegada y no por fecha de entrega. La propietaria
estima entre 15 y 20 minutos diarios en esta revisión.

**Ausencia de respaldo.** El cuaderno es el único registro. En julio de 2025 se
mojó parcialmente y se perdieron los encargos de una semana, que hubo que
reconstruir llamando a los clientes.

<!-- ── EL ÁRBOL DE PROBLEMAS ──────────────────────────────────────────── -->
### Árbol de problemas

```
   EFECTOS      Clientes insatisfechos que no vuelven
                Pérdida de ingresos por pedidos no entregados
                Tiempo del personal dedicado a reconstruir información
                          ↑
   PROBLEMA     El registro de pedidos por encargo no permite consultar
   CENTRAL      de forma confiable qué debe prepararse cada día
                          ↑
   CAUSAS       Los pedidos se anotan en orden de llegada, no por fecha
                El registro es único y no tiene copia
                La revisión diaria depende de que alguien se acuerde
```

### Problema central

> El registro de pedidos por encargo de la Panadería del Barrio no permite
> consultar de forma confiable qué debe prepararse cada día, lo que ocasiona
> pedidos no entregados y tiempo dedicado a revisar información dispersa.

---

*(Este documento continúa el Día 3 con los objetivos y la justificación.)*




¿como registra los pedidos y  que informacion registra?

¿Alguna vez tuvo confusiones con los pagos de los clientes explique que confuciones?



Qué porcentaje del precio total del pastel solicita como adelanto a sus clientes?




¿Durante el último año, ¿cuántas hojas o registros  se extraviaron y cuántos pedidos estaban anotados aproximadamente en cada hoja?

¿Cuántas veces tuvo que volver a preguntar a un cliente los detalles de su pedido por falta de información?

¿cuanto estima que tendra de perdida en esta graduacion 2026 por que motivos? 


## Objetivos

### Objetivo general

Desarrollar un sistema web de gestión de pedidos para la Pastelería 16 de Agosto, que permita registrar, organizar y consultar los pedidos de los clientes, las fechas de entrega y los datos económicos, facilitando el control de la información y evitando la pérdida de registros.


### Objetivos específicos

1. Diseñar una base de datos que permita almacenar la información de los clientes, productos, pedidos, fechas de entrega y datos económicos.
2. Implementar un módulo de registro de pedidos que permita guardar la información de cada cliente y las características del pastel solicitado.
3. Desarrollar una función de consulta que permita buscar y visualizar los pedidos registrados, según la fecha de entrega y el estado del pedido.
4. Implementar un módulo de control económico que permita registrar los adelantos y pagos pendientes de los clientes.
5. Realizar pruebas de funcionamiento para verificar que el sistema registre, almacene y consulte correctamente la información.




<!-- ── Justificación (subtema 2.4) ───────────────────────────────────── -->
## Justificación

**Práctica.**  La implementacion del sistema web permitira solucionar las dificultades que presenta la pasteleria al registrar los pedidos, las fechas de entrega y los datos economicos en un cuaderno. Actualmente, esta informacion se encuentra registrada manualmente, lo que dificulta su busqueda y aumenta el riesgo de perder datos cuando se extravian las hojas. Con el sistema se podra mantener la informacion organizada y consultar los pedidos de manera rapida.

**Técnica.** Se desarrollara una aplicacion web que permitira acceder al registro de pedidos desde diferentes dispositivos, como celulares y computadoras. Se utilizara una base de datos para almacenar la informacion de forma organizada y facilitar su consulta, evitando depender unicamente de los registros escritos en un cuaderno. Se usara PHP Y MySQL porque  funciona sobre hostig compartido de bajo costo ya que es accesible para  un negocio de este tamaño.


**Social.** El sistema beneficiará al propietario de la Pastelería 16 de Agosto, porque facilitará la atención y el seguimiento de los pedidos de los clientes. También permitirá tener un mejor control de las fechas de entrega, los adelantos y los pagos pendientes, contribuyendo a brindar un servicio más organizado y confiable.
---

*(Este documento continúa el Día 4 con la factibilidad, los alcances y los límites.)*<!-- ── Factibilidad (subtema 2.6) ────────────────────────────────────── -->
## Factibilidad

**Técnica.**  
El sistema de gestion de pedidos se desarrollara utilizando PHP 8 y MySQL para almacenar y administrar la informacion de los clientes, productos y pedidos. Durante el desarrollo se utilizara XAMPP como servidor local para realizar las pruebas y verificar el funcionamiento del sistema.
Para su utilizacion, el sistema estara disponible mediante un navegador web y podra accederse desde una computadora o un telefono celular con conexion a internet. No sera necesario instalar programas adicionales en los dispositivos de los usuarios.

**Operativa.** El sistema sera utilizado por el propietario y el personal encargado de atender los pedidos de la Pasteleria 16 de Agosto.ambas con
telefono con navegador y experiencia usando aplicaciones de mensajeria y banca
movil. La operacion diaria se reduce a registrar un pedido y consultar la lista
del dia, dos acciones que se resuelven en una pantalla cada una.



*Riesgo identificado:* el registro depende de que se cargue el pedido en el
momento. Si se sigue anotando en el cuaderno "para pasarlo después", el sistema
no resuelve nada. Se mitiga dejando el registro accesible desde el celular del
mostrador, sin instalar nada.

**Económica.** El desarrollo se realiza como parte del módulo, sin costo para
el cliente. La operación anual estimada es:

| Concepto | Costo anual (Bs) |
|---|---|
| Hosting compartido con PHP y MySQL | 350 |
| Dominio .bo | 250 |
| **Total** | **600** |

Frente a eso, los 12 pedidos no entregados en marzo, a un ticket promedio de
Bs 35 según la propietaria, representan unos Bs 420 en un solo mes.

<!-- ── Alcances y límites (subtema 2.7) ──────────────────────────────── -->
## Alcances y límites

### Alcance

El sistema entregado incluye:

- registro de un pedido con cliente, producto, cantidad y fecha de entrega
- consulta de los pedidos pendientes filtrados por fecha
- marcado de un pedido como entregado
- listado de productos, administrable desde la base de datos
- respaldo del registro mediante exportación de la base de datos

### Límites

El sistema **no** incluye, y en cada caso se indica por qué:

- **Cobros ni facturación.** La panadería factura con talonario manual, y la
  facturación electrónica en Bolivia exige integración con el sistema de
  Impuestos Nacionales, que excede el alcance de un módulo de cuatro semanas.
- **Gestión de inventario ni de insumos.** El problema formulado es la pérdida
  de pedidos, no el control de stock. Incluirlo duplicaría el tamaño del
  proyecto sin atacar el problema central.
- **Notificaciones automáticas al cliente.** Requiere integración con un
  servicio de mensajería de pago. Queda planteado como recomendación.
- **Múltiples sucursales.** El negocio tiene un solo local. El diseño de la
  base de datos no impide agregarlo después, pero no se implementa.

---