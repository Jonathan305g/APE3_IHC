# APE 3 · Rediseño del módulo Ubicaciones (GITT)

> Aplicación de la **Ley de Continuidad de Gestalt** para optimizar el recorrido visual y reducir la carga cognitiva en la gestión de ubicaciones del sistema **GITT – Gestión de Inventario Talleres Tecnológicos**.

![Estado](https://img.shields.io/badge/estado-completado-brightgreen)
![Prototipo](https://img.shields.io/badge/prototipo-Figma-F24E1E)
![Materia](https://img.shields.io/badge/materia-IHC-blue)

---

##  Información académica

| Campo | Detalle |
|---|---|
| **Universidad** | Universidad Técnica de Ambato (UTA) |
| **Facultad** | Ingeniería en Sistemas, Electrónica e Industrial |
| **Carrera** | Software |
| **Nivel y paralelo** | 5to "A" |
| **Asignatura** | Interacción Humano Computador |
| **Docente** | Ing. José Caiza, Mg. |
| **Periodo** | Agosto 2026 – Diciembre 2026 |
| **Actividad** | APE 3. Leyes y Guías de diseño |

### 👥 Integrantes

- Abril Lara Emilio Alexander
- Martinez Jimenez William Fernando
- Gamboa Guaman Jonathan Alexis
- Lozada Marcial Pablo Damian

---

##  Objetivos

### General
Rediseñar la interfaz de registro de ubicaciones aplicando la ley de continuidad de Gestalt para optimizar el recorrido visual y reducir la carga cognitiva del usuario.

### Específicos
1. Analizar la estructura de la interfaz actual para elaborar un boceto de baja fidelidad que justifique la ley de continuidad y defina el recorrido visual esperado.
2. Desarrollar la propuesta de diseño organizando los campos del formulario en una trayectoria continua, clara y predecible.
3. Evaluar la percepción y la carga cognitiva generada por la nueva distribución para corregir fallos visuales y consolidar el producto final.

---

##  Alcance

El análisis se limita al módulo **Configuración › Ubicaciones** e incluye:

- Consulta del listado
- Búsqueda y filtrado
- Creación
- Edición
- Eliminación (con recuperación)

El inicio de sesión y los demás módulos se observan únicamente como contexto de acceso.

---

##  Ley de Continuidad aplicada

La Ley de Continuidad indica que los elementos alineados o dispuestos siguiendo una dirección se perciben como parte de una misma trayectoria.

| Elemento | Continuidad perceptual | Efecto esperado |
|---|---|---|
| Migas de pan | Secuencia horizontal de Configuración a Ubicaciones y a la acción actual | Comprender la ruta y anticipar el regreso |
| Barra de herramientas | Búsqueda y filtro alineados; acción principal en el mismo eje | Explorar primero y crear cuando sea necesario |
| Tabla | Encabezados y datos mantienen columnas; cada fila termina en sus acciones | Comparar registros sin perder la fila |
| Formulario | Etiquetas y campos siguen un eje vertical constante | Completar los datos de arriba hacia abajo |
| Botones finales | Cancelar y Crear/Guardar juntos al cierre | Entender que la tarea concluye ahí |
| Retroalimentación | El mensaje aparece después de la acción | Cerrar mentalmente la operación |

### Recorrido visual esperado

```
Reconocer → Localizar → Comparar → Actuar → Confirmar
(título/ruta) (buscar/filtrar) (revisar tabla) (crear/editar/eliminar) (mensaje de resultado)
```

---

##  Estructura del proyecto por fases

### Fase 1 · Análisis, ideación y boceto
- Concepto de libertad y análisis de la interfaz actual.
- Lluvia de ideas (12 ideas) agrupadas en 4 alternativas puntuadas:

| Alternativa | Claridad | Continuidad | Control | Viabilidad | Total |
|---|:-:|:-:|:-:|:-:|:-:|
| **A. Formulario por pasos y secciones** ✅ | 5 | 5 | 4 | 5 | **19** |
| B. Vista jerárquica tipo árbol | 4 | 4 | 4 | 3 | 15 |
| C. Eliminación con deshacer | 4 | 3 | 5 | 3 | 15 |
| D. Panel de ocupación y capacidad | 3 | 3 | 3 | 4 | 13 |

- Idea seleccionada: **flujo continuo con formulario por pasos y agrupación semántica**.
- Bocetos de baja fidelidad del listado y del formulario.

### Fase 2 · Diseño y prototipo en Figma
Prototipo navegable de alta fidelidad que conserva la identidad visual de GITT y cubre:

- **Listado principal:** registros con descripción, tipo, piso, referencia, capacidad, ocupación y acciones.
- **Búsqueda y filtrado:** combina nombre + tipo y muestra el número de coincidencias, con acción *Limpiar*.
- **Creación (asistente de 3 pasos):** Datos básicos → Detalles → Revisar.
- **Edición:** mismo asistente con datos precargados y revisión comparativa de cambios (valor anterior tachado + etiqueta *Modificado*).
- **Eliminación:** modal de confirmación con el nombre del registro y acción **Deshacer** temporal.

### Fase 3 · Evaluación de la interfaz

| Técnica | Resultado |
|---|---|
| Verificación por tareas (T1–T6) | 6 de 6 tareas cumplen |
| Evaluación heurística (10 criterios) | **44 / 50 (88 %)** |
| Recorrido cognitivo | Objetivo, acción y resultado reconocibles en todas las tareas |
| Accesibilidad (POUR) | **14 / 20 (70 %)** |
| Mapas predictivos de atención visual | Jerarquía coherente con la acción esperada |

### Fase 4 · Mejora y presentación
Hallazgos priorizados y convertidos en mejoras concretas:

| ID | Hallazgo | Severidad | Tratamiento |
|---|---|---|---|
| H01 | Iconos Editar/Eliminar con área reducida | Alta | Objetivo de 44×44 px y tooltip |
| H02 | Sin estados de validación inline | Alta | Error bajo el campo y foco al primer error |
| H03 | Contraste de textos secundarios | Alta | Relación mínima 4.5:1 |
| H04 | Buscador global y del módulo similares | Media | Explicitar alcance en etiqueta y placeholder |
| H05 | Acciones inferiores fuera de vista | Media | Pie de acciones fijo |
| H06 | Tiempo de Deshacer no cuantificado | Media | Cuenta regresiva o barra temporal |
| H07 | Foco y teclado no visibles | Alta | Tabulación, foco visible, Escape y retorno de foco |
| H08 | Sin estados de carga, error o vacío | Media | Estados alternativos con recuperación |
| H09 | Ocupación debe compararse con capacidad | Alta | Impedir que la ocupación supere la capacidad |

**Orden de ejecución:** primero **P0** (accesibilidad, teclado, validación y contraste), después **P1** (búsqueda, acciones persistentes, Deshacer y estados alternativos) y por último repetir las tareas T1–T6.

---

##  Campos del formulario de ubicación

| Campo | Condición | Regla |
|---|---|---|
| Nombre | Obligatorio | Máximo 30 caracteres |
| Descripción | Obligatorio | Máximo 250 caracteres |
| Ubicación padre | Opcional | Puede quedar en *Ninguna* |
| Tipo | Obligatorio | Selección desde catálogo (oficina, almacén, estante, laboratorio…) |
| Piso | Opcional | Letras, números, guiones y guiones bajos |
| Referencia | Obligatorio | Máximo 50 caracteres |
| Capacidad y unidad | Obligatorio | Valor numérico no negativo |
| Ocupación | Opcional | No debe superar la capacidad |
| Notas | Opcional | Máximo 250 caracteres |

---

## 🔗 Evidencias

| Evidencia | Enlace |
|---|---|
|  Prototipo navegable en Figma | [Abrir prototipo](#) <!-- Reemplazar con el enlace de Figma --> |
|  Informe de guía práctica (PDF) | [Ver informe](./docs/INFORME_DE_GUIA_PRACTICA3.pdf) <!-- Ajustar ruta --> |

---

##  Estructura sugerida del repositorio

```
APE3-IHC/
├── README.md
├── docs/
│   └── INFORME_DE_GUIA_PRACTICA3.pdf
└── assets/
    ├── bocetos/        # Boceto de baja fidelidad (listado y formulario)
    ├── prototipo/      # Capturas del prototipo en Figma
    └── evaluacion/     # Mapas de atención y matrices
```

---
##  Herramientas utilizadas

- **Figma** – prototipado de alta fidelidad
- **Herramientas ofimáticas** – documentación e informe
- **Inteligencia Artificial** – apoyo en ideación y redacción (TAC declarada en el informe)

---

## Resultados

- Prototipo navegable que representa consulta, búsqueda y filtrado, creación, edición, eliminación y recuperación.
- Asistente de tres pasos reutilizado en crear y editar, con revisión previa y mensajes de resultado específicos.
- Evaluación con **88 %** en heurísticas y **70 %** en accesibilidad, con un plan de mejora priorizado (P0 / P1).

---

##  Referencias

> Agregar aquí las referencias en formato IEEE (Gestalt, heurísticas de Nielsen, WCAG, etc.).

---

<p align="center">
  Universidad Técnica de Ambato · Carrera de Software · 2026
</p>
