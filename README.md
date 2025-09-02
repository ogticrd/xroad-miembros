<img width="500" height="184" alt="image" src="https://github.com/user-attachments/assets/a66fd358-e45a-4eda-8763-e2e4cf027cc9" />

# Repositorio de miembros de la Plataforma Única de Interoperabilidad del Estado Dominicano

## INTRODUCCIÓN A XROAD Y A LA PLATAFORMA ÚNICA DE INTEROPERABILIDAD

X-Road es un marco de interoperabilidad orientado a garantizar la comunicación segura y confiable entre sistemas de distintas instituciones en entornos gubernamentales y empresariales. Su propósito principal es superar los retos que implica la integración entre entidades, ofreciendo un mecanismo estandarizado para el intercambio de datos, reduciendo costos de desarrollo, evitando duplicidad de esfuerzos y fortaleciendo la seguridad en los procesos de intercambio de información.

El ecosistema de X-Road consta de un operador de X-Road, organizaciones miembros y proveedores de servicios de confianza.

<img width="2464" height="1438" alt="image" src="https://github.com/user-attachments/assets/1ff2b2de-789e-4107-929d-7e5ba9cb868e" />


### Operador de X-Road

La OGTIC, en calidad de Operador del ecosistema X-Road en la República Dominicana, es responsable de la gestión y buen funcionamiento de la Plataforma Única de Interoperabilidad. Sus responsabilidades incluyen: definir las normativas y lineamientos de uso, aprobar y dar de alta a nuevos miembros, brindar soporte técnico y administrativo a las entidades participantes, y operar los componentes centrales del software X-Road, como el Servidor Central y el Servidor de Configuración.

### Miembros de la Plataforma Única de Interoperabilidad

Los miembros son las instituciones públicas y, en algunos casos, privadas que se incorporan a la plataforma para publicar y/o consumir servicios de manera segura con otros organismos. Una entidad puede desempeñar el rol de proveedor de servicios, consumidor de servicios, o ambos. Para integrarse, cada institución debe completar el proceso de incorporación definido por la OGTIC, lo que incluye la instalación de su Servidor de Seguridad, el componente técnico esencial que permite el intercambio de mensajes en X-Road.

### Proveedores de Servicios de Confianza

En la República Dominicana, los servicios de confianza que requiere el ecosistema X-Road son provistos directamente por la OGTIC, lo que garantiza la seguridad y confiabilidad del sistema. Estos servicios incluyen:

Autoridad de Certificación (CA): administrada por OGTIC, encargada de emitir y gestionar los certificados digitales para la autenticación y comunicación segura entre miembros.

Autoridad de Sellado de Tiempo (TSA): también administrada por OGTIC, asegura la validez temporal de las transacciones electrónicas, otorgando trazabilidad y confianza al ecosistema.

De esta forma, la OGTIC centraliza y asegura la provisión de servicios de confianza, eliminando la dependencia de terceros y fortaleciendo el marco de interoperabilidad nacional.

La presente documentación tiene como objetivo servir de guía a las entidades en el proceso de instalación, configuración e inscripción como miembros de la Plataforma Única de Interoperabilidad. Al completar estos pasos, cada institución podrá conectarse al ecosistema digital de manera segura, interoperar con otros organismos de forma ágil y confiable, y aprovechar todos los beneficios que aporta esta plataforma: eficiencia en la gestión pública, simplificación de trámites, y mayor transparencia en la prestación de servicios.

## REQUISITOS PREVIOS PARA LA INSTALACIÓN DEL SERVIDOR DE SEGURIDAD

Antes de iniciar el proceso de instalación del Servidor de Seguridad X-Road, la institución debe asegurarse de cumplir con los siguientes requisitos técnicos:
 
1. Servidor virtual con sistema operativo Ubuntu 22.04 LTS, con al menos:

- 2 a 4 CPU

- 3 a 4 GB de memoria RAM

- 20 GB de almacenamiento en disco SSD

2. Subdominio público dedicado y exclusivo para el servidor de seguridad, con una dirección IP pública fija.

- Formato sugerido: ss1.dominio.de.la.institucion

  Ejemplo: ss1.ogtic.gob.do

3.  Conectividad a Internet:

- El servidor debe tener acceso a internet para sincronizarse con el Servidor Central de la OGTIC.

4. Accesibilidad desde Internet:

- Deben estar habilitados los puertos:

  `5500` (intercambio de mensajes)

  `5577` (administración remota del servidor)

5. Accesibilidad desde la red local de la institución:

- Deben estar habilitados los puertos:

  `443` (interfaz web de administración)

  `4000` (interfaz de configuración técnica)

  ## INSTALACIÓN

### Instalación de Docker y Docker Compose

Instalaremos Docker a través de snap:

```sh 
sudo snap install docker
```
Nota: Verifique que el servicio de Docker quede activo ejecutando:
```sh
docker --version
```

### Descarga del repositorio

Clone el repositorio oficial con:
```sh
https://github.com/ogticrd/xroad-miembros.git
```
Acceda al directorio descargado:
```sh
cd xroad-miembros
```
### Configuración inicial

1. Cree el archivo de configuración a partir de la plantilla incluida:
```sh
cp .env.example .env
```
2. Edite el archivo `.env` con el editor de su preferencia:
```sh
nano .env
```
En este archivo deberá configurar al menos lo siguiente:

- PIN del token software.

- Password del usuario administrador.

### Despliegue del Servidor de Seguridad

Ejecute el siguiente comando para iniciar el despliegue:
```sh
sudo docker-compose up -d
```
Si todo se ejecuta correctamente, podrá acceder a la interfaz web del Servidor de Seguridad desde un navegador en: `https://<subdominio>:4000`

### Próximos pasos

Una vez completada la instalación, debe proceder con la [configuración del Servidor de Seguridad](/Configuración.md) y su inclusión como miembro de la plataforma X-Road.

Continúe con la [Guía de Configuración de Miembro](/Configuración.md)

## NOTAS ADICIONALES

- Si después de completar la instalación no puede visualizar la interfaz de inicio de sesión en el navegador (indicada en el último paso de la guía), diríjase a la sección de **Problemas Frecuentes**.  
- En caso de necesitar revertir todo el proceso de instalación, consulte la guía de **Desinstalación**.  

---

## Desinstalación

Si desea revertir la instalación, debe eliminar tanto el contenedor desplegado como los volúmenes que almacenan los archivos de configuración y los datos recopilados por la plataforma.  

1. Localice el directorio donde descargó el repositorio al momento de la instalación.  
2. Ingrese a ese directorio y verifique que exista el archivo `docker-compose.yml`.  
3. Ejecute el siguiente comando para eliminar todo:  

```bash
sudo docker-compose down -v
```








