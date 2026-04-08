# Manual Practico de Tailwind CSS + CSS de apoyo

Guia diaria para construir UI rapido, con ejemplos listos para copiar.
Enfoque: solucion directa, poco texto y mucho codigo.

## Indice

- [Tipografia](#tipografia)
- [Colores](#colores)
- [Spacing](#spacing)
- [Layout (Flex y Grid)](#layout)
- [Posicionamiento](#posicionamiento)
- [Componentes comunes](#componentes)
- [Inputs y formularios](#inputs)
- [Botones](#botones)
- [Imagenes y backgrounds](#imagenes)
- [Estados (hover, focus...)](#estados)
- [Animaciones y transiciones](#animaciones)
- [Trucos utiles](#trucos)
- [Errores comunes](#errores)

---

## Tipografia

### Cheat sheet rapido

- `font-medium`: peso medio
- `font-semibold`: peso seminegrita
- `font-bold`: negrita
- `text-xs` `text-sm` `text-base` `text-lg` `text-xl` `text-2xl` `text-4xl`: tamanos
- `tracking-wide`: separacion de letras
- `leading-tight` `leading-relaxed`: altura de linea
- `uppercase` `lowercase` `capitalize`: transformacion
- `line-clamp-2`: limitar texto a 2 lineas (si plugin/utilidad disponible)

### Ejemplos listos

```tsx
<h1 className="text-3xl font-bold tracking-tight text-slate-900">
  Dashboard
</h1>
<p className="mt-2 text-sm text-slate-500">
  Resumen de actividad diaria
</p>
```

- Esto hace: titulo fuerte + subtitulo discreto.
- Usalo cuando: encabezado de pagina.

```tsx
<p className="text-base leading-relaxed text-slate-700">
  Este bloque tiene una lectura comoda en parrafos largos.
</p>
```

- Esto hace: mejora legibilidad.
- Usalo cuando: texto de detalle.

```tsx
<span className="text-xs font-semibold uppercase tracking-wide text-indigo-600">
  Nuevo
</span>
```

- Esto hace: etiqueta compacta.
- Usalo cuando: badges o labels.

### Patron util de jerarquia

```tsx
<header className="space-y-1">
  <p className="text-xs uppercase tracking-wider text-slate-500">Seccion</p>
  <h2 className="text-2xl font-bold text-slate-900">Usuarios</h2>
  <p className="text-sm text-slate-600">Gestion y permisos</p>
</header>
```

---

## Colores

### Cheat sheet rapido

- Texto: `text-slate-900`, `text-gray-600`, `text-white`
- Fondo: `bg-white`, `bg-slate-50`, `bg-indigo-600`
- Borde: `border-slate-200`
- Opacidad de color: `bg-black/40`, `text-white/80`
- Color custom: `text-[#193133]`, `bg-[#8f93ff]`, `border-[#8f93ff]`

### Ejemplos directos

```tsx
<div className="bg-white text-slate-900 border border-slate-200 rounded-lg p-4">
  Contenido principal
</div>
```

```tsx
<button className="bg-indigo-600 hover:bg-indigo-700 text-white font-semibold px-4 py-2 rounded-md">
  Guardar cambios
</button>
```

```tsx
<p className="text-[#193133]">Color de marca sin tocar config</p>
```

- Esto hace: aplica color exacto por hex.
- Usalo cuando: prototipo rapido o branding puntual.

### Hover y contraste

```tsx
<a className="text-slate-700 hover:text-indigo-600 transition-colors" href="#">
  Ir al detalle
</a>
```

```tsx
<div className="bg-slate-900 text-slate-100 p-6 rounded-xl">
  Tema oscuro local
</div>
```

### Buen patron con variables CSS (cuando toque)

```css
:root {
  --brand: #8f93ff;
  --brand-dark: #6f74ff;
}
```

```tsx
<button className="text-white px-4 py-2 rounded" style={{ background: "var(--brand)" }}>
  CTA
</button>
```

---

## Spacing

### Cheat sheet rapido

- Margin: `m-4`, `mt-4`, `mb-2`, `mx-auto`, `my-6`
- Padding: `p-4`, `px-6`, `py-2`, `pt-8`, `pl-3`
- Separacion entre hijos:
- `space-y-4` para columna
- `space-x-3` para fila
- Gap en layouts:
- `gap-2`, `gap-4`, `gap-8`

### Ejemplos claros

```tsx
<div className="max-w-xl mx-auto mt-10 p-6 border rounded-xl">
  Caja centrada con margen superior
</div>
```

```tsx
<ul className="space-y-3">
  <li className="p-3 bg-slate-100 rounded">Item 1</li>
  <li className="p-3 bg-slate-100 rounded">Item 2</li>
  <li className="p-3 bg-slate-100 rounded">Item 3</li>
</ul>
```

```tsx
<div className="flex gap-4">
  <button className="px-4 py-2 rounded bg-slate-200">Cancelar</button>
  <button className="px-4 py-2 rounded bg-indigo-600 text-white">Aceptar</button>
</div>
```

### Regla practica de ritmo visual

- Titulos: `mb-2`
- Bloques: `mb-4` o `mb-6`
- Formularios: `space-y-4`
- Paginas: `py-8` o `py-10`

---

## Layout

### FLEX

#### Centrar horizontal

```tsx
<div className="flex justify-center">
  <div className="w-64 h-20 bg-slate-200" />
</div>
```

#### Centrar vertical

```tsx
<div className="h-64 flex items-center border">
  <span>Estoy centrado vertical</span>
</div>
```

#### Centrar todo

```tsx
<div className="min-h-screen flex items-center justify-center">
  <div className="p-8 rounded-xl bg-white shadow">Card centrada</div>
</div>
```

#### Columnas y alineacion

```tsx
<div className="flex flex-col items-start gap-3">
  <h2 className="text-xl font-bold">Perfil</h2>
  <p className="text-slate-600">Datos principales</p>
</div>
```

#### Distribucion entre extremos

```tsx
<div className="flex items-center justify-between">
  <h3 className="font-semibold">Pedidos</h3>
  <button className="text-sm text-indigo-600">Ver todo</button>
</div>
```

#### Wrap para chips/tags

```tsx
<div className="flex flex-wrap gap-2">
  <span className="px-2 py-1 rounded bg-slate-100">React</span>
  <span className="px-2 py-1 rounded bg-slate-100">TypeScript</span>
  <span className="px-2 py-1 rounded bg-slate-100">Tailwind</span>
</div>
```

### GRID

#### Uso basico

```tsx
<div className="grid grid-cols-2 gap-4">
  <div className="bg-slate-100 p-4 rounded">A</div>
  <div className="bg-slate-100 p-4 rounded">B</div>
</div>
```

#### Responsive comun

```tsx
<div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
  <article className="rounded-xl border p-4">Card 1</article>
  <article className="rounded-xl border p-4">Card 2</article>
  <article className="rounded-xl border p-4">Card 3</article>
</div>
```

#### Layout app tipico

```tsx
<div className="grid min-h-screen grid-cols-1 lg:grid-cols-[260px_1fr]">
  <aside className="border-r p-4">Sidebar</aside>
  <main className="p-6">Contenido</main>
</div>
```

#### Formulario 2 columnas

```tsx
<form className="grid grid-cols-1 md:grid-cols-2 gap-4">
  <input className="border rounded p-2" placeholder="Nombre" />
  <input className="border rounded p-2" placeholder="Apellidos" />
  <input className="border rounded p-2 md:col-span-2" placeholder="Email" />
</form>
```

---

## Posicionamiento

### Cheat sheet rapido

- `relative`: referencia para hijos absolutos
- `absolute`: posicion libre dentro del relativo
- `fixed`: pegado a viewport
- `sticky`: se pega al hacer scroll
- utilidades: `top-0`, `right-3`, `inset-0`, `z-50`, `-translate-y-1/2`

### Input con boton dentro (real)

```tsx
<div className="relative">
  <input
    className="w-full rounded-md border p-2 pr-10"
    type="password"
    placeholder="Contrasena"
  />
  <button
    type="button"
    className="absolute right-3 top-1/2 -translate-y-1/2 text-slate-500 hover:text-indigo-600"
  >
    Ver
  </button>
</div>
```

- Esto hace: coloca boton dentro del input.
- Usalo cuando: password show/hide, iconos, limpiar campo.

### Overlay oscuro sobre imagen

```tsx
<div className="relative h-72 overflow-hidden rounded-xl">
  <img
    src="/banner.jpg"
    alt="banner"
    className="h-full w-full object-cover"
  />
  <div className="absolute inset-0 bg-black/45" />
  <div className="absolute inset-0 flex items-center justify-center">
    <h2 className="text-white text-3xl font-bold">Titulo</h2>
  </div>
</div>
```

### Modal fixed centrado

```tsx
<div className="fixed inset-0 z-50 flex items-center justify-center bg-black/40 p-4">
  <div className="w-full max-w-lg rounded-xl bg-white p-6 shadow-2xl">
    Contenido modal
  </div>
</div>
```

### Sticky header

```tsx
<header className="sticky top-0 z-40 border-b bg-white/90 backdrop-blur">
  <div className="mx-auto max-w-6xl px-4 py-3">Header</div>
</header>
```

### Centrar absoluto dentro de contenedor

```tsx
<div className="relative h-56 border rounded">
  <div className="absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2">
    Centro exacto
  </div>
</div>
```

---

## Componentes

### Card base

```tsx
export function Card({ children }: { children: React.ReactNode }) {
  return (
    <div className="rounded-2xl border border-slate-200 bg-white p-6 shadow-sm">
      {children}
    </div>
  )
}
```

- Esto hace: bloque reutilizable limpio.
- Usalo cuando: auth, paneles, resumenes.

### Card premium

```tsx
<div className="rounded-2xl border border-slate-200 bg-white/90 p-6 shadow-[0_10px_40px_rgba(2,6,23,0.08)] backdrop-blur">
  Contenido
</div>
```

### Container centrado

```tsx
<div className="mx-auto w-full max-w-6xl px-4 sm:px-6 lg:px-8">
  Contenido centrado
</div>
```

### Header basico

```tsx
<header className="border-b bg-white">
  <div className="mx-auto flex h-14 max-w-6xl items-center justify-between px-4">
    <strong className="text-slate-900">Mi App</strong>
    <nav className="flex items-center gap-4 text-sm text-slate-600">
      <a className="hover:text-indigo-600" href="#">Inicio</a>
      <a className="hover:text-indigo-600" href="#">Usuarios</a>
    </nav>
  </div>
</header>
```

### Sidebar + content

```tsx
<div className="grid min-h-screen grid-cols-1 lg:grid-cols-[240px_1fr]">
  <aside className="border-r bg-slate-50 p-4">Menu</aside>
  <main className="p-6">Contenido</main>
</div>
```

### Clases globales de componentes (opcional)

```css
@layer components {
  .app-card {
    @apply rounded-2xl border border-slate-200 bg-white p-6 shadow-sm;
  }

  .app-container {
    @apply mx-auto w-full max-w-6xl px-4 sm:px-6 lg:px-8;
  }
}
```

---

## Inputs

### Input basico

```tsx
<input
  className="w-full rounded-md border border-slate-300 p-2"
  type="text"
  placeholder="Nombre"
/>
```

### Input con focus moderno

```tsx
<input
  className="w-full rounded-md border border-[#193133] p-2 text-[#193133] outline-none transition-all duration-300 focus:border-[#8f93ff] focus:ring-1 focus:ring-[#8f93ff]/30"
  type="email"
  placeholder="correo@dominio.com"
/>
```

- Esto hace: borde y anillo al enfocar.
- Usalo cuando: formularios principales.

### Input con icono (muy importante)

```tsx
import { Mail } from "lucide-react"

<div className="relative">
  <Mail className="pointer-events-none absolute left-3 top-1/2 h-4 w-4 -translate-y-1/2 text-slate-400" />
  <input
    className="w-full rounded-md border p-2 pl-9 outline-none focus:ring-1 focus:ring-indigo-500/30"
    type="email"
    placeholder="Email"
  />
</div>
```

### Password show/hide

```tsx
import { Eye, EyeOff } from "lucide-react"

const [showPassword, setShowPassword] = useState(false)

<div className="relative">
  <input
    className="w-full rounded-md border p-2 pr-10"
    type={showPassword ? "text" : "password"}
    placeholder="Contrasena"
  />

  <button
    type="button"
    className="absolute right-3 top-1/2 -translate-y-1/2 text-slate-500 hover:text-indigo-600"
    onClick={() => setShowPassword((s) => !s)}
    aria-label={showPassword ? "Ocultar contrasena" : "Mostrar contrasena"}
  >
    {showPassword ? <EyeOff size={18} /> : <Eye size={18} />}
  </button>
</div>
```

### Error visual

```tsx
<input
  className="w-full rounded-md border border-red-500 bg-red-50 p-2 text-red-900 placeholder:text-red-300 focus:ring-1 focus:ring-red-400/40"
  type="text"
  placeholder="Campo con error"
/>
<p className="mt-1 text-xs text-red-600">Este campo es obligatorio.</p>
```

### Formulario completo reusable

```tsx
<form className="space-y-4 rounded-xl border bg-white p-6 shadow-sm">
  <div>
    <label className="mb-1 block text-sm font-semibold" htmlFor="name">Nombre</label>
    <input id="name" className="w-full rounded-md border p-2" />
  </div>

  <div>
    <label className="mb-1 block text-sm font-semibold" htmlFor="email">Email</label>
    <input id="email" type="email" className="w-full rounded-md border p-2" />
  </div>

  <button className="w-full rounded-md bg-slate-900 p-2 text-white hover:bg-black">
    Enviar
  </button>
</form>
```

---

## Botones

### Boton basico

```tsx
<button className="rounded-md bg-slate-900 px-4 py-2 text-white">Guardar</button>
```

### Boton con hover

```tsx
<button className="rounded-md bg-indigo-600 px-4 py-2 text-white hover:bg-indigo-700">
  Continuar
</button>
```

### Boton con transicion

```tsx
<button className="rounded-md bg-emerald-600 px-4 py-2 text-white transition-colors duration-300 hover:bg-emerald-700">
  Confirmar
</button>
```

### Boton disabled

```tsx
<button className="rounded-md bg-slate-900 px-4 py-2 text-white disabled:cursor-not-allowed disabled:opacity-50" disabled>
  Cargando...
</button>
```

### Boton outline

```tsx
<button className="rounded-md border border-slate-300 bg-white px-4 py-2 text-slate-700 hover:bg-slate-50">
  Cancelar
</button>
```

### Boton shine (tailwind + css)

```tsx
<button className="btn-shine rounded-md px-4 py-2 text-white">
  Crear cuenta
</button>
```

```css
.btn-shine {
  position: relative;
  overflow: hidden;
  background: linear-gradient(135deg, #193133, #2a4f52);
}

.btn-shine::before {
  content: "";
  position: absolute;
  top: 0;
  left: -120%;
  width: 60%;
  height: 100%;
  transform: skewX(-20deg);
  background: linear-gradient(to right, transparent, rgba(255, 255, 255, 0.35), transparent);
  transition: left 0.7s ease;
}

.btn-shine:hover::before {
  left: 130%;
}
```

### Botones con variantes en un helper

```tsx
const base = "inline-flex items-center justify-center rounded-md px-4 py-2 font-semibold transition"

const variants = {
  primary: "bg-indigo-600 text-white hover:bg-indigo-700",
  secondary: "bg-slate-100 text-slate-800 hover:bg-slate-200",
  danger: "bg-red-600 text-white hover:bg-red-700"
}

<button className={`${base} ${variants.primary}`}>Guardar</button>
```

---

## Imagenes

### Background full screen

```tsx
<div
  className="min-h-screen bg-cover bg-center bg-no-repeat"
  style={{ backgroundImage: "url('/images/bg.jpg')" }}
>
  Contenido
</div>
```

### Imagen dentro de div

```tsx
<div className="h-64 w-full overflow-hidden rounded-xl">
  <img src="/images/photo.jpg" alt="Foto" className="h-full w-full object-cover" />
</div>
```

### Imagen redondeada avatar

```tsx
<img src="/images/avatar.png" alt="Avatar" className="h-12 w-12 rounded-full object-cover" />
```

### Overlay oscuro en hero

```tsx
<section className="relative h-[420px]">
  <img src="/images/hero.jpg" alt="Hero" className="h-full w-full object-cover" />
  <div className="absolute inset-0 bg-black/50" />
  <div className="absolute inset-0 flex items-center justify-center">
    <h1 className="text-4xl font-bold text-white">Bienvenido</h1>
  </div>
</section>
```

### Efecto zoom al hover

```tsx
<div className="group overflow-hidden rounded-xl">
  <img
    src="/images/post.jpg"
    alt="Post"
    className="h-56 w-full object-cover transition-transform duration-500 group-hover:scale-105"
  />
</div>
```

---

## Estados

### Hover

```tsx
<button className="bg-slate-900 text-white px-4 py-2 rounded hover:bg-slate-700">
  Hover
</button>
```

### Focus

```tsx
<input className="border rounded p-2 focus:outline-none focus:ring-2 focus:ring-indigo-500/40" />
```

### Active

```tsx
<button className="bg-indigo-600 text-white px-4 py-2 rounded active:scale-[0.98]">
  Active
</button>
```

### Disabled

```tsx
<button className="bg-slate-900 text-white px-4 py-2 rounded disabled:opacity-40 disabled:cursor-not-allowed" disabled>
  Disabled
</button>
```

### Group hover (hijo reacciona)

```tsx
<a className="group flex items-center gap-2 rounded-lg border p-3 hover:bg-slate-50" href="#">
  <span className="font-medium">Abrir reporte</span>
  <span className="text-slate-400 transition-transform group-hover:translate-x-1">-></span>
</a>
```

### Peer (input afecta label)

```tsx
<div>
  <input id="terms" type="checkbox" className="peer sr-only" />
  <label htmlFor="terms" className="cursor-pointer rounded border px-3 py-2 peer-checked:bg-emerald-100 peer-checked:border-emerald-400">
    Acepto terminos
  </label>
</div>
```

---

## Animaciones

### Transition base

```tsx
<button className="transition duration-300 ease-in-out hover:-translate-y-0.5 hover:shadow-lg">
  Boton vivo
</button>
```

### Fade in simple

```tsx
<div className="opacity-0 animate-[fadeIn_.4s_ease_forwards]">Contenido</div>
```

```css
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(6px); }
  to { opacity: 1; transform: translateY(0); }
}
```

### Pulso de estado

```tsx
<span className="inline-flex h-2.5 w-2.5 rounded-full bg-emerald-500 animate-pulse" />
```

### Spinner de carga

```tsx
<div className="h-5 w-5 animate-spin rounded-full border-2 border-slate-300 border-t-slate-800" />
```

### Tooltip con transicion

```tsx
<div className="group relative inline-block">
  <button className="rounded bg-slate-900 px-3 py-1 text-white">Info</button>
  <div className="pointer-events-none absolute left-1/2 top-full mt-2 w-max -translate-x-1/2 rounded bg-black px-2 py-1 text-xs text-white opacity-0 transition-opacity duration-200 group-hover:opacity-100">
    Texto de ayuda
  </div>
</div>
```

### Animacion de entrada por lista

```tsx
<ul className="space-y-2">
  {items.map((item, i) => (
    <li
      key={item.id}
      className="animate-[fadeIn_.4s_ease_forwards] opacity-0"
      style={{ animationDelay: `${i * 60}ms` }}
    >
      {item.name}
    </li>
  ))}
</ul>
```

---

## Trucos

### 1) Centrar pantalla completa

```tsx
<div className="min-h-screen flex items-center justify-center">
  <div className="rounded-xl bg-white p-6 shadow">Centro perfecto</div>
</div>
```

### 2) Card de auth centrada con fondo

```tsx
<div
  className="min-h-screen flex items-center justify-center bg-cover bg-center bg-no-repeat"
  style={{ backgroundImage: "url('/images/auth-bg.png')" }}
>
  <div className="w-full max-w-md rounded-2xl bg-white/85 p-6 shadow-xl backdrop-blur">
    Formulario
  </div>
</div>
```

### 3) Input con icono + boton show/hide

```tsx
<div className="relative">
  <input className="w-full rounded-md border p-2 pl-10 pr-10" type="password" />
  <span className="absolute left-3 top-1/2 -translate-y-1/2 text-slate-400">@</span>
  <button type="button" className="absolute right-3 top-1/2 -translate-y-1/2 text-slate-500">Ver</button>
</div>
```

### 4) Boton moderno reutilizable

```css
@layer components {
  .btn-primary {
    @apply inline-flex items-center justify-center rounded-md bg-indigo-600 px-4 py-2 font-semibold text-white transition-all duration-300 hover:bg-indigo-700 active:scale-[0.99] disabled:cursor-not-allowed disabled:opacity-50;
  }
}
```

```tsx
<button className="btn-primary">Guardar</button>
```

### 5) Overlay oscuro para mejorar lectura

```tsx
<div className="relative">
  <img src="/images/cover.jpg" className="h-80 w-full object-cover" alt="cover" />
  <div className="absolute inset-0 bg-gradient-to-t from-black/70 via-black/20 to-transparent" />
  <div className="absolute bottom-4 left-4 text-white">
    <h3 className="text-2xl font-bold">Titulo</h3>
    <p className="text-sm text-white/85">Subtitulo</p>
  </div>
</div>
```

### 6) Layout rapido para admin

```tsx
<div className="grid min-h-screen grid-cols-1 lg:grid-cols-[220px_1fr]">
  <aside className="border-r bg-slate-50 p-4">Sidebar</aside>
  <main className="p-6">
    <div className="mx-auto max-w-6xl space-y-6">Contenido</div>
  </main>
</div>
```

### 7) Tabla responsive rapida

```tsx
<div className="overflow-x-auto rounded-lg border">
  <table className="min-w-full text-sm">
    <thead className="bg-slate-50 text-slate-600">
      <tr>
        <th className="px-4 py-3 text-left">Nombre</th>
        <th className="px-4 py-3 text-left">Email</th>
      </tr>
    </thead>
    <tbody>
      <tr className="border-t hover:bg-slate-50">
        <td className="px-4 py-3">Ana</td>
        <td className="px-4 py-3">ana@mail.com</td>
      </tr>
    </tbody>
  </table>
</div>
```

### 8) Skeleton de carga

```tsx
<div className="space-y-2">
  <div className="h-4 w-40 animate-pulse rounded bg-slate-200" />
  <div className="h-4 w-full animate-pulse rounded bg-slate-200" />
  <div className="h-4 w-5/6 animate-pulse rounded bg-slate-200" />
</div>
```

### 9) Badge de estado

```tsx
<span className="inline-flex items-center rounded-full bg-emerald-100 px-2.5 py-1 text-xs font-semibold text-emerald-700">
  Activo
</span>
```

### 10) Toast simple fijo

```tsx
<div className="fixed bottom-4 right-4 z-50 rounded-lg bg-slate-900 px-4 py-3 text-sm text-white shadow-lg">
  Cambios guardados
</div>
```

---

## Errores

### 1) Usar `opacity` en contenedor principal por error

Mal:

```tsx
<div className="opacity-60 bg-black">
  <p className="text-white">Texto tambien pierde opacidad</p>
</div>
```

Bien:

```tsx
<div className="bg-black/60">
  <p className="text-white">Texto nitido</p>
</div>
```

### 2) Intentar centrar sin `flex` o `grid`

Mal:

```tsx
<div className="min-h-screen">
  <div className="justify-center items-center">No centra</div>
</div>
```

Bien:

```tsx
<div className="min-h-screen flex items-center justify-center">
  <div>Si centra</div>
</div>
```

### 3) Mezclar global/local sin criterio

Problema:

- Clase global cambia botones de toda la app sin querer.

Solucion:

- Global para utilidades comunes (`btn-primary`, `app-card`).
- Especifico de pagina en CSS module o utilidades en el TSX local.

### 4) No reservar espacio para icono en input

Mal:

```tsx
<input className="w-full border rounded p-2" />
<span className="absolute left-3">@</span>
```

Bien:

```tsx
<div className="relative">
  <span className="absolute left-3 top-1/2 -translate-y-1/2">@</span>
  <input className="w-full border rounded p-2 pl-9" />
</div>
```

### 5) Olvidar estados de focus

Mal:

```tsx
<input className="border rounded p-2 outline-none" />
```

Bien:

```tsx
<input className="border rounded p-2 outline-none focus:ring-2 focus:ring-indigo-500/40 focus:border-indigo-500" />
```

### 6) Usar demasiados valores arbitrarios sin sistema

Problema:

- `mt-[13px]`, `p-[7px]`, `text-[15px]` en todos lados.

Solucion:

- Usa escala tailwind por defecto.
- Arbitrarios solo para casos puntuales.

### 7) No usar responsive

Mal:

```tsx
<div className="grid grid-cols-3 gap-6">...</div>
```

Bien:

```tsx
<div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">...</div>
```

### 8) No controlar overflow en tablas/cards

```tsx
<div className="overflow-x-auto">
  <table className="min-w-full">...</table>
</div>
```

### 9) `absolute` sin padre `relative`

Mal:

```tsx
<div>
  <button className="absolute right-2 top-2">X</button>
</div>
```

Bien:

```tsx
<div className="relative">
  <button className="absolute right-2 top-2">X</button>
</div>
```

### 10) No usar `disabled` en botones async

```tsx
<button disabled={isPending} className="disabled:opacity-50 disabled:cursor-not-allowed">
  {isPending ? "Guardando..." : "Guardar"}
</button>
```

---

## Bloque de referencia ultra rapida

### Texto

```txt
font-semibold | font-bold
text-sm | text-base | text-xl | text-3xl
leading-relaxed | tracking-wide
```

### Espacio

```txt
m-4 mt-6 mb-2 mx-auto
p-4 px-6 py-2
gap-2 gap-4 gap-6
space-y-4
```

### Layout

```txt
flex items-center justify-center
flex justify-between
grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3
```

### Inputs

```txt
w-full rounded-md border p-2
focus:border-indigo-500 focus:ring-1 focus:ring-indigo-500/30
relative + absolute + pr-10 / pl-9
```

### Botones

```txt
rounded-md px-4 py-2
bg-indigo-600 hover:bg-indigo-700 text-white
transition duration-300
disabled:opacity-50 disabled:cursor-not-allowed
```

### Imagenes

```txt
bg-cover bg-center bg-no-repeat
object-cover
rounded-full
absolute inset-0 bg-black/40
```

### Estados

```txt
hover:
focus:
active:
disabled:
group-hover:
peer-checked:
```

---

## Mini kit para copiar al proyecto (opcional)

```css
/* src/styles/custom.css */
@layer components {
  .app-container {
    @apply mx-auto w-full max-w-6xl px-4 sm:px-6 lg:px-8;
  }

  .app-card {
    @apply rounded-2xl border border-slate-200 bg-white p-6 shadow-sm;
  }

  .input-base {
    @apply w-full rounded-md border border-slate-300 p-2 outline-none transition-all duration-300 focus:border-indigo-500 focus:ring-1 focus:ring-indigo-500/30;
  }

  .btn-primary {
    @apply inline-flex items-center justify-center rounded-md bg-indigo-600 px-4 py-2 font-semibold text-white transition-colors duration-300 hover:bg-indigo-700 disabled:cursor-not-allowed disabled:opacity-50;
  }

  .btn-secondary {
    @apply inline-flex items-center justify-center rounded-md border border-slate-300 bg-white px-4 py-2 font-semibold text-slate-700 transition-colors duration-300 hover:bg-slate-50;
  }
}
```

```tsx
<div className="app-container py-8">
  <div className="app-card space-y-4">
    <input className="input-base" placeholder="Email" />
    <div className="flex gap-2">
      <button className="btn-secondary">Cancelar</button>
      <button className="btn-primary">Guardar</button>
    </div>
  </div>
</div>
```

---

Fin del manual.
