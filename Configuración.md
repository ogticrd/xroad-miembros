# Guía de Configuración del Servidor de Seguridad X-Road

## Antes de iniciar
Asegúrese de haber completado el proceso de **instalación** correctamente y de haber seguido la **guía técnica de preparación para la configuración**.

## Acceso inicial

1. Abra un navegador web e ingrese a la interfaz del Servidor de Seguridad en la siguiente ruta: `https://<subdominio>:4000`

- El puerto **4000** es el que viene configurado por defecto.  
- Si utilizó otro puerto en la instalación, debe ingresar ese.

2. Inicie sesión utilizando las credenciales configuradas en su archivo `.env`:  
- **XROAD_ADMIN_USER**  
- **XROAD_ADMIN_PASSWORD**  
<img width="1869" height="919" alt="image" src="https://github.com/user-attachments/assets/5a8e67e8-b0fc-472d-bb95-0a303aa09493" />

## Cargar Ancla de Configuración

1. Localice el archivo XML llamado [ancla de configuración](/configuration_anchor_DO_internal_UTC_2023-06-13_22_02_45.xml), disponible en el repositorio o carpeta de instalación.  
2. Desde la interfaz web, haga clic en **Buscar**, seleccione el archivo y confirme la carga.  

> Nota: Si el mensaje de confirmación queda cargando y no continúa, probablemente exista un problema de comunicación entre su servidor y el **Servidor Central**. Verifique conectividad antes de continuar.
<img width="1872" height="1011" alt="image" src="https://github.com/user-attachments/assets/b0e76445-1527-4144-a1fb-85b3fdb9e1af" />

## Registro de Miembro

Complete el formulario con los siguientes campos:

- **Clase de miembro:** Seleccione `GOB` para entidades estatales.  
- **Código de miembro:** Ingrese las siglas oficiales de su institución.  
- Ejemplo:  
 - Nombre: Junta Central Electoral → Siglas: `JCE`  
 - Nombre: Ministerio de Salud Pública → Siglas: `MSP`  

> Nota: Si el nombre de la institución no aparece automáticamente, el registro podría fallar. En ese caso, comuníquese a: `interoperabilidad@ogtic.gob.do`.  

- **Código del servidor de seguridad:** Ingrese `SS` seguido del número de orden de su servidor.  
- Ejemplo: `SS1`, `SS2`, `SS3`.  
<img width="1871" height="1007" alt="image" src="https://github.com/user-attachments/assets/408c7af4-a4d6-48c6-971c-fddaae379040" />

## Configuración del PIN

Ingrese el **PIN de seguridad** definido en el archivo `.env` (variable `XROAD_TOKEN_PIN`).  
Debe repetir el PIN en ambos campos y luego presionar **Continuar**.  

> Es importante que el PIN coincida exactamente con el configurado durante la instalación, ya que garantiza el acceso seguro a las llaves y certificados.

<img width="1869" height="1000" alt="image" src="https://github.com/user-attachments/assets/3ad1e1c3-e120-47d5-a607-7d8305006bbe" />

## Configuración del servicio de sellado de tiempo

1. Elija Configuración -> Parámetros del sistema -> Servicios de marca de tiempo -> Agregar.
2. Elija el servicio de marca de tiempo de la lista.
3. Presione Agregar.

   <img width="1280" height="689" alt="image" src="https://github.com/user-attachments/assets/9c0549bf-1153-4d5c-903a-2066694b1027" />

## Generación de Llaves y Certificados

1. Vaya a la sección **Keys and Certificates**.  
2. Localice el **Soft Token** (almacén de llaves), luego se debe dar click en el boton a la derecha del Soft Token que dice “Log in” y colocar el PIN. Si dice “Log out” es porque actuamente el Soft Token se encuentra listo para ser utilizado.

<img width="1872" height="1003" alt="image" src="https://github.com/user-attachments/assets/7489ec66-1653-4695-96e0-2865b5e603ca"/> 

### Crear llave de autenticación
- Haga clic en **Add Key**.  
- Defina un *label* (ejemplo: `AUTH`).  
- En **Usage** seleccione: `Authentication`.  
- En **Server DNS Name**, coloque el subdominio (ej: `ss1.institucion.gob.do`).  
- En **Country Code**, coloque `DO`.  
- Genere el CSR (**Generate CSR**) y descárguelo.  
<img width="1920" height="1038" alt="image" src="https://github.com/user-attachments/assets/92ab50b4-c6bf-437f-9cd7-825a1d34ccb1" />

### Crear llave de firma
- Haga clic nuevamente en **Add Key**.  
- Defina un *label* (ejemplo: `SIGN`).  
- En **Usage** seleccione: `Signing`.  
- En **Client**, seleccione la opción disponible.
  <img width="1869" height="1006" alt="image" src="https://github.com/user-attachments/assets/b0cff9c2-3010-40e2-b019-5868739471f2" />
  
- En **Country Code**, coloque `DO`.  
- Genere el CSR (**Generate CSR**) y descárguelo.

3. Comprima ambos archivos CSR en un **.zip**.  
4. Envíe el archivo a:  
- `interoperabilidad@ogtic.gob.do`  
- Copia a: `kevin.jimenez@ogtic.gob.do`  

5. Espere la devolución de los certificados firmados por la misma vía.

## Importación de Certificados

1. Una vez recibidos los certificados firmados, impórtelos en la misma sección **Keys and Certificates**.
   <img width="1867" height="1006" alt="image" src="https://github.com/user-attachments/assets/2d10e089-ff32-4436-b10e-0a7920b125b6" />

3. Active el **certificado de autenticación**.
  <img width="1863" height="1000" alt="image" src="https://github.com/user-attachments/assets/2cc9138e-5218-4f37-8210-c1ec0193bed3" />

5. Registre el servidor haciendo clic en **Register** y colocando el subdominio (ej: `ss1.institucion.gob.do`).
   <img width="1872" height="1005" alt="image" src="https://github.com/user-attachments/assets/adc46b91-25dd-4d87-9116-a2a41944140d" />
   
6. La solicitud de registro del certificado de autenticación se envía al servidor central. El certificado pasa al registro estatal en curso.
   <img width="1872" height="1004" alt="image" src="https://github.com/user-attachments/assets/3981681a-c7c3-45cc-ac40-b2a9134e4748" />


> Este paso envía la solicitud al **Servidor Central**, donde un operador verificará y aprobará el registro.  



## Conclusión

En este punto ha completado la **configuración general** de su Servidor de Seguridad.  
A partir de aquí, podrá comenzar a [**registrar subsistemas y servicios**](/Subsistemas.md) según las necesidades de su institución.  











 
