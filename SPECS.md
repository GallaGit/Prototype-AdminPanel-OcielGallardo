# AgentHub Frontend Specification

## 1. Product Overview

### Que es AgentHub

AgentHub es una plataforma SaaS donde empresas alquilan agentes de IA configurables mediante skills reutilizables. Cada agente representa una capacidad lista para usar dentro de una empresa.

### Que problema resuelve

AgentHub centraliza la supervision de agentes, usuarios, skills, contratos y errores en una sola interfaz. El panel evita que un administrador tenga que revisar multiples sistemas o estados dispersos.

### Quien es el administrador que utilizara el panel

El usuario principal es un administrador interno de una empresa cliente. Puede ser un operations manager, un admin tecnico o un lider de automatizacion. Necesita monitorear estado, uso, configuracion visual y contratos sin depender de backend real.

### Objetivos del dashboard

- Mostrar el estado general del negocio de forma inmediata.
- Permitir navegar entre las 6 areas principales del producto.
- Simular interacciones reales con dropdowns, modales y listas colapsables.
- Servir como referencia visual para futuros desarrolladores backend.

## 2. Technology Stack & Constraints

La implementacion debe usar exclusivamente:

- HTML5
- TailwindCSS via CDN
- Vanilla JavaScript

Restricciones explicitas:

- Sin React
- Sin Vue
- Sin Angular
- Sin jQuery
- Sin TypeScript
- Sin backend
- Sin API calls
- Datos completamente hardcodeados

Implicaciones practicas:

- Todo debe vivir en una sola pagina.
- Todas las interacciones deben resolverse en el navegador.
- Ningun boton visible puede quedar sin comportamiento.

## 3. Layout Specification

### Sidebar

- Navegacion persistente.
- Siempre visible en desktop.
- Contiene las 6 secciones: Dashboard, User Management, Agent Management, Skills, Agent Rentals y Error Logs.
- Estado activo resaltado con color, fondo e indicador visual.
- En mobile se comporta como panel overlay.

### Topbar

- Muestra el titulo de la seccion actual.
- Incluye toggle Dark/Light Mode.
- Puede incluir una accion global o una busqueda simple si ayuda a la demo.
- Debe mantenerse estable en desktop y mobile.

### Main Content Area

- Responsive.
- Padding consistente en todas las secciones.
- Scroll independiente cuando el layout lo permita.
- Cada seccion debe sentirse separada mediante espacio, fondo o tarjetas.

## 4. Section Specifications

Cada requisito de seccion debe definirse por componente, contenido, apariencia y comportamiento.

### Dashboard

#### Especificacion 1

- Componente: grid responsive 2x2 de metricas.
- Contenido: total de usuarios, agentes activos, skills activas e ingresos mensuales.
- Apariencia: tarjetas con icono, etiqueta y valor principal. Cada tarjeta usa un color diferenciador.
- Comportamiento: en desktop se ve como grid 2x2 y en mobile baja a una columna.

#### Especificacion 2

- Componente: tarjetas de metricas.
- Contenido: icono, nombre de la metrica, valor y texto secundario opcional.
- Apariencia: superficie clara, borde suave, sombra ligera y valor con mayor peso visual.
- Comportamiento: hover sutil y sin desplazar el layout.

#### Especificacion 3

- Componente: area placeholder para grafico semanal.
- Contenido: titulo y grafico simulado de actividad semanal.
- Apariencia: panel ancho con barras construidas con HTML y Tailwind.
- Comportamiento: no depende de librerias ni APIs, pero debe parecer un grafico funcional.

### User Management

#### Especificacion 1

- Componente: tabla de usuarios.
- Contenido: nombre, email, rol, empresa, estado y ultima actividad.
- Apariencia: tabla administrativa limpia con encabezados visibles y badges de estado.
- Comportamiento: en pantallas pequenas puede usar scroll horizontal o tarjetas apiladas.

#### Especificacion 2

- Componente: dropdown por fila.
- Contenido: acciones como View Details, Suspend User y Reset Access.
- Apariencia: trigger compacto con menu flotante alineado a la fila.
- Comportamiento: se abre por click y se cierra por click externo, Escape o al elegir una accion.

#### Especificacion 3

