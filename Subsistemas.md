# Subsistemas en X-Road

## ¿Qué es un subsistema?

En el contexto de **X-Road**, un **subsistema** es el mecanismo utilizado para **agrupar y organizar los servicios de transferencia de datos**.  

Los subsistemas son esenciales porque:  
- Permiten identificar los **proyectos de interoperabilidad** de cada institución.  
- Funcionan como el medio por el cual las entidades pueden **otorgarse accesos** entre sí.  
- Agrupan los servicios de una manera ordenada y estandarizada.  

Todos los miembros de la plataforma pueden visualizar los subsistemas creados por los demás miembros.  
Cada subsistema creado debe pasar por un proceso de **aprobación en el Servidor Central**, lo que garantiza la correcta construcción del catálogo de servicios de interoperabilidad.  

---

## Criterios para la creación de un subsistema

Un subsistema debe cumplir los siguientes requisitos:

1. **Nombre descriptivo del proyecto** (muy importante).  
2. Escribirlo **totalmente en mayúsculas**.  
3. **No debe contener espacios ni caracteres especiales**  
Ejemplo no permitido: `PROYECTO*&$#@!`  
4. Evitar abreviaturas poco claras.  

> **Nota importante:**  
> El nombre debe ser **muy descriptivo** y corresponder al proyecto relacionado.  
> No se permiten nombres ambiguos o genéricos como:  
> - `PRODUCCION`, `PRUEBA`, `TEST`, `PROD`, `PRD`, `QA`  
> Tampoco nombres que contengan palabras como:  
> - `API`, `DATOS`, `DATA`, `INFORMACION`, `INFO`  
> 
> Estos serán rechazados por los operadores del Servidor Central, dejando el subsistema inutilizable.  

---

## Crear un subsistema

1. Acceda a la pestaña **Clients**.  
2. En la primera fila, encontrará su institución como cliente. Haga clic en **Add Subsystem**.  
<img width="1870" height="1002" alt="image" src="https://github.com/user-attachments/assets/11a24a31-0a92-459b-8152-81d787d1da36" />

3. Complete el campo **Subsystem Code** con el nombre del subsistema.  
   - Debe estar en **MAYÚSCULAS**.  
   - No debe contener espacios ni caracteres especiales.  
<img width="1280" height="687" alt="image" src="https://github.com/user-attachments/assets/9c652978-09c4-4de6-adb5-09842b3a3a0d" />



4. Verifique que la opción de **registrar subsistema** esté activa.  
5. Haga clic en **Add Subsystem**.  
<img width="1871" height="1004" alt="image" src="https://github.com/user-attachments/assets/89cfb419-8a95-4677-9730-b0637b5b777c" />


---

## Registro en el Servidor Central

- Registrar el subsistema en el Servidor Central es **opcional al inicio**, pero **indispensable para interoperar**.  
- Un subsistema **no podrá ser utilizado** hasta que se encuentre **aprobado por el Servidor Central**.  
- Una vez agregado, debe enviar un **registro de subsistema** que será revisado por un operador.  
- El registro solo se aprueba si cumple con las **convenciones de nombres** descritas anteriormente.  

---

## Incidencias más frecuentes

- **Error al registrar el subsistema:**  
  - El subsistema se crea localmente, pero no se envía al Servidor Central.  
  - Posibles causas:  
    - Fallo de conexión con el Servidor Central (`cs.xroad.digital.gob.do`).  
    - El **certificado de autenticación** se encuentra deshabilitado.  

- **Nombre no válido:**  
  - El subsistema no cumple con el estándar de nombres descrito en esta guía.  

---

## Próximo paso

Una vez creada la estructura de **subsistemas**, puede continuar con la [**creación de servicios**](/Crear_servicio.md) dentro de ellos.  
