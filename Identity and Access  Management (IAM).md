# AWS IAM (Identity and Access Management)

## ¿Qué es AWS IAM?

AWS IAM (Identity and Access Management) es el servicio global de AWS encargado de controlar quién puede acceder a los recursos y qué acciones puede realizar.

Su función principal es gestionar de forma centralizada:
- Usuarios
- Grupos
- Roles
- Políticas de permisos

> IAM es como entregar "llaves digitales" para acceder únicamente a los recursos autorizados.

---

# Usuarios y grupos

## Usuario IAM

Representa a una persona o servicio que necesita acceder a AWS.

Características:

- Tiene credenciales propias.
- Puede tener permisos individuales.
- Puede pertenecer a varios grupos.
- No es obligatorio pertenecer a un grupo.

## Grupo IAM

Es un conjunto de usuarios con necesidades de acceso similares.

Características:

- Solo contiene usuarios (no otros grupos).
- Facilita administrar permisos de forma centralizada.
- Los permisos asignados al grupo son heredados por todos sus miembros.

---

# Buenas prácticas con usuarios

- Eliminar usuarios que ya no necesiten acceso.
- Utilizar etiquetas (Tags) para organizar usuarios.
- Aplicar siempre el principio de mínimo privilegio.
- Asignar permisos a grupos antes que directamente a usuarios.

---

# Políticas IAM

Las políticas son documentos JSON que definen qué puede hacer un usuario, grupo o rol.

Las políticas especifican:

- Acciones permitidas
- Recursos afectados
- Condiciones
- Si la acción está permitida o denegada

Si una acción **no está permitida explícitamente**, AWS la deniega automáticamente.

---

# Tipos de políticas

## Políticas heredadas

Los usuarios reciben automáticamente los permisos del grupo al que pertenecen.

Ventajas:

- Administración sencilla.
- Cambiar una política afecta a todos los miembros.

---

## Políticas en línea (Inline Policies)

Se asignan directamente a un usuario o recurso.

Se utilizan cuando un usuario necesita permisos específicos que nadie más tendrá.

---

# Estructura de una política IAM

Una política está formada por:

## Version

Versión del lenguaje de la política.

Siempre suele ser:

```json
"Version": "2012-10-17"
```

---

## Statement

Lista de reglas de la política.

Cada Statement contiene:

### Sid

Identificador opcional.

### Effect

Indica si la acción está:

- Allow
- Deny

### Principal

Quién recibe la política.

Puede ser:

- Usuario
- Rol
- Cuenta AWS

### Action

Lista de acciones permitidas o denegadas.

Ejemplo:

- s3:GetObject
- ec2:StartInstances

### Resource

Sobre qué recursos se aplican esas acciones.

### Condition

Condiciones adicionales (opcional).

---

# Principio de mínimo privilegio

Regla fundamental de AWS:

> Conceder únicamente los permisos estrictamente necesarios.

Nunca dar permisos por comodidad.

---

# Política de contraseñas

IAM permite definir reglas para las contraseñas:

- Longitud mínima.
- Mayúsculas.
- Minúsculas.
- Números.
- Caracteres especiales.
- Caducidad.
- Evitar reutilización.
- Permitir cambio de contraseña.

---

# MFA (Multi-Factor Authentication)

Añade una segunda forma de autenticación además de la contraseña.

Ejemplos:

- Código en el móvil.
- Huella.
- Llave física.

Beneficio principal:

Aunque roben la contraseña, no podrán acceder sin el segundo factor.

Debe activarse especialmente en:

- Cuenta Root
- Usuarios IAM

---

# Factores de autenticación

## Algo que sabes

- Contraseña

## Algo que tienes

- Teléfono
- Llave física

## Algo que eres

- Huella
- Reconocimiento facial

---

# Dispositivos MFA

## Virtual

Aplicaciones móviles como:

- Google Authenticator
- Authy

---

## Llave de seguridad (U2F)

Dispositivos físicos como:

- YubiKey

---

## Token hardware

Dispositivo dedicado que genera códigos temporales.

---

# Formas de acceder a AWS

## Consola Web

