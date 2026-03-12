# ADR-0009: User Authentication and Multi-User Data Isolation

## Status
Accepted

## Context
Inicialmente la aplicación fue concebida como una herramienta personal orientada a un único usuario. Bajo ese supuesto, el sistema de autenticación tenía como único objetivo proteger el acceso a los datos locales de la aplicación mediante un login persistente similar al de aplicaciones personales o bancarias.

Sin embargo, durante el desarrollo del proyecto surgió la posibilidad de que otras personas puedan probar la aplicación y brindar feedback. Esto introduce la necesidad de permitir que múltiples usuarios tengan cuentas independientes y utilicen la aplicación sin acceder a los datos de otros usuarios.

El sistema debe permitir:

- múltiples usuarios registrados
- aislamiento completo de los datos entre usuarios
- sesiones persistentes para minimizar fricción de acceso
- una implementación simple acorde al MVP

Al mismo tiempo, se busca evitar la complejidad innecesaria de sistemas de autenticación avanzados (OAuth, proveedores externos, gestión de organizaciones o roles), ya que el objetivo inicial es validar el producto y su modelo de uso.

## Decision
Se implementará un sistema de autenticación basado en **cuentas de usuario con email y password**, utilizando **sesiones persistentes** para mantener la sesión iniciada entre usos de la aplicación.

Cada usuario tendrá su propia cuenta y todos los datos del sistema estarán asociados a ese usuario mediante una relación explícita en la base de datos.

Esto implica que las entidades principales del sistema incluirán una referencia al usuario propietario.

Estructura conceptual:

User  
 └ Project  
      └ Objective  
           └ Task  

Cada registro de estas entidades estará asociado a un `user_id`, garantizando el aislamiento de los datos entre usuarios.

El flujo de autenticación será el siguiente:

1. **Registro**
   - El usuario crea una cuenta utilizando email y password.

2. **Login**
   - El usuario inicia sesión con sus credenciales.
   - El servidor genera un token de sesión.

3. **Sesión persistente**
   - El token de sesión se almacena en una cookie segura.
   - Mientras la sesión sea válida, el usuario accede directamente a la aplicación sin necesidad de volver a iniciar sesión.

Este modelo mantiene una experiencia de uso simple y de baja fricción, similar a aplicaciones personales donde el login ocurre una sola vez y luego la sesión permanece activa.

## Consequences

### Positive
- Permite que múltiples usuarios utilicen la aplicación.
- Garantiza el aislamiento de datos entre usuarios.
- Facilita obtener feedback real de otras personas utilizando la app.
- Mantiene un sistema de autenticación simple adecuado para un MVP.
- Prepara la arquitectura para futuras extensiones del sistema de autenticación.
- Evita migraciones complejas de base de datos en el futuro al incluir `user_id` desde el inicio.

### Negative
- Introduce una complejidad mayor en comparación con un sistema estrictamente single-user.
- Requiere validar el acceso a recursos en cada request utilizando el contexto del usuario autenticado.
- Obliga a diseñar correctamente el manejo de sesiones y seguridad básica desde el inicio.

## Alternatives Considered

- **Single User Authentication Model** – No fue elegido porque limita el uso de la aplicación a una sola persona y dificulta obtener feedback de otros usuarios.

- **OAuth / Social Login (Google, GitHub, etc.)** – No fue elegido para el MVP porque introduce complejidad innecesaria y dependencias externas antes de validar el producto.