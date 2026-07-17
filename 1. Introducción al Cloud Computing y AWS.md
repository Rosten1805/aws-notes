## Infraestructura tradicional

Antes del Cloud Computing, las empresas alojaban su infraestructura en:

- Centros de datos propios.
- Servidores en oficinas o instalaciones privadas.

### Problemas de la infraestructura tradicional

- Alto coste de adquisición y mantenimiento del hardware.
- Gastos en electricidad, refrigeración y espacio físico.
- Escalado lento al requerir comprar e instalar nuevos servidores.
- Necesidad de personal disponible 24/7 para el mantenimiento.
- Difícil recuperación ante desastres (incendios, terremotos, apagones...).

---

# ¿Qué es el Cloud Computing?

El **Cloud Computing** consiste en proporcionar recursos informáticos a través de Internet bajo demanda.

Entre estos recursos se incluyen:

- Servidores
- Almacenamiento
- Bases de datos
- Redes
- Aplicaciones
- Servicios de computación

## Características

- Pago únicamente por los recursos utilizados (_Pay as you go_).
- Aprovisionamiento casi inmediato.
- Escalabilidad rápida.
- Acceso desde cualquier lugar mediante Internet.

---

# AWS (Amazon Web Services)

AWS es el proveedor de servicios Cloud de Amazon.

Permite disponer de infraestructura informática sin necesidad de mantener hardware propio.

Empresas como Netflix, Airbnb, Twitch o Samsung utilizan AWS para alojar sus aplicaciones.

---

# Ejemplos de servicios Cloud que usamos diariamente

- Gmail
- Microsoft Teams
- Netflix
- Dropbox
- Zoom

---

# DevOps

DevOps es una metodología que une los equipos de desarrollo (Development) y operaciones (Operations).

Su objetivo es automatizar el desarrollo, pruebas y despliegue del software.

## Beneficios

- Mejor colaboración entre equipos.
- Entrega de software más rápida.
- Mayor estabilidad.
- Escalado más sencillo.
- Mayor calidad del software.

---

# CI/CD

CI/CD (**Continuous Integration / Continuous Delivery o Deployment**) automatiza el ciclo de vida del software.

Permite:

- Integrar cambios de código continuamente.
- Ejecutar pruebas automáticamente.
- Desplegar nuevas versiones con rapidez y seguridad.

## Fases de un Pipeline CI/CD

1. **Plan**
    - Definir objetivos y planificación.
2. **Code**
    - Desarrollo del código.
3. **Build**
    - Compilar la aplicación.
4. **Test**
    - Ejecutar pruebas automáticas.
5. **Release**
    - Preparar una versión estable.
6. **Deploy**
    - Publicar la aplicación.
7. **Operate**
    - Gestionar la aplicación en producción.
8. **Monitor**
    - Supervisar rendimiento y disponibilidad.

---

# Modelos de despliegue Cloud

## Cloud Privado

Infraestructura utilizada exclusivamente por una organización.

**Ventajas**

- Mayor control.
- Mayor seguridad.
- Personalización.

---

## Cloud Público

Infraestructura gestionada por un proveedor como AWS.

**Ventajas**

- Menor coste.
- Escalabilidad.
- Pago por uso.

---

## Cloud Híbrido

Combina infraestructura privada con servicios Cloud públicos.

Permite mantener datos sensibles localmente y aprovechar la elasticidad del Cloud.

---

# Cinco características del Cloud Computing

## 1. Autoservicio bajo demanda

Los usuarios crean y eliminan recursos sin intervención del proveedor.

---

## 2. Acceso amplio por red

Los recursos son accesibles desde cualquier dispositivo conectado.

---

## 3. Recursos compartidos

Varios clientes utilizan la misma infraestructura física de forma aislada y segura.

---

## 4. Elasticidad rápida

Los recursos aumentan o disminuyen automáticamente según la demanda.

---

## 5. Servicio medido

El consumo se registra y únicamente se paga por lo utilizado.

---

# Ventajas del Cloud

