# Sesión 8 – Pruebas del paso 9 (capturas para el PDF)

Con el backend corriendo (`mvn spring-boot:run`) y el frontend con `ng serve`, abre F12 → pestaña **Red**.

| N.º | Acción | Resultado esperado |
|---|---|---|
| 1 | Entrar a «Productos» desde el sidebar | GET `pagina=0&tamanio=10&ordenarPor=nombre&direccion=asc`; la tabla muestra la categoría |
| 2 | Clic dos veces en «Precio» | `ordenarPor=precio` con `direccion=asc` y luego `desc` |
| 3 | Cambiar a 5 por página y «Siguiente» | `tamanio=5&pagina=1`; «Página 2 de …» |
| 4 | Filtrar por una categoría | Solo sus productos de la página actual, sin nuevas peticiones |
| 5 | «Nuevo producto» | El select lista solo categorías activas (Vitaminas no aparece) |
| 6 | «Registrar» sin completar | Mensajes de validación; no se envía la petición |
| 7 | Registrar un producto válido | POST 201; aparece en el listado con su categoría |
| 8 | Registrar otro con el mismo nombre en minúsculas | Alerta con el mensaje del backend (POST 409) |
| 9 | Editar un producto de «Vitaminas» (inactiva) | Select muestra «(inactiva)», aviso, y «Actualizar» no envía hasta elegir una activa |
| 10 | Cambiar la categoría de un producto y guardar | PUT 200; listado con la nueva categoría |
| 11 | Dar de baja un producto | DELETE 204; fila «Inactivo» y botón deshabilitado |
| 12 | En «Categorías», eliminar una con productos | Alerta con el mensaje del backend (DELETE 409) |

Commits sugeridos (rama `feature/productos-landa`):
1. `feat(productos): listar productos paginados con su categoría`
2. `feat(productos): ordenar, cambiar tamaño de página y filtrar por categoría`
3. `feat(productos): registrar y editar con lista de categorías`
4. `feat(productos): validar categoría inactiva y dar de baja`
