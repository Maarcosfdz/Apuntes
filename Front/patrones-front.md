# Patrones Front

## Uso de claves en Storage

### Qué es una clave
Identificador único para guardar datos en storage.

Ejemplo:
sessionStorage.setItem("clave", "valor");

### Buenas prácticas

- Usar nombres claros:
  "onboarding-form-draft"

- Versionar:
  "onboarding-form-draft_v1"

- Usar constantes:
  const FORM_DRAFT_KEY = "onboarding-form-draft_v1";

### Problemas comunes

- Colisiones de claves
- Datos sobrescritos
- Incompatibilidad al cambiar el modelo

### Idea clave
"La clave es el ID de tu dato en el navegador"

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
