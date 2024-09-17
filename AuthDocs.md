### API Reference

#### Endpoint: `/auth/register`
- **Method**: POST
- **Description**: Registers a new user in the system. This endpoint creates a new user in the database and assigns the 'customer' role to it..

##### Request Body (JSON)
The request body must be sent in JSON format with the following fields:

```json
{
    "name": "string", // Required. The username. Maximum 255 characters.
    "email": "string", // Required. Must be a valid and unique email address.
    "password": "string", // Required. Must be at least 8 characters.
    "nombre_completo": "string", // Required. Full name of the user.
    "dirección": "string", // Mandatory. User address. Maximum 255 characters.
    "celular": "string", // Mandatory. Cell phone number. Maximum 15 characters.
    "fecha_nacimiento": "date", // Required. Date of birth in YYYY-MM-DD format.
    "estado": "integer", // Required. User status, represented as an integer.
    "etiqueta": "string|null", // Optional. Label associated with the user. Maximum 50 characters.
    "ciudad": "string", // Mandatory. City of residence. Maximum 100 characters.
    "tipo_documento": "string", // Mandatory. Document type (en. CC, TI). Maximum 10 characters.
    "documento": "string", // Mandatory. Unique identity document. Maximum 20 characters.
    "método_pago": "string|null", // Optional. Preferred payment method. Maximum 50 characters.
    "pais": "string" // Mandatory. Country of residence. Maximum 100 characters.
}
```

##### Response (JSON)
If the registration is successful, the following JSON response will be returned:

```json
{
    "message": "User created successfully",
    "user": {
        "id": "integer", // User's unique ID.
        "name": "string", // Username.
        "email": "string", // email addres.
        "nombre_completo": "string", //User's full name. 
        "dirección": "string", // User's address.
        "celular": "string", // Cell phone number.
        "fecha_nacimiento": "date", // Date of birth.
        "estado": "integer", // User's status.
        "etiqueta": "string|null", // User's label.
        "ciudad": "string", // City of residence.
        "tipo_documento": "string", // Document type.
        "documento": "string", // Identity document.
        "método_pago": "string|null", // Preferred payment method.
        "pais": "string", // Country of residence.
        "created_at": "datetime", // User creation date.
        "updated_at": "datetime"  // Last updated date.
    }
}
```

##### Códigos de Respuesta
- **201 Created**: The user has been created successfully.
- **422 Unprocessable Entity**: Validation errors. The response body will contain details of the errors.

---

#### Endpoint: `/auth/login`
- **Method**: POST
- **Description**: Authenticates a user and returns an access token. This endpoint verifies the user's credentials and, if correct, generates an authentication token.

##### Request Body (JSON)
The request body must be sent in JSON format with the following fields:

```json
{
    "email": "string", // Required. The email user.
    "password": "string" // Required. The user's password.
}
```

##### Response (JSON)
If the login is successful, the following JSON response will be returned:

```json
{
    "token": "string", // Authentication token generated.
    "Type": "Bearer", // Token type (Bearer).
    "role": "string" // Role of the authenticated user (for example, 'customer', 'admin').
}
```

##### Códigos de Respuesta
- **200 OK**: Login successful. An authentication token is returned.
- **401 Unauthorized**: The credentials provided are incorrect.

### Notas Adicionales
- **Autenticación**: The token returned by the `/auth/login` endpoint must be used in the headers of requests to endpoints that require authentication, in the form:`Authorization: Bearer {token}`.
- **Validación de campos**: All validation error messages are customized in Spanish.