Acceso mediante:

- Usuario IAM
- Usuario Root

Protegido con:

- Contraseña
- MFA

---

## AWS CLI

Herramienta de línea de comandos.

Permite:

- Automatizar tareas.
- Ejecutar scripts.
- Administrar AWS desde la terminal.

Usa claves de acceso.

---

## AWS SDK

Permite administrar AWS desde código.

Disponible para numerosos lenguajes:

- Python
- JavaScript
- Java
- Go
- C#
- PHP
- Ruby
- Kotlin
- Rust
- Swift

Ejemplo:

La AWS CLI está desarrollada utilizando el SDK de Python (boto3).

---

# Claves de acceso

Compuestas por:

- Access Key ID
- Secret Access Key

Se utilizan para:

- AWS CLI
- AWS SDK

Buenas prácticas:

- Nunca compartirlas.
- No almacenarlas en el código.
- Rotarlas periódicamente.

Piensa en ellas como:

- Access Key ID → Usuario
- Secret Access Key → Contraseña

---

# Roles IAM

Un rol es una identidad temporal que concede permisos sin utilizar credenciales permanentes.

Características:

- No pertenece a una persona concreta.
- Se asume temporalmente.
- Puede ser utilizado por usuarios o servicios.
- Permite acceso entre cuentas AWS.

---

# Usuarios vs Roles

## Usuario

- Permanente.
- Tiene contraseña.
- Tiene Access Keys.

---

## Rol

- Temporal.
- No tiene contraseña.
- Genera credenciales temporales.
- Mayor seguridad.

---

# Funcionamiento de un rol

Intervienen dos políticas:

## Política de confianza

Define quién puede asumir el rol.

---

## Política de permisos

Define qué puede hacer ese rol.

Cuando alguien asume un rol:

1. AWS verifica la política de confianza.
2. Si está autorizado:
   - genera credenciales temporales mediante STS (AssumeRole).

---

# Roles para servicios AWS

Los roles también pueden asignarse a servicios.

Ejemplo:

Una instancia EC2 puede obtener permisos para acceder a S3 sin almacenar claves.

Siempre se recomienda aplicar el principio de mínimo privilegio.

---

# Herramientas de auditoría

## IAM Credential Report

Informe a nivel de cuenta.

Incluye:

- Usuarios.
- Último acceso.
- MFA habilitado.
- Políticas asignadas.
- Estado de las credenciales.

---

## IAM Access Advisor

Informe a nivel de usuario.

Permite ver:

- Qué servicios puede usar.
- Cuándo los utilizó por última vez.

Sirve para eliminar permisos innecesarios.

---

# Buenas prácticas de IAM

- No utilizar la cuenta Root salvo para tareas excepcionales.
- Una persona = un usuario IAM.
- Agrupar usuarios.
- Asignar permisos a grupos.
- Aplicar el principio de mínimo privilegio.
- Configurar políticas de contraseña fuertes.
- Activar MFA.
- Utilizar Roles para servicios AWS.
- Usar Access Keys únicamente para CLI y SDK.
- Revisar periódicamente permisos.
- Eliminar usuarios, roles y claves que ya no se utilicen.
- No compartir usuarios ni Access Keys.

---

# Modelo de responsabilidad compartida

## AWS

Se encarga de:

- Seguridad física.
- Infraestructura.
- Red global.
- Cumplimiento y análisis de vulnerabilidades.

---

## Cliente

Debe gestionar:

- Usuarios.
- Grupos.
- Roles.
- Políticas.
- MFA.
- Rotación de claves.
- Auditoría de permisos.
- Revisión de accesos.

---

# Resumen rápido

## Usuarios

Personas que acceden a AWS.

## Grupos

Conjuntos de usuarios con permisos comunes.

## Políticas

Documentos JSON que definen permisos.

## Roles

Permisos temporales para usuarios o servicios.

## MFA

Segunda capa de seguridad.

## AWS CLI

Administración mediante terminal.

## AWS SDK

Administración mediante programación.

## Access Keys

Credenciales para CLI y SDK.

## Auditoría

- IAM Credential Report
- IAM Access Advisor