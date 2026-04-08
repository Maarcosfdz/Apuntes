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
