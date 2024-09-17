Of course! Here's the translation:

---

## API Routes Documentation

**Base URL:** `https://miurafx.com/server/api/`

### 1. **Movement Routes:**

#### **GET /movimientos**

**Description:**  
Fetches a list of financial movements. Authentication via token and specific roles is required.

- **Middleware:** `auth-token`, `role: master | monitor`
- **Method:** `GET`
- **Authentication:** Yes (token required)
- **Allowed Roles:** `master`, `monitor`

**Successful Response (200):**  
```json
[
  {
    "id": 1,
    "radicado": "12345ABCD",
    "tipo_solicitud": "retiro",
    "estado_solicitud": "pendiente",
    "metodo_pago": "transferencia bancaria",
    "fecha_solicitud": "2024-09-17T00:00:00.000000Z",
    "divisa": "USD",
    "cantidad": "5000",
    "razon_rechazo": "no aplica",
    "documento": "documento123.pdf",
    "cliente_id": 1
  },
  ...
]
```

#### **POST /movimientos**

**Description:**  
Creates a new financial movement. Authentication via token and specific roles is required.

- **Middleware:** `auth-token`, `role: master | monitor`
- **Method:** `POST`
- **Authentication:** Yes (token required)
- **Allowed Roles:** `master`, `monitor`
- **Body:** 
  ```json
  {
    "radicado": "",
    "tipo_solicitud": "",
    "estado_solicitud": "",
    "metodo_pago": "",
    "fecha_solicitud": "",
    "divisa": "",
    "cantidad": "",
    "razon_rechazo": "",
    "documento": "",
    "cliente_id": ""
  }
  ```

**Successful Response (201):**  
```json
{
  "message": "Movimiento creado con éxito",
  "movimiento_id": 12
}
```

---

### 2. **Single Movement Routes:**

#### **GET /movimientos/{id}**

**Description:**  
Fetches information for a specific movement.

- **Middleware:** `auth-token`, `role: master | monitor`
- **Method:** `GET`
- **Authentication:** Yes (token required)
- **Allowed Roles:** `master`, `monitor`

**Successful Response (200):**  
```json
{
  "id": 11,
  "radicado": "12345ABCD",
  "tipo_solicitud": "retiro",
  "estado_solicitud": "pendiente",
  "metodo_pago": "transferencia bancaria",
  "fecha_solicitud": "2024-09-17T00:00:00.000000Z",
  "divisa": "USD",
  "cantidad": "5000",
  "razon_rechazo": "no aplica",
  "documento": "documento123.pdf",
  "cliente_id": 1
}
```

---

### 3. **Request Status Update Routes:**

#### **PUT /movimientos/estado/{id}**

**Description:**  
Updates the status of a specific request in the movement records table.

- **Middleware:** `auth-token`, `role: master | monitor`
- **Method:** `PUT`
- **Authentication:** Yes (token required)
- **Allowed Roles:** `master`, `monitor`
- **Body:** 
  ```json
  {
    "estado_solicitud": "aprobado"
  }
  ```

**Possible values for `estado_solicitud`:**  
- `aprobado`
- `rechazado`
- `pendiente`

**Successful Response (200):**  
```json
{
  "message": "Estado de la solicitud actualizado con éxito"
}
```

---

### Notes:
- **Authentication:** All endpoints require a valid token for authentication.
- **Roles:** The allowed roles for accessing the routes are `master` and `monitor`. 

---
