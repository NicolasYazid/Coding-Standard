# 📘 Estándar de codificación C# — Gin Rummy

> **Índice de control del estándar definitivo.**
> Una casilla marcada (☑) significa que la regla está **aprobada como definitiva**.
> Este archivo solo lista las reglas; su contenido completo vive en el documento del estándar.
> Las fuentes de cada regla aprobada están en [REFERENCIAS.md](REFERENCIAS.md).
> Evidencia de cambios respecto al estándar base: [NUEVAS.md](NUEVAS.md) · [MODIFICADAS.md](MODIFICADAS.md) · [ELIMINADAS.md](ELIMINADAS.md).

---

## 📊 Progreso

| # | Sección | Aprobadas | Total |
|---|---------|:---------:|:-----:|
| 1 | [Idioma](#1-idioma) | 2 | 2 |
| 2 | [Reglas de nombrado](#2-reglas-de-nombrado) | 12 | 45 |
| 3 | [Organización del proyecto](#3-organización-del-proyecto) | 0 | 0 |
| 4 | [Estilo de código](#4-estilo-de-código) | 0 | 16 |
| 5 | [Prácticas de programación](#5-prácticas-de-programación) | 0 | 6 |
| 6 | [Manejo de errores y excepciones](#6-manejo-de-errores-y-excepciones) | 0 | 13 |
| 7 | [Manejo de logs](#7-manejo-de-logs) | 0 | 12 |
| 8 | [Comentarios](#8-comentarios) | 0 | 12 |
| 9 | [Estructuras de control](#9-estructuras-de-control) | 23 | 23 |
| 10 | [Conexión con la base de datos](#10-conexión-con-la-base-de-datos--almacenamiento-local) | 0 | 0 |
| 11 | [Pruebas unitarias](#11-pruebas-unitarias) | 0 | 7 |
| 12 | [Validación de entrada y seguridad](#12-validación-de-entrada-y-seguridad) | 0 | 0 |
| 13 | [DTOs y modelos de dominio](#13-dtos-y-modelos-de-dominio) | 0 | 0 |
| 14 | [Manejo de documentos / Assets](#14-manejo-de-documentos--assets) | 0 | 0 |
| 15 | [Gestión gráfica](#15-gestión-gráfica) | 0 | 0 |
| 16 | [Dependencias externas y de seguridad](#16-dependencias-externas-y-de-seguridad) | 0 | 0 |
| | **Total** | **37** | **136** |

---

## 🔖 Leyenda

| Marca | Significado |
|:-----:|-------------|
| ☑ | Regla aprobada (definitiva) |
| ☐ | Regla pendiente de revisión |
| 🆕 | Regla nueva (no existía en el estándar base) |
| ✏️ | Regla en corrección |
| 🗑️ | Regla propuesta para eliminar |
| 🔗 | Depende de otra regla (se indica cuál) |
| 🕳️ | Subsección sin reglas: hay que crearlas o eliminar la subsección |
| ⚠️ | La regla depende de una versión de C# superior a la del proyecto (C# 7.3, .NET Framework 4.8) |

**IDs:** cada regla tiene un número fijo (`sección.subsección.regla`). Si una regla se elimina, pasa a la sección [Reglas eliminadas](#-reglas-eliminadas) y su número no se reutiliza.

---

## 1. Idioma

### 1.1 Reglas sobre el idioma
- [x] **1.1.1** Identificadores en inglés
- [x] **1.1.2** Idioma de los comentarios y la documentación

---

## 2. Reglas de nombrado

### 2.1 Variables
- [x] **2.1.1** Formato de variables locales
- [x] **2.1.2** Variables de instancia
- [x] **2.1.3** Contadores de bucle
- [x] **2.1.4** Colecciones
- [x] **2.1.5** Booleanos con prefijo `is` (estado)
- [x] **2.1.6** Booleanos con prefijo `has` (posesión o estado completado)
- [x] **2.1.7** Booleanos con prefijo `can` (capacidad o permiso)
- [x] **2.1.8** Declaración única
- [x] **2.1.10** Exención de abreviatura para excepciones (`ex`)
- [x] **2.1.11** Prefijo estático `s_`

### 2.2 Propiedades
- [x] **2.2.1** Nomenclatura de propiedades
- [ ] **2.2.2** Plantilla vacía sin título ni contenido 🗑️
- [ ] **2.2.3** Plantilla vacía sin título ni contenido 🗑️
- [ ] **2.2.4** Declaración correcta de propiedades
- [ ] **2.2.5** Modificación de valor en propiedades
- [x] **2.2.6** Set restringido 🆕

### 2.3 Componentes de interfaz gráfica
- 🕳️ Sin reglas

### 2.4 Identificadores de interfaz
- 🕳️ Sin reglas

### 2.5 Constantes
- [ ] **2.5.1** Nomenclatura (PascalCase)
- [ ] **2.5.2** Inmutabilidad en tiempo de compilación (`const`)
- [ ] **2.5.3** Inmutabilidad en tiempo de ejecución (`static readonly`)

### 2.6 Métodos
- [ ] **2.6.1** Nomenclatura (PascalCase)
- [ ] **2.6.2** Verbos o frases verbales
- [ ] **2.6.3** Límite de parámetros

### 2.7 Manejadores de eventos (prefijos On, Handle, Toggle)
- [ ] **2.7.1** Prefijo `On` (reacción a eventos del sistema)
- [ ] **2.7.2** Prefijo `Handle` (procesamiento de entradas)
- [ ] **2.7.3** Prefijo `Toggle` (alternancia de estados booleanos)
- [ ] **2.7.4** Descriptores directos (sin prefijo)
- [ ] **2.7.5** Límite de parámetros en eventos

### 2.8 Métodos de prueba unitaria
- [ ] **2.8.1** Estructura de nomenclatura (prefijo `Test`)
- [ ] **2.8.2** Nombres descriptivos vs. genéricos
- [ ] **2.8.3** Cobertura de lógica central y flujos existentes
- [ ] **2.8.4** Atributo de prueba y exenciones

### 2.9 Clases
- [ ] **2.9.1** Nomenclatura base (PascalCase)
- [ ] **2.9.2** Prohibición de prefijos especiales
- [ ] **2.9.3** Acrónimo arquitectónico (`Dao`)
- [ ] **2.9.4** Acrónimo arquitectónico (`Dto`)

### 2.10 Clases controladoras
- [ ] **2.10.1** Sufijo obligatorio y nomenclatura completa
- [ ] **2.10.2** Eliminación de prefijos tecnológicos

### 2.11 Interfaces
- [ ] **2.11.1** Prefijo obligatorio y convención base (PascalCase)
- [ ] **2.11.2** Prohibición de redundancias

### 2.12 Sufijos por responsabilidad
- [ ] **2.12.1** Acceso a datos (`Dao`)
- [ ] **2.12.2** Servicios lógicos (`Service`)
- [ ] **2.12.3** Procesamiento de eventos (`Handler`)
- [ ] **2.12.4** Validación de estados (`Validator`)
- [ ] **2.12.5** Lógica auxiliar (`Common`)
- [ ] **2.12.6** Excepciones personalizadas (sufijo `Exception`)

---

## 3. Organización del proyecto

### 3.1 Capa de acceso a datos / Persistencia
- 🕳️ Sin reglas

### 3.2 Contratos e implementaciones DAO
- 🕳️ Sin reglas

### 3.3 Capa lógica (Core del videojuego)
- 🕳️ Sin reglas

### 3.4 Capa GUI (Interfaz visual del juego)
- 🕳️ Sin reglas

### 3.5 Separación Vistas / Controladores
- 🕳️ Sin reglas

### 3.6 Control de versiones
- 🕳️ Sin reglas

---

## 4. Estilo de código

### 4.1 Formato y estructura general
- [ ] **4.1.1** Indentación base (4 espacios)
- [ ] **4.1.2** Límite de columna (140 caracteres) y ruptura de línea
- [ ] **4.1.3** Indentación en líneas continuadas

### 4.2 Uso de espacios en blanco
- [ ] **4.2.1** Separación vertical entre métodos y constructores
- [ ] **4.2.2** Agrupación vertical de propiedades simples (auto-propiedades)
- [ ] **4.2.3** Separación vertical de propiedades complejas
- [ ] **4.2.4** Agrupación lógica y prohibición de múltiples líneas en blanco
- [ ] **4.2.5** Espacios en operadores binarios
- [ ] **4.2.6** Espacios en estructuras de control
- [ ] **4.2.7** Ausencia de espacios en métodos
- [ ] **4.2.8** Espaciado en delimitadores de listas (comas)

### 4.3 Organización del código en el archivo
- [ ] **4.3.1** Orden estructural del archivo
- [ ] **4.3.2** Agrupación y orden de directivas `using`
- [ ] **4.3.3** Declaración única por archivo

### 4.4 Orden de miembros en la clase
- [ ] **4.4.1** Jerarquía estructural de miembros
- [ ] **4.4.2** Orden de métodos por visibilidad

---

## 5. Prácticas de programación

### 5.1 Un único return
- [ ] **5.1.1** Punto único de retorno en métodos con valor de retorno

### 5.2 Prevención de números mágicos
- [ ] **5.2.1** Prevención de números mágicos

### 5.3 Número máximo de operadores en expresiones
- [ ] **5.3.1** Número máximo de operaciones en expresiones

### 5.4 Complejidad ciclomática
- [ ] **5.4.1** Complejidad ciclomática

### 5.5 Manejo de nulos
- [ ] **5.5.1** Prohibición de retorno nulo en colecciones

### 5.6 Uso de expresiones lambda
- [ ] **5.6.1** Regla sin definir (sin título ni contenido) ✏️

---

## 6. Manejo de errores y excepciones

### 6.1 Uso de bloques try-catch y manejo de excepciones específicas
- [ ] **6.1.1** Captura de excepciones específicas
- [ ] **6.1.2** Prohibición de bloques `catch` vacíos
- [ ] **6.1.3** Priorización de excepciones del sistema 🗑️ 🔗 duplicada con 6.4.2

### 6.2 Orden jerárquico en los bloques catch
- [ ] **6.2.1** Orden de mayor a menor especificidad
- [ ] **6.2.2** Jerarquía con excepciones personalizadas

### 6.3 Propagación y empaquetamiento de excepciones
- [ ] **6.3.1** Propagación directa (`throw;`)
- [ ] **6.3.2** Empaquetamiento de excepciones (`InnerException`)

### 6.4 Jerarquía de excepciones personalizadas del videojuego
- [ ] **6.4.1** Creación de la excepción base del dominio
- [ ] **6.4.2** Priorización de excepciones del sistema 🔗 duplicada con 6.1.3
- [ ] **6.4.3** Herencia de excepciones específicas (jerarquía de un solo nivel)

### 6.5 Uso obligatorio de la sentencia using
- [ ] **6.5.1** Prohibición de liberación manual (`Dispose`)
- [ ] **6.5.2** Preferencia por la declaración simplificada (C# 8.0+) ⚠️ no disponible en C# 7.3
- [ ] **6.5.3** Uso del bloque tradicional para liberación anticipada

---

## 7. Manejo de logs

### 7.1 Prohibición de la salida estándar
- [ ] **7.1.1** Prohibición de consola para eventos operativos e informativos
- [ ] **7.1.2** Prohibición de volcado de excepciones en consola

### 7.2 Declaración e inicialización del logger (`ILogger`)
- [ ] **7.2.1** Declaración de la variable de instancia (`ILogger<T>`)
- [ ] **7.2.2** Inicialización mediante inyección de dependencias

### 7.3 Categorización y niveles de log
- [ ] **7.3.1** Nivel Trace
- [ ] **7.3.2** Nivel Debug
- [ ] **7.3.3** Nivel Info
- [ ] **7.3.4** Nivel Warning
- [ ] **7.3.5** Nivel Error
- [ ] **7.3.6** Nivel Fatal (Critical)

### 7.4 Marcadores de posición
- [ ] **7.4.1** Estructura obligatoria de marcadores de posición
- [ ] **7.4.2** Nomenclatura de los marcadores de posición (PascalCase)

---

## 8. Comentarios

### 8.1 Reglas individuales para los comentarios
- [ ] **8.1.1** Comentarios de una línea (`//`): formato y ubicación
- [ ] **8.1.2** Comentarios en bloque (`/* */`)
- [ ] **8.1.3** Justificación lógica del comentario (el "por qué", no el "qué")
- [ ] **8.1.4** Prohibición de comentarios redundantes
- [ ] **8.1.5** Documentación XML (`///`): cuándo se usa
- [ ] **8.1.6** Documentación XML (`///`): etiquetas obligatorias
- [ ] **8.1.7** Documentación XML: formato válido
- [ ] **8.1.8** Comentario especial `TODO`
- [ ] **8.1.9** Comentario especial `FIXME`
- [ ] **8.1.10** Ciclo de vida de `TODO` y `FIXME`
- [ ] **8.1.11** Prohibición de código muerto comentado
- [ ] **8.1.12** Balance y densidad de comentarios

---

## 9. Estructuras de control

### 9.1 Uso de llaves
- [x] **9.1.1** Estilo de llaves (Allman)
- [x] **9.1.2** Obligatoriedad de las llaves
- [x] **9.1.3** Interior del bloque
- [x] **9.1.4** Formato de los accesores 🆕
- [x] **9.1.5** Formato de los inicializadores de objeto 🆕
- [x] **9.1.6** Formato de los inicializadores de colección 🆕
- [x] **9.1.7** Formato de los tipos anónimos 🆕
- [x] **9.1.8** Formato de los inicializadores de arreglo 🆕

### 9.2 Sentencias condicionales (`if`, `else`)
- [x] **9.2.1** Agrupación de las cláusulas
- [x] **9.2.2** Prohibición de comparar con literales booleanos

### 9.3 Bucles (`for`, `while`, `do-while`)
- [x] **9.3.1** Ámbito de la variable de control
- [x] **9.3.2** Recorrido de colecciones
- [x] **9.3.3** Prohibición de modificar la colección recorrida
- [x] **9.3.5** Condición de salida en la cabecera

### 9.4 Sentencias `switch`
- [x] **9.4.1** Elección del `switch`
- [x] **9.4.2** Uso de llaves en el cuerpo de un `case`
- [x] **9.4.3** Cláusula `default` obligatoria
- [x] **9.4.4** Agrupación de etiquetas
- [x] **9.4.5** Cuerpo de la sección

### 9.5 Uso del operador ternario
- [x] **9.5.1** Ámbito de uso
- [x] **9.5.2** Prohibición del ternario anidado
- [x] **9.5.3** Ramas booleanas explícitas
- [x] **9.5.4** Extensión del ternario

---

## 10. Conexión con la base de datos / Almacenamiento local

### 10.1 Usuarios de base de datos
- 🕳️ Sin reglas

### 10.2 Credenciales y archivo de configuración
- 🕳️ Sin reglas

### 10.3 Manejo de conexiones
- 🕳️ Sin reglas

### 10.4 Manejo seguro de recursos
- 🕳️ Sin reglas

### 10.5 Manejo de transacciones
- 🕳️ Sin reglas

### 10.6 Consultas parametrizadas
- 🕳️ Sin reglas

---

## 11. Pruebas unitarias

### 11.1 Ubicación y nomenclatura
- [ ] **11.1.1** Ubicación lógica (namespaces)
- [ ] **11.1.2** Nomenclatura de la clase de prueba

### 11.2 Estructura de un test
- [ ] **11.2.1** Patrón lógico (Arrange, Act, Assert) sin comentarios
- [ ] **11.2.2** Límite de aserciones
- [ ] **11.2.3** Configuración inicial compartida

### 11.3 Métodos builders en pruebas
- [ ] **11.3.1** Nomenclatura y visibilidad
- [ ] **11.3.2** Límite de parámetros en constructores auxiliares e inicialización por defecto

---

## 12. Validación de entrada y seguridad

### 12.1 Centralización de validaciones
- 🕳️ Sin reglas

### 12.2 Almacenamiento de contraseñas
- 🕳️ Sin reglas

### 12.3 Gestión de sesión
- 🕳️ Sin reglas

---

## 13. DTOs y modelos de dominio

### 13.1 Estructura de un DTO
- 🕳️ Sin reglas

---

## 14. Manejo de documentos / Assets

### 14.1 Manejo y guardado de archivos
- 🕳️ Sin reglas

### 14.2 Generación automática de documentos
- 🕳️ Sin reglas

---

## 15. Gestión gráfica

### 15.1 Navegación entre vistas / escenas
- 🕳️ Sin reglas

### 15.2 Mensajes e indicadores al usuario
- 🕳️ Sin reglas

---

## 16. Dependencias externas y de seguridad

### 16.1 Vulnerabilidades conocidas
- 🕳️ Sin reglas

---

## 🗑️ Reglas eliminadas

- ~~**1.1.3** Idioma de los mensajes de error (logs y excepciones)~~ — sin fuente de C# que la respalde; Microsoft recomienda traducir los mensajes de excepción en aplicaciones localizadas.
- ~~**9.3.4** Elección del `do-while`~~ — solo describía para qué sirve un `do-while`; no prevenía ningún defecto.
- ~~**9.2.3** Cláusula de guarda~~ — eliminada por decisión del equipo; su redacción castigaba métodos `void` con un solo `if` y dependía de la regla 5.1.1.
- ~~**2.1.9** Prevención de sombreado de datos~~ — en C# 7.3 el compilador ya impide el sombreado entre variables locales (CS0136), y las reglas 2.1.1, 2.1.2 y 2.1.11 impiden que una variable local se llame igual que un campo.

---

## 📝 Bitácora de cambios

| Fecha | Regla | Cambio |
|-------|-------|--------|
| 2026-11-15 | — | Creación del índice a partir del estándar base (118 páginas). Ninguna regla aprobada. |
| 2026-11-15 | 1.1.1 | Pasa a corrección ✏️. |
| 2026-11-15 | 1.1.1 | **Aprobada.** Título cambiado a "Identificadores en inglés"; ahora cubre todo identificador (tipo, miembro, variable o namespace). |
| 2026-11-15 | 1.1.2, 1.1.3, 2.1.1 | Pasan a corrección ✏️. |
| 2026-11-15 | 1.1.2 | **Aprobada.** Ahora menciona la documentación XML (`///`) y tiene cita. |
| 2026-11-15 | 1.1.3 | **Eliminada.** Sin fuente de C# que la respalde. |
| 2026-11-15 | 2.1.1 | **Aprobada.** Incluye parámetros; prohíbe abreviaturas salvo las ampliamente conocidas y aceptadas. |
| 2026-11-15 | 2.1.2, 2.1.3, 2.1.4 | Pasan a corrección ✏️. |
| 2026-11-15 | 2.1.2 | **Aprobada.** Solo variables de instancia privadas o internas (no `static` ni `const`); con cita. |
| 2026-11-15 | 2.1.3 | **Aprobada.** Letras limitadas a i, j, k; con cita. |
| 2026-11-15 | 2.1.4 | **Aprobada.** Cubre variables, parámetros, campos y propiedades; prohíbe sufijos "List" y "Collection"; con cita. |
| 2026-11-15 | 2.1.5, 2.1.6, 2.1.7 | **Aprobadas.** Mismo texto con cita agregada; ejemplos corregidos (tema Gin Rummy y estructura compilable). |
| 2026-11-15 | 2.1.5, 2.1.6 | Ejemplos cambiados a variables locales dentro de métodos. |
| 2026-11-15 | 2.1.8 | **Aprobada.** Mismo texto con cita; ejemplos corregidos. |
| 2026-11-15 | 6.5.2 | Marcada ⚠️: la declaración `using` simplificada requiere C# 8.0 y el proyecto usa C# 7.3. |
| 2026-11-15 | 2.1.9 | **Eliminada.** Imposible de violar en C# 7.3 con las reglas de nombrado aprobadas. |
| 2026-11-15 | 2.1.10 | **Aprobada.** Fija `ex` como único nombre de la excepción en `catch`; con cita. |
| 2026-11-15 | 2.1.11 | **Aprobada e invertida.** Título cambiado a "Prefijo estático `s_`": ahora exige `s_` en campos `static` privados o internos, siguiendo a Microsoft. |
| 2026-11-16 | 2.2.1 | **Aprobada.** Mismo texto con cita; ejemplos con tema Gin Rummy. |
| 2026-11-16 | 2.2.6 | **Aprobada (nueva).** Separada de la regla 2.2.4 original. Pendiente de confirmar: agregar el caso `protected set` para clases derivadas. |
| 2026-11-16 | 9.1.3 | **Aprobada.** Cita reemplazada por StyleCop (SA1505 y SA1508); ejemplos corregidos. |
| 2026-11-16 | 9.1.2 | **Aprobada.** "exige" cambiado por "prefiere" y cita con fecha (IDE0011); ejemplos corregidos. |
| 2026-11-16 | 9.1.1 | **Aprobada.** Excepciones explícitas: accesores (9.1.4), inicializadores (9.1.5) y llaves dentro de texto. |
| 2026-11-16 | 9.1.4 | **Aprobada (nueva).** Accesores de una instrucción en una línea; de dos o más, en varias líneas. |
| 2026-11-16 | 9.1.5 | Nueva, en corrección ✏️. |
| 2026-11-16 | 9.1.7 | **Aprobada (nueva).** Un miembro en una línea; dos o más, cada llave y miembro en su propia línea. |
| 2026-11-16 | 9.1.6, 9.1.8 | Nuevas, en corrección ✏️ (colecciones y arreglos separados). |
| 2026-11-16 | 9.1.6 | **Aprobada (nueva).** Valores simples en una línea; objetos creados con `new`, uno por línea. |
| 2026-11-16 | 9.1.8 | **Aprobada (nueva).** Una línea; si supera el límite de columna (4.1.2), cada llave y elemento en su propia línea. |
| 2026-11-16 | 9.1.6 | Descripción actualizada: agrega el caso en que la línea supera el límite de columna (4.1.2). |
| 2026-11-16 | 9.1.5 | **Aprobada (nueva).** Un miembro en una línea; dos o más, cada llave y miembro en su propia línea. |
| 2026-11-16 | 9.1.1 | Texto ajustado: las excepciones de inicializadores remiten a las reglas 9.1.5 a 9.1.8. |
| 2026-11-16 | 9.2.1 | **Aprobada.** Define comparación (lista cerrada de operadores) y cita con fecha; constantes en lugar de números mágicos. |
| 2026-11-16 | 9.2.2 | **Aprobada.** Agrega el motivo y la cita (IDE0100); ejemplos sin cambios. |
| 2026-11-16 | 9.2.3 | **Eliminada.** Decisión del equipo. |
| 2026-11-16 | 9.3.1, 9.3.3, 9.3.5 | **Aprobadas.** Citas sin fecha reemplazadas por fuentes verificadas; 9.3.3 renombra la clase del ejemplo (sufijo Manager). |
| 2026-11-16 | 9.3.4 | **Eliminada.** Decisión del equipo. |
| 2026-11-16 | 9.3.2 | En corrección ✏️: su texto atribuye a Microsoft afirmaciones que la fuente no hace. |
| 2026-11-16 | 9.3.2 | **Aprobada.** Motivo ajustado a lo que dice la fuente; cita verificada. |
| 2026-11-16 | 9.4.1, 9.4.2, 9.4.4, 9.4.5 | **Aprobadas.** Citas verificadas; ejemplos corregidos (compilación, números mágicos, default). |
| 2026-11-16 | 9.4.3 | En corrección ✏️. |
| 2026-11-16 | 9.4.3 | **Aprobada.** Define qué va dentro del default (acción para los valores sin case o solo `break;`); cita verificada. Subsección 9.4 cerrada. |
| 2026-11-17 | 9.5.1 | **Aprobada.** Define "ejecutar acciones" como descartar el resultado con `_ =`; cita verificada; ejemplos compilables con tema Gin Rummy. |
| 2026-11-17 | 9.5.2 | **Aprobada.** Agrega el motivo y qué hacer con más de dos valores (cada ternario en su propia variable); cita de DeepSource (C#). |
| 2026-11-17 | 9.5.3, 9.5.4 | En corrección ✏️: se investiga en Microsoft la forma explícita `? true : false` y el ternario en varias líneas. |
| 2026-11-17 | 9.5.4 | **Aprobada.** Invertida: el ternario que no cabe en 140 caracteres se parte en tres líneas, con `?` y `:` al inicio y 4 espacios más de sangría; cita IDE2005. |
| 2026-11-17 | 9.5.3 | **Aprobada e invertida.** Título cambiado a "Ramas booleanas explícitas": exige escribir las ramas `true` y `false` del ternario y prohíbe dejar solo la condición; cita IDE0075. Subsección 9.5 cerrada; sección 9 completa. |
