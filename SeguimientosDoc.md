### API Documentation

**Base URL:**  
`https://miurafx.com/server/api/`

---

### 1. **Endpoint: `/seguimientos`**

- **Method:** `GET`, `POST`
- **Middleware:** `auth-token`, `role:master|monitor`
- **Description:** This endpoint is used to retrieve or store tracking records (follow-ups).

#### **GET /seguimientos (index)**  
This will retrieve a list of tracking records (follow-ups).

#### **POST /seguimientos (store)**  
This will create a new tracking record with the following body:

**Request Body (JSON):**
```json
{
  "id": "",
  "fecha_creacion": "",
  "ultimo_contacto": "",
  "observaciones": "",
  "usuario": {
    "id": "",
    "nombre": ""
  },
  "cliente": {
    "id": "",
    "nombre": ""
  }
}
```

---

### 2. **Endpoint: `/seguimiento/${id}`**

- **Method:** `GET`
- **Middleware:** `auth-token`, `role:master|monitor`
- **Description:** Retrieve specific tracking record details by `id`.

#### **GET /seguimiento/${id}**

**Response (JSON):**
```json
{
  "id": 1,
  "fecha_creacion": "2024-09-17T00:00:00.000000Z",
  "ultimo_contacto": "2024-09-16T15:30:00.000000Z",
  "observaciones": "Sin comentarios",
  "usuario": {
    "id": 101,
    "nombre": "Juan Pérez"
  },
  "cliente": {
    "id": 202,
    "nombre": "Carlos Gómez"
  }
}
```

---

### 3. **Endpoint: `/seguimientos`**

- **Method:** `POST`
- **Middleware:** `auth-token`, `role:master|monitor`
- **Description:** Update a follow-up record with new information.

#### **POST /seguimientos**

**Request Body (JSON):**
```json
{
  "observaciones": "",
  "cliente_id": "",
  "user_id": ""
}
```

This endpoint is used to update the latest contact date, add observations, and link the client and user information to the follow-up record.

#### **Response JSON**
```json
{
  "message": "Seguimiento creado correctamente",
  "result": [
    {
      "id": 1,
      "fecha_creacion": "2024-09-17T00:00:00.000000Z",
      "ultimo_contacto": "2024-09-16T15:30:00.000000Z",
      "observaciones": "Sin comentarios",
      "usuario": {
        "id": 101,
        "nombre": "Juan Pérez"
      },
      "cliente": {
        "id": 202,
        "nombre": "Carlos Gómez"
      }
    }
  ]
}

  
  
```
