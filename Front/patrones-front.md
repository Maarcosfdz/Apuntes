# Patrones Front

## 📚 Índice

* [Uso de claves en Storage](#uso-de-claves-en-storage)
* [Funciones async: void vs Promise](#funciones-async-void-vs-promisevoid)
* [Forms](#forms)

---

## Uso de claves en Storage

### Qué es una clave

Identificador único para guardar datos en storage.

Ejemplo:

```ts
sessionStorage.setItem("clave", "valor");
```

### Buenas prácticas

* Usar nombres claros:
  "onboarding-form-draft"

* Versionar:
  "onboarding-form-draft_v1"

* Usar constantes:

```ts
const FORM_DRAFT_KEY = "onboarding-form-draft_v1";
```

### Problemas comunes

* Colisiones de claves
* Datos sobrescritos
* Incompatibilidad al cambiar el modelo

### Idea clave

"La clave es el ID de tu dato en el navegador"

---

## Funciones async: void vs Promise<void>

### Diferencia clave

* `void`
  La función no devuelve nada útil.
  Puede ejecutar lógica async internamente, pero **no se puede hacer await desde fuera**.

* `Promise<void>`
  La función devuelve una promesa sin valor.
  Permite:

  * hacer `await`
  * controlar loading
  * manejar errores

---

### Ejemplo

```ts
function onClick(): void {
  fetchData(); // async interno, pero no awaitable
}

async function onSubmit(): Promise<void> {
  await fetchData(); // awaitable desde fuera
}
```

---

### Caso mixto

```ts
type Handler = () => void | Promise<void>;
```

👉 La función puede ser síncrona o asíncrona.

---

### Problema

El llamador no sabe si puede hacer `await`.

---

### Solución (normalizar)

```ts
await Promise.resolve(handler());
```

👉 Esto permite:

* soportar funciones sync
* soportar funciones async
* evitar errores

---

### Cuándo usar cada uno

* `void` → handlers simples (clicks, eventos sin control externo)
* `Promise<void>` → cuando necesitas:

  * loading
  * control de flujo
  * manejo de errores

---

### Idea clave

"Si alguien necesita esperar a que termine, devuelve una Promise"

---

## Forms

### Patrón básico

👉 Siempre:

1. estado (`useState`)
2. inputs controlados (`value + onChange`)
3. validación en `onSubmit`
4. mostrar errores en UI
5. desactivar validación del navegador

---

### Ejemplo base

```tsx
const [email, setEmail] = useState("");
const [error, setError] = useState("");

function handleSubmit(e) {
  e.preventDefault();

  if (!email) {
    setError("El correo es obligatorio");
    return;
  }

  setError("");
}
```

---

### Validación email

```ts
const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

if (!emailRegex.test(email)) {
  setError("Correo inválido");
}
```

---

### Desactivar validación del navegador

```tsx
<form onSubmit={handleSubmit} noValidate>
```

👉 Evita mensajes tipo:
"Please fill out this field"

---

### Mostrar error

```tsx
{error && <p className="text-red-500 text-sm">{error}</p>}
```

---

### Idea clave

"El formulario lo controlo yo, no el navegador"
