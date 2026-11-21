# AgriPro – Gestión de una empresa agrícola

Aplicación web full stack para administrar el personal y las plantaciones de una empresa agrícola.
Proyecto del curso de Bases de Datos (UCSP, 2023).

**Stack:** Next.js 14 · React · TypeScript · Tailwind CSS · Node.js · Express · MySQL

## Qué hace

- CRUD completo de **operarios**, **ingenieros** y **plantaciones** (crear, listar, editar y eliminar).
- Consulta de la **variedad** de cultivo asociada a cada plantación.
- Frontend con páginas separadas por entidad que consume la API con Axios.

## Arquitectura

```
frontend/   Frontend (Next.js + TypeScript + Tailwind)  → http://localhost:3000
api/        API REST (Express + mysql)                  → http://localhost:3001
            Base de datos MySQL "agripro"
```

## API REST

| Método | Ruta | Descripción |
|---|---|---|
| GET | `/operarios` · `/ingenieros` · `/plantaciones` | Lista los registros |
| POST | `/createOperario` · `/createIngeniero` · `/createPlantacion` | Crea un registro |
| PUT | `/updateOperario` · `/updateIngeniero` · `/updatePlantacion` | Actualiza un registro |
| DELETE | `/deleteOperario/:id` · `/deleteIngeniero/:id` · `/deletePlantacion/:id` | Elimina un registro |
| GET | `/variedad/:id_variedad` | Devuelve una variedad de cultivo |

Las consultas usan parámetros (`?`) para evitar inyección SQL.

## Cómo ejecutarlo

Requisitos: Node.js 18+ y un servidor MySQL local con una base de datos `agripro`.

```bash
# API
cd api
npm install
node index.js          # escucha en el puerto 3001

# Frontend (en otra terminal)
cd frontend
npm install
npm run dev            # abre http://localhost:3000
```

La conexión a MySQL se configura al inicio de `api/index.js` (por defecto `root` sin contraseña en `localhost`).
