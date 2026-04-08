# 🧠 Sistema de Apuntes Front

Este archivo define cómo organizo mis apuntes de frontend.

Sirve para:

* Mantener consistencia
* Saber dónde guardar cada cosa
* Pedir ayuda a ChatGPT pegando contexto

---

## 📂 Estructura actual

/apuntes-front
├── conceptos-front.md
├── decisiones-front.md
├── arquitectura-front.md
├── patrones-front.md

---

## 🧩 Tipos de conocimiento

### 1. Conceptos (`conceptos-front.md`)

👉 Qué es algo

Ejemplos:

* React
* Vite vs Next.js
* localStorage vs sessionStorage
* wizard

💡 Regla:
Explicaciones simples, como si me lo explicara a mí mismo.

---

### 2. Decisiones (`decisiones-front.md`)

👉 Cuándo usar algo

Ejemplos:

* cuándo usar Vite o Next
* cuándo usar sessionStorage
* cuándo usar context vs props

💡 Regla:
Siempre en formato:

* uso X cuando...
* evito X cuando...

---

### 3. Arquitectura (`arquitectura-front.md`)

👉 Cómo organizo proyectos

Ejemplos:

* arquitectura por capas
* estructura de carpetas
* separación de responsabilidades

💡 Regla:
Habla de estructura global, no de detalles pequeños.

---

### 4. Patrones (`patrones-front.md`)

👉 Cómo se hacen bien las cosas en la práctica

Ejemplos:

* uso de claves en storage
* manejo de formularios multi-step
* naming conventions
* manejo de estado

💡 Regla:
Incluye:

* buenas prácticas
* problemas reales
* soluciones

---

## 🧠 Cómo decidir dónde va algo

Cuando tenga nueva información, me pregunto:

1. ¿Estoy definiendo qué es algo?
   → conceptos

2. ¿Estoy decidiendo cuándo usar algo?
   → decisiones

3. ¿Estoy organizando código/proyecto?
   → arquitectura

4. ¿Estoy explicando cómo hacerlo bien en código real?
   → patrones

---

## 🤖 Cómo usar este archivo con ChatGPT

Cuando quiera añadir algo, hago:

1. Pego este archivo (o parte relevante)
2. Pego el contenido nuevo
3. Pregunto:

"¿Dónde meto esto?"

Opcional:
"Si no encaja, crea un nuevo archivo"

---

## 📌 Reglas importantes

* No mezclar tipos de contenido
* Preferir claridad sobre cantidad
* Usar ejemplos reales
* Mantener nombres consistentes

---

## 🚀 Futuro (cuando suba nivel)

Posibles nuevos archivos:

* anti-patrones-front.md → cosas a evitar
* snippets-front.md → código reutilizable
* testing-front.md → testing (jest, vitest, etc.)

---

## 🔥 Idea clave

"Mis apuntes no son para guardar información, son para pensar mejor"
