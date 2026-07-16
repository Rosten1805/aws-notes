

> **Objetivo:** Organizar correctamente los entornos de AWS siguiendo las buenas prácticas recomendadas por AWS.

---

# ¿Por qué crear varias cuentas?

Una de las mejores prácticas en AWS es **no utilizar una única cuenta para todos los recursos**.

En lugar de ello, se crean **varias cuentas independientes**, cada una destinada a un propósito específico.

Ejemplo:

```text
AWS Organization
│
├── Management (Gestión)
├── Production
├── Development
├── Testing
└── Sandbox
```

En la diapositiva solo aparecen dos:

- Cuenta General (Gestión)
- Cuenta Production (Producción)

---

# Cuenta General (Management)

Es la cuenta principal desde la que se administra la infraestructura.

Su función es centralizar la gestión de la organización y administrar el resto de cuentas.

Dentro de ella encontramos:

- Usuario Root
- MFA
- AWS Budgets
- Usuario IAM Administrador

Esquema:

```text
Tú
│
▼
Cuenta General
│
├── Root
└── IAM Admin
```

---

# Usuario Root

El usuario **Root** es el propietario de la cuenta AWS.

Tiene permisos ilimitados sobre todos los servicios.

## Buenas prácticas

- No utilizarlo para trabajar diariamente.
- Activar siempre MFA.
- Guardar sus credenciales en un lugar seguro.
- Utilizarlo únicamente para tareas críticas.

### Ejemplos de cuándo usar Root

- Cambiar el método de pago.
- Cerrar la cuenta.
- Recuperar el acceso.
- Cambios muy sensibles de seguridad.

---

# MFA (Multi-Factor Authentication)

El MFA añade una segunda capa de seguridad.

Además de la contraseña será necesario introducir un código generado por otro dispositivo.

Puede utilizarse mediante:

- Google Authenticator
- Microsoft Authenticator
- Authy
- YubiKey (llave física)

## ¿Por qué es importante?

Si alguien roba la contraseña del usuario Root, **no podrá acceder sin el segundo factor de autenticación**.

---

# AWS Budgets

AWS permite configurar presupuestos para controlar el gasto.

Ejemplo:

```text
Presupuesto mensual

50 €

↓

Avisos al alcanzar:

80%
90%
100%
```

Cuando se alcanza un porcentaje determinado del presupuesto, AWS envía una notificación por correo electrónico.

Esto ayuda a evitar facturas inesperadas.

---

# Usuario IAM Administrador

Después de crear la cuenta se crea un usuario IAM con permisos administrativos.

Ejemplo:

```text
IAMAdmin
```

Este será el usuario utilizado para trabajar diariamente.

## Nunca trabajar con Root.

---

# Cuenta Production

La producción se mantiene en una cuenta completamente independiente.

Dentro de ella también existen:

- Usuario Root
- MFA
- AWS Budgets
- Usuario IAM Administrador

Es otra cuenta aislada del resto.

---

# ¿Por qué separar Producción?

Separar las cuentas aporta numerosas ventajas.

## Seguridad

Si una cuenta es comprometida, el resto permanece aislado.

Ejemplo:

```text
Cuenta Desarrollo
    ↓
Comprometida

Cuenta Producción
    ↓
Sigue protegida
```

---

## Evitar errores

Los desarrolladores pueden experimentar libremente sin afectar a los servicios que utilizan los clientes.

```text
Desarrollo

✔ Crear recursos
✔ Eliminar recursos
✔ Probar configuraciones

↓

No afecta a Producción
```

---

## Facturación independiente

Cada cuenta posee sus propios costes.

Ejemplo:

```text
Producción

150 €/mes

------------------

Desarrollo

30 €/mes
```

Esto facilita el control económico.

---

## Permisos independientes

Cada cuenta puede tener usuarios distintos.

Ejemplo:

```text
Producción

Equipo DevOps

-------------------

Desarrollo

Equipo de Desarrollo
```

Así se aplica el principio de **mínimo privilegio**.

---

# ¿Qué significan los números 1 y 2 del esquema?

Representan el orden recomendado de configuración.

## Paso 1

Crear la cuenta General.

Configurar:

- Root
- MFA
- AWS Budgets
- IAM Admin

---

## Paso 2

Crear la cuenta de Producción.

Configurar nuevamente:

- Root
- MFA
- AWS Budgets
- IAM Admin

Cada cuenta debe protegerse de forma independiente.

---

# AWS Organizations

En empresas no se administran múltiples cuentas iniciando sesión con distintos correos electrónicos.

Para ello existe **AWS Organizations**.

Permite:

- Administrar múltiples cuentas.
- Centralizar la facturación.
- Aplicar políticas de seguridad.
- Compartir servicios entre cuentas.
- Organizar cuentas mediante Organizational Units (OU).

Ejemplo:

```text
AWS Organization
│
├── Management
│
├── Security
│
├── Logging
│
├── Shared Services
│
├── Networking
│
├── Production
│
├── Staging
│
├── Development
│
├── QA
│
└── Sandbox
```

---

# Buenas prácticas

- Nunca utilizar el usuario Root para trabajar.
- Activar siempre MFA.
- Crear un usuario IAM administrador.
- Configurar AWS Budgets.
- Separar Producción y Desarrollo en cuentas distintas.
- Gestionar todas las cuentas mediante AWS Organizations.
- Aplicar siempre el principio de mínimo privilegio.

---

# Resumen

- Una cuenta AWS representa un entorno aislado.
- El usuario Root solo debe utilizarse en casos excepcionales.
- El trabajo diario debe realizarse con usuarios IAM.
- MFA protege el acceso a la cuenta.
- AWS Budgets ayuda a controlar los costes.
- Producción y Desarrollo deben estar separados.
- AWS Organizations permite administrar todas las cuentas desde un único lugar.

---

# Conceptos clave para el examen

| Concepto | Descripción |
|----------|-------------|
| Root | Usuario propietario de la cuenta con permisos ilimitados. |
| IAM | Servicio para crear usuarios, grupos y permisos. |
| IAM Admin | Usuario administrador utilizado para el trabajo diario. |
| MFA | Segundo factor de autenticación para aumentar la seguridad. |
| AWS Budgets | Servicio para controlar y recibir alertas sobre el gasto. |
| Production | Cuenta que contiene los recursos utilizados por los clientes. |
| Management | Cuenta principal desde la que se administran las demás. |
| AWS Organizations | Servicio para gestionar múltiples cuentas AWS desde un único lugar. |