- Componente: modal de detalle.
- Contenido: perfil del usuario, agentes asignados y actividad reciente.
- Apariencia: modal centrado con backdrop oscuro y boton de cierre visible.
- Comportamiento: cierre por boton, backdrop y tecla Escape.

### Agent Management

#### Especificacion 1

- Componente: lista de agentes.
- Contenido: nombre, categoria, owner, estado, resumen y metricas basicas.
- Apariencia: tarjetas o filas enriquecidas con badges y acciones.
- Comportamiento: cada agente debe permitir ver skills o abrir configuracion.

#### Especificacion 2

- Componente: skills colapsables.
- Contenido: lista de skills asociadas al agente.
- Apariencia: bloque secundario con chips o badges.
- Comportamiento: expansion y colapso con animacion simple.

#### Especificacion 3

- Componente: dropdown de acciones y modal de configuracion.
- Contenido: acciones como Configure, Pause Agent y Duplicate, mas detalle visual del agente.
- Apariencia: dropdown compacto y modal ancho con bloques de configuracion.
- Comportamiento: el modal abre desde una accion del dropdown y se cierra con los patrones globales.

### Skills

#### Especificacion 1

- Componente: catalogo de skills.
- Contenido: nombre, categoria, descripcion y nivel de uso.
- Apariencia: grid o lista de tarjetas compactas con icono y badge.
- Comportamiento: reflow responsive sin perder legibilidad.

#### Especificacion 2

- Componente: explicacion contextual.
- Contenido: texto breve que explique para que sirve cada skill.
- Apariencia: descripcion secundaria debajo del nombre.
- Comportamiento: siempre visible, sin depender de tooltip.

#### Especificacion 3

- Componente: indicador de uso y dropdown de acciones.
- Contenido: contador de uso y acciones como View Dependencies o Disable.
- Apariencia: badge o mini barra de uso junto a trigger de acciones.
- Comportamiento: dropdown funcional con cierre por click externo o Escape.

### Agent Rentals

#### Especificacion 1

- Componente: tabla de contratos.
- Contenido: cliente, agente, inicio, renovacion y estado.
- Apariencia: tabla ordenada con columnas alineadas y badges de estado.
- Comportamiento: responsive sin perder lectura.

#### Especificacion 2

- Componente: skills asociadas.
- Contenido: chips con las skills incluidas en cada contrato.
- Apariencia: grupo compacto de badges dentro de la fila.
- Comportamiento: si hay muchas skills se puede resumir visualmente sin romper la tabla.

#### Especificacion 3

- Componente: importes y modal de desglose.
- Contenido: monto mensual, extras y total.
- Apariencia: importes destacados y modal centrado con bloques por concepto.
- Comportamiento: el modal abre desde la fila y cierra por boton, backdrop o Escape.

### Error Logs

#### Especificacion 1

- Componente: tabla de errores.
- Contenido: timestamp, agente, modulo, mensaje corto y estado.
- Apariencia: tabla sobria con jerarquia clara y opcion de texto tecnico.
- Comportamiento: cada fila permite abrir detalle o usar acciones.

#### Especificacion 2

- Componente: badges de gravedad.
- Contenido: Low, Medium, High y Critical.
- Apariencia: badges codificados por color y con texto legible.
- Comportamiento: deben mantenerse distinguibles en light y dark mode.

#### Especificacion 3

- Componente: dropdown de acciones y modal con stack trace.
- Contenido: acciones como View Trace, Assign y Resolve, mas stack trace hardcodeado.
- Apariencia: modal amplio con bloque tecnico y metadatos visibles.
- Comportamiento: dropdown funcional y modal cerrable por boton, backdrop y Escape.

## 5. Reusable Component Inventory

### Sidebar

Proposito: navegar entre secciones.
Reutilizacion: mismo patron para todos los items de menu.

### Topbar

Proposito: dar contexto y exponer acciones globales.
Reutilizacion: misma estructura para todas las vistas del panel.

### Metric Card

Proposito: resumir KPIs.
Reutilizacion: se usa en Dashboard y en bloques de resumen secundarios.

### Data Table

Proposito: mostrar datos administrativos ordenados.
Reutilizacion: usuarios, contratos y errores.

### Action Dropdown

