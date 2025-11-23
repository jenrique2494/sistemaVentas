# Usuarios por Defecto del Sistema VTR

Este documento contiene la lista de usuarios por defecto creados en la base de datos del sistema VTR con sus respectivos roles y credenciales.

## Credenciales de Acceso

**Contraseña para todos los usuarios**: `password`

## Usuarios y Roles

| Usuario | Email | Rol | Descripción | Flags |
|---------|-------|-----|-------------|-------|
| `visitante` | visitante@gmail.com | EjecVenta | Usuario visitante de prueba | flagSaleEquip: ✓, flagRetryEquip: ✓ |
| `ejecutivo_venta` | ejecutivo@gmail.com | EjecVenta | Ejecutivo de ventas | flagSaleEquip: ✓, flagRetryEquip: ✓ |
| `supervisor` | supervisor@gmail.com | Supervisor | Supervisor de ventas | flagSaleEquip: ✓, flagRetryEquip: ✓ |
| `backoffice` | backoffice@gmail.com | BackOffice | Personal de back office | flagSaleEquip: ✓, flagRetryEquip: ✓ |
| `logistica` | logistica@gmail.com | Logistic | Personal de logística | flagSaleEquip: ✗, flagRetryEquip: ✓ |
| `admin_usuarios` | admin@gmail.com | User_administrator | Administrador de usuarios | flagSaleEquip: ✓, flagRetryEquip: ✓ |

## Roles del Sistema

- **EjecVenta**: Ejecutivo de Ventas - Puede realizar operaciones de venta
- **Supervisor**: Supervisor - Supervisa operaciones de venta
- **BackOffice**: Back Office - Procesa operaciones administrativas
- **Logistic**: Logística - Gestiona reintentos y seguimiento logístico
- **User_administrator**: Administrador de Usuarios - Gestiona mantenimiento de usuarios

## Prueba de Login

Para probar el acceso al sistema, puede usar cualquiera de los usuarios anteriores con la contraseña `password`.

### Ejemplo con curl:
```bash
curl -X POST http://localhost:3000/api/authenticate/v1/login \
  -H "Content-Type: application/json" \
  -d '{"username":"visitante","password":"password"}'
```

### Ejemplo con PowerShell:
```powershell
$body = @{ username = "visitante"; password = "password" } | ConvertTo-Json
Invoke-WebRequest -Uri "http://localhost:3000/api/authenticate/v1/login" \
  -Method POST \
  -ContentType "application/json" \
  -Body $body
```

## Notas Importantes

- Todos los usuarios tienen la contraseña: **password**
- Los datos son de prueba y pueden ser modificados/eliminados según sea necesario
- Para cambiar contraseñas en producción, configure variables de entorno adicionales
- El seed solo crea usuarios si estos no existen ya en la base de datos