- Sustituye inversiones iniciales (CAPEX) por gastos operativos (OPEX).
- Pago por uso.
- Escalabilidad automática.
- Mayor agilidad.
- Despliegues rápidos.
- Presencia global.
- Menor carga de administración.

---

# Problemas que resuelve el Cloud

- Flexibilidad para cambiar recursos.
- Escalabilidad según la carga.
- Elasticidad para crecer o reducir capacidad.
- Alta disponibilidad.
- Tolerancia a fallos.
- Reducción de costes.
- Desarrollo y despliegue más rápidos.

---

# Modelos de servicio

## IaaS (Infrastructure as a Service)

El proveedor ofrece infraestructura.

Ejemplos:

- Amazon EC2
- Azure Virtual Machines

El usuario administra:

- Sistema operativo
- Aplicaciones
- Configuración

---

## PaaS (Platform as a Service)

El proveedor administra la infraestructura y la plataforma.

El desarrollador solo se preocupa por desarrollar la aplicación.

Ejemplos:

- Elastic Beanstalk
- Azure App Service
- Heroku

---

## SaaS (Software as a Service)

El usuario consume directamente una aplicación completa.

No necesita instalar ni mantener nada.

Ejemplos:

- Gmail
- Google Workspace
- Dropbox
- Zoom

---

# Modelo de precios de AWS

AWS cobra según el uso de:

- Tiempo de computación.
- Almacenamiento utilizado.
- Transferencia de datos salientes (la entrada suele ser gratuita).

---

# Modelo de responsabilidad compartida

## AWS es responsable de

La **seguridad de la nube**, incluyendo:

- Centros de datos.
- Hardware.
- Red.
- Infraestructura física.

## El cliente es responsable de

La **seguridad dentro de la nube**, incluyendo:

- Usuarios.
- Permisos.
- Configuración.
- Datos.
- Aplicaciones.

---

# Infraestructura global de AWS

La infraestructura mundial de AWS se basa en:

- Regiones.
- Zonas de disponibilidad (AZ).
- Centros de datos.
- Edge Locations.
- Local Zones.

---

# Regiones

Una región es una ubicación geográfica donde AWS dispone de varios centros de datos.

## Ventajas

- Baja latencia.
- Alta disponibilidad.
- Cumplimiento normativo.

### Factores para elegir una región

- Cercanía a los usuarios.
- Legislación sobre datos.
- Servicios disponibles.
- Precio.

---

# Zonas de Disponibilidad (Availability Zones - AZ)

Cada región contiene varias AZ.

Cada AZ está formada por uno o varios centros de datos independientes.

Características:

- Alimentación redundante.
- Redes redundantes.
- Baja latencia entre AZ.
- Aislamiento frente a fallos.

Esto permite mantener aplicaciones disponibles incluso si una AZ falla.

---

# Edge Locations

Son puntos de presencia distribuidos mundialmente para acercar el contenido al usuario.

Su objetivo es:

- Reducir la latencia.
- Mejorar la velocidad de carga.

Son la base de servicios como **CloudFront**.

---

# Múltiples regiones

Distribuir una aplicación entre distintas regiones permite:

- Alta disponibilidad.
- Recuperación ante desastres.
- Menor latencia para usuarios internacionales.

---

# AWS Local Zones

Extienden determinados servicios AWS cerca de grandes ciudades.

Casos de uso:

- Aplicaciones que requieren muy baja latencia.
- Migraciones híbridas.
- Requisitos de residencia de datos.

---

# Servicios regionales y globales

## Servicios regionales

Funcionan dentro de una región concreta.

Ejemplos:

- EC2
- Elastic Beanstalk

---

## Servicios globales

Funcionan a nivel mundial.

Ejemplos:

- IAM
- Route 53
- CloudFront
- WAF

---

# Buenas prácticas al crear una cuenta AWS

- Activar MFA en la cuenta Root.
- No utilizar la cuenta Root para el trabajo diario.
- Crear usuarios IAM.
- Crear un usuario administrador mediante IAM.
- Configurar presupuestos y alertas de gasto.
- Reservar la cuenta Root únicamente para tareas críticas.