Proposito: agrupar acciones secundarias.
Reutilizacion: usuarios, agentes, skills y logs.

### Modal

Proposito: mostrar detalle sin salir de la pagina.
Reutilizacion: detalle de usuario, configuracion de agente, desglose de contrato y stack trace.

### Badge

Proposito: comunicar estado, categoria o severidad.
Reutilizacion: usuarios, agentes, skills, contratos y errores.

### Collapsible Skill List

Proposito: mostrar skills relacionadas bajo demanda.
Reutilizacion: principalmente en Agent Management.

### Dark Mode Toggle

Proposito: cambiar el tema visual.
Reutilizacion: control global persistente en la topbar.

### Status Indicator

Proposito: reforzar estados con color y texto.
Reutilizacion: agentes, usuarios, contratos y logs.

## 6. Design System

### Colors

- Primary: color principal para acciones, links y estado activo.
- Success: color para estados activos o resueltos.
- Warning: color para alertas y estados intermedios.
- Danger: color para errores criticos y acciones destructivas.
- Neutral: escala para fondos, bordes y texto secundario.

### Typography

- Jerarquia de headings: titulo de pagina, titulo de seccion y titulo de bloque claramente diferenciados.
- Texto de tablas: compacto, legible y con encabezados mas fuertes que el contenido.
- Texto de badges: pequeno, semibold y facil de escanear.

### Spacing

- Separacion entre secciones: consistente y amplia para no saturar la pantalla.
- Padding de cards: suficiente para que el contenido respire.
- Gaps de grids: uniformes en metricas, catalogos y paneles.

## 7. Interactions

### Dropdowns

- Se abren al hacer click en el trigger.
- Solo un dropdown puede estar abierto al mismo tiempo.
- Se cierran por click externo, Escape o seleccion de accion.

### Modales

- Se abren desde botones o acciones de fila.
- Deben mostrar backdrop.
- Se cierran con boton, click sobre backdrop o Escape.

### Skills colapsables

- Se expanden desde un trigger visible.
- La animacion debe ser simple y rapida.
- El contenido expandido no debe romper el layout.

### Cambio Dark/Light Mode

- Debe alternar clases o atributos globales.
- Debe afectar sidebar, topbar, tarjetas, tablas, modales y badges.
- Puede persistir opcionalmente en localStorage.

### Hover states

- Botones, filas, tarjetas y links muestran feedback visual.
- El hover debe ser sutil y consistente.

### Focus states

- Todo control interactivo debe tener focus visible.
- El focus debe ser claro en ambos temas.

## 8. Acceptance Criteria

1. La navegacion lateral es visible en desktop.
2. Las 6 secciones principales existen.
3. El estado activo del sidebar se resalta visualmente.
4. La topbar muestra el titulo de la seccion actual.
5. El Dark mode funciona sin recargar la pagina.
6. El Light mode funciona al volver desde Dark mode.
7. El Dashboard incluye un grid responsive 2x2 de metricas.
8. Cada tarjeta de metrica muestra icono, etiqueta y valor.
9. Existe un placeholder visible para grafico semanal.
10. User Management incluye tabla de usuarios.
11. Cada fila de usuarios tiene dropdown funcional.
12. User Management incluye modal de detalle funcional.
13. Agent Management incluye lista de agentes.
14. Los agentes muestran skills colapsables funcionales.
15. Agent Management incluye dropdown de acciones funcional.
16. Agent Management incluye modal de configuracion funcional.
17. Skills incluye catalogo, explicacion contextual e indicador de uso.
18. Agent Rentals muestra tabla de contratos con skills e importes.
19. Agent Rentals incluye modal de desglose funcional.
20. Error Logs muestra tabla de errores con badges de gravedad.
21. Error Logs incluye dropdown de acciones funcional.
22. Error Logs incluye modal con stack trace funcional.
23. Todos los modales tienen backdrop funcional.
24. Todos los dropdowns se cierran al hacer click fuera.
25. Todos los datos mostrados estan hardcodeados.
26. El layout es responsive en desktop, tablet y mobile.
27. La implementacion usa exclusivamente TailwindCSS via CDN y Vanilla JavaScript.
28. No hay llamadas a APIs ni dependencias de backend.
