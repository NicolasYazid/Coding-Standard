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
| 2 | [Reglas de nombrado](#2-reglas-de-nombrado) | 32 | 37 |
| 4 | [Estilo de código](#4-estilo-de-código) | 14 | 16 |
| 5 | [Prácticas de programación](#5-prácticas-de-programación) | 5 | 5 |
| 6 | [Manejo de errores y excepciones](#6-manejo-de-errores-y-excepciones) | 8 | 8 |
| 7 | [Manejo de logs](#7-manejo-de-logs) | 0 | 12 |
| 8 | [Comentarios](#8-comentarios) | 9 | 9 |
| 9 | [Estructuras de control](#9-estructuras-de-control) | 23 | 23 |
| 10 | [Conexión con la base de datos](#10-conexión-con-la-base-de-datos--almacenamiento-local) | 0 | 0 |
| 11 | [Pruebas unitarias](#11-pruebas-unitarias) | 3 | 3 |
| 13 | [DTOs y modelos de dominio](#13-dtos-y-modelos-de-dominio) | 1 | 1 |
| 14 | [Manejo de documentos / Assets](#14-manejo-de-documentos--assets) | 0 | 0 |
| 15 | [Gestión gráfica](#15-gestión-gráfica) | 0 | 0 |
| | **Total** | **96** | **116** |

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
- [x] **2.2.2** Propiedades en lugar de métodos de acceso
- [x] **2.2.3** Propiedades simples
- [x] **2.2.6** Set restringido 🆕

### 2.5 Constantes
- [x] **2.5.1** Nomenclatura (PascalCase)
- [x] **2.5.2** Uso de `const`
- [x] **2.5.3** Uso de `static readonly`

### 2.6 Métodos
- [x] **2.6.1** Nomenclatura (PascalCase)
- [x] **2.6.2** Verbos o frases verbales
- [x] **2.6.3** Límite de parámetros

### 2.7 Manejadores de eventos (prefijos On, Handle, Toggle)
- [x] **2.7.1** Prefijo `On` (método que lanza un evento)
- [x] **2.7.2** Prefijo `Handle` (método que reacciona a un evento)
- [x] **2.7.3** Prefijo `Toggle` (alternancia de estados booleanos)
- [x] **2.7.4** Descriptores directos (sin prefijo)

### 2.8 Métodos de prueba unitaria
> Texto introductorio (sin obligación): La realización de pruebas unitarias priorizará la verificación de la capa lógica del videojuego, abarcando aspectos como el cálculo de puntuaciones y las reglas de la partida. De este modo, se evita forzar una cobertura del 100% que pueda volver frágil el código, ya que tratar de cubrir el 100% es imposible.

- [x] **2.8.1** Estructura de nomenclatura (prefijo `Test`)
- [x] **2.8.2** Nombres descriptivos vs. genéricos
- [x] **2.8.4** Atributos de prueba

### 2.9 Clases
- [x] **2.9.1** Nomenclatura base (PascalCase)
- [x] **2.9.2** Nombre de clase sin prefijo
- [x] **2.9.3** Acrónimos en el nombre de una clase

### 2.11 Interfaces
- [x] **2.11.1** Prefijo obligatorio y convención base (PascalCase)
- [x] **2.11.2** Nombre de interfaz sin la palabra "Interface"

### 2.12 Sufijos por responsabilidad
- [ ] **2.12.2** Servicios lógicos (`Service`)
- [ ] **2.12.3** Procesamiento de eventos (`Handler`)
- [ ] **2.12.4** Validación de estados (`Validator`)
- [ ] **2.12.5** Lógica auxiliar (`Common`)
- [ ] **2.12.6** Excepciones personalizadas (sufijo `Exception`)

---

## 4. Estilo de código

### 4.1 Formato y estructura general
- [x] **4.1.1** Indentación base (4 espacios)
- [x] **4.1.2** Límite de columna (140 caracteres) y ruptura de línea
- [x] **4.1.3** Indentación en líneas continuadas

### 4.2 Uso de espacios en blanco
- [x] **4.2.1** Separación vertical entre métodos y constructores
- [x] **4.2.2** Agrupación vertical de propiedades simples (auto-propiedades)
- [x] **4.2.3** Separación vertical de propiedades complejas
- [x] **4.2.4** Agrupación lógica y prohibición de múltiples líneas en blanco
- [x] **4.2.5** Espacios en operadores binarios
- [x] **4.2.6** Espacios en estructuras de control
- [x] **4.2.7** Ausencia de espacios en métodos
- [x] **4.2.8** Espaciado en delimitadores de listas (comas)

### 4.3 Organización del código en el archivo
- [x] **4.3.1** Orden estructural del archivo
- [x] **4.3.2** Agrupación y orden de directivas `using`
- [x] **4.3.3** Declaración única por archivo

### 4.4 Orden de miembros en la clase
- [ ] **4.4.1** Jerarquía estructural de miembros
- [ ] **4.4.2** Orden de métodos por visibilidad

---

## 5. Prácticas de programación

### 5.1 Un único return
- [x] **5.1.1** Punto único de retorno en métodos con valor de retorno

### 5.2 Prevención de números mágicos
- [x] **5.2.1** Prevención de números mágicos

### 5.3 Número máximo de operadores en expresiones
- [x] **5.3.1** Número máximo de operaciones en expresiones

### 5.4 Complejidad ciclomática
- [x] **5.4.1** Complejidad ciclomática

### 5.5 Manejo de nulos
- [x] **5.5.1** Prohibición de retorno nulo en colecciones

---

## 6. Manejo de errores y excepciones

### 6.1 Uso de bloques try-catch y manejo de excepciones específicas
- [x] **6.1.1** Captura de excepciones específicas
- [x] **6.1.2** Contenido de los bloques `catch`

### 6.2 Orden jerárquico en los bloques catch
- [x] **6.2.1** Orden de los bloques `catch` por especificidad

### 6.3 Propagación y empaquetamiento de excepciones
- [x] **6.3.1** Propagación directa (Preservación del Stack Trace)
- [x] **6.3.2** Empaquetamiento de excepciones (`InnerException`)

### 6.4 Jerarquía de excepciones personalizadas del videojuego
- [x] **6.4.1** Creación de la excepción base del dominio
- [x] **6.4.2** Priorización de excepciones del sistema
- [x] **6.4.3** Herencia de excepciones específicas (jerarquía de un solo nivel)

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
- [x] **8.1.1** Comentarios de una línea (`//`): formato y ubicación
- [x] **8.1.2** Comentarios en bloque (`/* */`)
- [x] **8.1.3** Justificación lógica del comentario (el "por qué", no el "qué")
- [x] **8.1.6** Documentación XML (`///`): etiquetas obligatorias
- [x] **8.1.7** Documentación XML: formato válido
- [x] **8.1.8** Uso y formato del comentario especial `TODO`
- [x] **8.1.9** Uso y formato del comentario especial `FIXME`
- [x] **8.1.10** Ciclo de vida de `TODO` y `FIXME`
- [x] **8.1.11** Prohibición de código comentado

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
- [x] **11.1.2** Nomenclatura de la clase de prueba

### 11.2 Estructura de un test
- [x] **11.2.1** Estructura de las pruebas (Arrange, Act, Assert)
- [x] **11.2.2** Límite de aserciones por método

---

## 13. DTOs y modelos de dominio

### 13.1 Estructura de un DTO
- [x] **13.1.1** Contrato de datos explícito 🆕

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

## 🗑️ Reglas eliminadas

- ~~**1.1.3** Idioma de los mensajes de error (logs y excepciones)~~ — sin fuente de C# que la respalde; Microsoft recomienda traducir los mensajes de excepción en aplicaciones localizadas.
- ~~**9.3.4** Elección del `do-while`~~ — solo describía para qué sirve un `do-while`; no prevenía ningún defecto.
- ~~**9.2.3** Cláusula de guarda~~ — eliminada por decisión del equipo; su redacción castigaba métodos `void` con un solo `if` y dependía de la regla 5.1.1.
- ~~**2.1.9** Prevención de sombreado de datos~~ — en C# 7.3 el compilador ya impide el sombreado entre variables locales (CS0136), y las reglas 2.1.1, 2.1.2 y 2.1.11 impiden que una variable local se llame igual que un campo.
- ~~**2.7.5** Límite de parámetros en eventos~~ — repetía el límite de tres parámetros que la regla 2.6.3 ya fija para todo método, incluidos los manejadores de eventos.
- ~~**2.8.3** Cobertura de lógica central y flujos existentes~~ — no regulaba nombres y no se podía medir; la parte de nombres ya la cubren las reglas 2.8.1 y 2.8.2. La idea pasó como texto introductorio de la subsección 2.8.
- ~~**Sección 3** Organización del proyecto (3.1 a 3.6, sin reglas)~~ — trataba la arquitectura del proyecto y el control de versiones, no la codificación; esos temas cambian y se documentan en otros artefactos. El número 3 no se reutiliza.
- ~~**2.10** Clases controladoras (2.10.1 Sufijo obligatorio y nomenclatura completa; 2.10.2 Eliminación de prefijos tecnológicos)~~ — el proyecto no usa controladores (patrón MVC), así que la subsección no aplica.
- ~~**Sección 16** Dependencias externas y de seguridad (16.1 Vulnerabilidades conocidas, sin reglas)~~ — el equipo decidió no abarcar este tema en el estándar de codificación. El número 16 no se reutiliza.
- ~~**Sección 12** Validación de entrada y seguridad (12.1 Centralización de validaciones, 12.2 Almacenamiento de contraseñas, 12.3 Gestión de sesión; sin reglas)~~ — el equipo decidió no abarcar este tema en el estándar de codificación. El número 12 no se reutiliza.
- ~~**2.9.4** Acrónimo arquitectónico (`Dto`)~~ — la regla 2.9.3 ya cubre cualquier acrónimo de tres o más letras en el nombre de una clase, incluido `Dto`; además, el proyecto no usa DTO.
- ~~**2.12.1** Acceso a datos (`Dao`)~~ — el proyecto no usa DAO (decisión de la versión 9: repositorios y unidad de trabajo); la regla obligaba a un patrón que no se usa.
- ~~**8.1.4** Prohibición de comentarios redundantes~~ — la regla 8.1.3 ya pide que el comentario no repita lo que dice la línea de código que comenta, y el "Sin estándar" de la 8.1.4 ya violaba la 8.1.3.
- ~~**8.1.5** Documentación XML (`///`): cuándo se usa~~ — dependía de qué proyectos y clases existen en el sistema ("capa de servicios", "mecánicas de bajo nivel"), que cambian; Microsoft solo recomienda documentar los miembros públicos y advierte que documentar los privados expone el funcionamiento interno, no lo prohíbe. La documentación XML queda opcional y las reglas 8.1.6 y 8.1.7 aplican a los bloques que se escriban.
- ~~**8.1.12** Balance y densidad de comentarios~~ — repetía lo que ya piden la 8.1.3 (el comentario `//` solo dice lo que el código no expresa) y la 2.8.2 (nombres descriptivos), y no definía un umbral para "balance estricto" ni para "sobre-comentar", por lo que no se podía comprobar.
- ~~**2.2.4** Declaración correcta de propiedades~~ — repetía lo que ya piden la 2.2.1 (PascalCase en propiedades), la 2.2.2 (los métodos que solo devuelven o asignan un campo son propiedades) y la 2.2.6 (`set` restringido); lo demás, prohibir cualquier método `Get...` o `Set...` que obtenga o modifique el estado, era demasiado amplio.
- ~~**2.2.5** Modificación de valor en propiedades~~ — su único contenido comprobable, que una propiedad no se lea ni se asigne a sí misma, es un error que hace caer el juego en cuanto se ejecuta esa línea (`StackOverflowException`), así que el propio programa lo muestra; el resto ya lo cubren la 2.2.2 y la 2.2.3.
- ~~**2.3** Componentes de interfaz gráfica y **2.4** Identificadores de interfaz (sin reglas)~~ — el equipo decidió quitar estas dos subsecciones porque, por ahora, no tienen reglas ni propósito en el estándar. Los números 2.3 y 2.4 no se reutilizan.
- ~~**6.2.2** Jerarquía con excepciones personalizadas~~ — era la 6.2.1 aplicada a las excepciones propias del juego, sin ningún criterio nuevo que se pudiera revisar; ponerlas en el orden contrario tampoco compila (error CS0160). Usaba `GameSystemException` como excepción base, pero el juego y la 6.4.1 usan `GameCoreException`. Su contenido quedó dentro de la 6.2.1, que ahora dice "incluidas las excepciones propias del juego".
- ~~**6.1.3** Priorización de excepciones del sistema~~ — repetía la 6.4.2 con casi las mismas palabras (solo cambiaban los ejemplos y el año de la cita); la regla trata de qué excepción lanzar o crear, no de cómo capturar, así que encaja en la subsección 6.4, donde se evalúa.
- ~~**6.5.2** Preferencia por la declaración simplificada (C# 8.0+)~~ — la declaración `using` sin llaves se agregó en C# 8.0 (Microsoft, 2026) y el proyecto usa C# 7.3, así que el ejemplo "Con estándar" no compila.
- ~~**6.5.3** Uso del bloque tradicional para liberación anticipada~~ — con la 6.5.2 eliminada, la forma con llaves es la única que existe en C# 7.3, así que cualquier `using` ya la cumple; cerrar el recurso antes de que termine el método no se puede medir, y la fuente solo describe cuándo se libera el objeto, no pide hacerlo.
- ~~**6.5.1** Prohibición de liberación manual (`Dispose`) (subsección 6.5 completa)~~ — el equipo decidió eliminarla porque no se entendía. Además, el texto base obligaba a que todo objeto `IDisposable` usara `using`, y eso no se puede cumplir con los objetos guardados en campos de una clase (como `_context` y `_transaction` de `EntityFrameworkUnitOfWork`) ni con los clientes de WCF, que Microsoft indica cerrar con `Close()` y `Abort()` (Microsoft, 2021).
- ~~**5.6.1** Tipo de los parámetros de una lambda~~ — el equipo decidió eliminarla porque no hay tiempo para definirla.
- ~~**5.6.2** Paréntesis de los parámetros de una lambda~~ — regla nueva creada el 2026-11-17 al separar la plantilla vacía 5.6.1; nunca se redactó.
- ~~**5.6.3** Cuerpo de una lambda (subsección 5.6 completa)~~ — regla nueva creada el 2026-11-17 al separar la plantilla vacía 5.6.1; nunca se redactó.
- ~~**13.1.2** Una clase de transferencia solo contiene datos~~ — regla nueva propuesta el 2026-11-22 que el equipo no aprobó. Era más estricta que la fuente, que permite validación básica en un DTO, y no previene un defecto que hoy exista en el juego.
- ~~**13.1.3** Sin herencia entre clases de transferencia~~ — regla nueva propuesta el 2026-11-22 que el equipo no aprobó. Microsoft no prohíbe la herencia en los contratos de datos, solo pide declarar `KnownType` cuando se usa, y el juego no usa herencia en ninguna de sus 19 clases.
- ~~**11.3.2** Límite de parámetros en constructores auxiliares e inicialización por defecto (subsección 11.3 completa)~~ — el límite de tres parámetros ya lo pide la regla 2.6.3 para todos los métodos; el resto dependía de los conceptos "método builder" y "objeto complejo" de la 11.3.1, eliminada, y de "valores más críticos", que no se puede medir.
- ~~**11.3.1** Nomenclatura y visibilidad (métodos *builder* en pruebas)~~ — el prefijo `Builder` no tiene respaldo en ninguna fuente (en las fuentes, "Builder" es una clase y va al final del nombre) y choca con la regla 2.6.2 (nombres de métodos con verbo); "objeto complejo" no tiene una medida. Lo que sí tiene respaldo, extraer la construcción de objetos a un método auxiliar privado, es una recomendación que no se puede volver regla sin inventar un límite arbitrario.
- ~~**11.2.3** Configuración inicial compartida~~ — no se podía medir ("múltiples métodos" y "los mismos objetos" no tienen un criterio claro), obligaba a usar `[SetUp]` y se acoplaba a NUnit; Microsoft recomienda crear los objetos en cada prueba o en métodos auxiliares y deja la preparación compartida para cuando todas las pruebas de la clase necesitan lo mismo.
- ~~**11.1.1** Ubicación lógica (namespaces)~~ — se acoplaba a la estructura del código de producción (`Entities`, `UseCases`, `Ports`) y a la organización de los proyectos de pruebas; lo único comprobable, que el namespace lleve `.Tests`, ya lo cumple el nombre de los proyectos de pruebas.

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
| 2026-11-17 | 2.5.1 | **Aprobada.** Aplica a campos y constantes locales de cualquier acceso; UPPER_SNAKE_CASE prohibido; cita verificada. |
| 2026-11-17 | 2.5.2 | **Aprobada.** Título cambiado a "Uso de `const`": obliga a declarar `const` todo campo con valor escrito en el código que nunca se reasigna; citas Field design y CA1802. |
| 2026-11-17 | 2.5.3 | **Aprobada.** Título cambiado a "Uso de `static readonly`": un campo `static` que nunca se reasigna y no puede ser `const` lleva `readonly`. Subsección 2.5 cerrada. |
| 2026-11-17 | 2.6.1 | **Aprobada.** Mismo texto; "alineándose con las convenciones de Microsoft" pasa a ser la cita; ejemplos dentro de una clase. |
| 2026-11-17 | 2.6.2 | **Aprobada.** El nombre empieza con el verbo; "sustantivos estáticos" pasa a "sustantivos"; constructores y `Main` quedan fuera; cita verificada. |
| 2026-11-17 | 2.6.3 | En corrección ✏️: ejemplos más simples. |
| 2026-11-17 | 2.6.3 | **Aprobada.** Aplica a métodos y constructores; si se necesitan más datos se agrupan en una clase; quedan fuera las interfaces de .NET; cita SonarSource (S107). Subsección 2.6 cerrada. |
| 2026-11-17 | 2.6.3 | Texto ajustado a petición del equipo: "se agrupan" pasa a "se pueden agrupar" (deja abierta otra solución, como dividir el método). |
| 2026-11-17 | 2.7.1 | **Aprobada.** Cambia de significado para seguir a Microsoft: `On` + nombre del evento es el método que solo avisa que ocurrió el evento; única excepción a la 2.6.2. |
| 2026-11-17 | 2.7.2 | **Aprobada.** Cambia de significado: el método que reacciona a un evento empieza con `Handle`. |
| 2026-11-17 | 2.7.3 | **Aprobada.** `Toggle` solo en métodos que no hacen nada más que invertir un `bool`, y todo método así lo lleva; cita IToggleProvider.Toggle. |
| 2026-11-17 | 2.7.2 | Texto ampliado: `Handle` no es exclusivo de los métodos que reaccionan a un evento; ejemplo con `HandleCardSelection`. |
| 2026-11-17 | 2.7.4 | **Aprobada.** Método que no es `On`, `Handle` (de evento) ni `Toggle` empieza con un verbo de acción; ese verbo también puede ser `Handle` (2.7.2). |
| 2026-11-17 | 2.7.5 | **Eliminada.** Duplicaba la regla 2.6.3. |
| 2026-11-17 | 2.8.1 | **Aprobada.** Descripción del equipo con cita; ejemplos dentro de clase y del dominio Gin Rummy. |
| 2026-11-17 | 2.8.2 | **Aprobada.** Descripción del equipo con cita; el ejemplo "Sin estándar" cumple la 2.8.1 pero usa un escenario numerado y un resultado genérico. |
| 2026-11-17 | 2.8.4 | **Aprobada.** Se quita la exención de prefijos de eventos; el ejemplo "Sin estándar" ahora omite `[Test]`; cita de NUnit. |
| 2026-11-17 | 2.8.3 | **Eliminada.** No medible y fuera del tema de nombrado; su idea pasa a un texto introductorio de la 2.8 escrito por el equipo. Subsección 2.8 completa. |
| 2026-11-17 | Sección 3 | **Eliminada completa** (3.1 a 3.6, sin reglas). Arquitectura y control de versiones se documentan fuera del estándar de codificación. |
| 2026-11-17 | 2.8.4 | Título cambiado a "Atributos de prueba". |
| 2026-11-17 | 2.10.1, 2.10.2 | **Eliminada la subsección 2.10 completa.** El proyecto no usa controladores (patrón MVC). |
| 2026-11-17 | 5.1.1 | **Aprobada.** Se agrega que es una regla del equipo (sin cita: no hay fuente oficial de C# que la exija). Ejemplos sin cambios. |
| 2026-11-17 | 5.2.1 | **Aprobada sin cambios.** El equipo conserva su texto (solo números con significado dentro del contexto del juego). |
| 2026-11-17 | 5.2.1 | Se retira la cita "(Microsoft, s.f.)"; queda sin cita. |
| 2026-11-17 | 5.3.1 | **Aprobada.** Descripción del equipo sin cambios; el ejemplo "Con estándar" agrega `? true : false` para cumplir la 9.5.3. |
| 2026-11-17 | 5.4.1 | **Aprobada.** Redacción del equipo (10 como límite; 12 excepcional y justificado) con cita de Microsoft; el método de los ejemplos pasa de `Validate` a `ValidateKnock`. |
| 2026-11-17 | 5.5.1 | **Aprobada.** Descripción y ejemplos sin cambios; se agrega la cita de las guías de colecciones de Microsoft. |
| 2026-11-17 | 2.1.4 | Se permite el singular en sustantivos colectivos; ejemplos con `_meld` (permitido) y `_meldCard` (prohibido). |
| 2026-11-17 | 5.6.1, 5.6.2, 5.6.3 | La plantilla vacía 5.6.1 se separa en tres reglas sobre cómo escribir lambdas (tipo de los parámetros, paréntesis y cuerpo). Quedan como **Regla pendiente de revisión**. |
| 2026-11-21 | Sección 16 | **Eliminada completa** (16.1, sin reglas). El tema ya no se abarca en el estándar. |
| 2026-11-21 | Sección 12 | **Eliminada completa** (12.1 a 12.3, sin reglas). El tema ya no se abarca en el estándar. |
| 2026-11-21 | 2.9.1 | **Aprobada.** Descripción del equipo con cita; ejemplos de Gin Rummy que muestran PascalCase y sustantivo contra verbo. |
| 2026-11-21 | 2.9.2 | **Aprobada.** Título cambiado a "Nombre de clase sin prefijo"; redactada como regla, sin la parte de guiones bajos (ya la cubre la 2.9.1); con cita; ejemplos `PlayerHand` y `CPlayerHand`. |
| 2026-11-22 | 2.9.3 | **Aprobada.** Título cambiado a "Acrónimos en el nombre de una clase"; ya no depende de `Dao` (el proyecto no usa DAO); cubre todo acrónimo de tres o más letras; ejemplos `SmtpSettings` y `SMTPSettings`. |
| 2026-11-22 | 2.9.4 | **Eliminada.** Repetía la 2.9.3. Subsección 2.9 completa. |
| 2026-11-22 | 2.11.1 | **Aprobada.** Solo regula el prefijo `I` y el PascalCase (se quitó la oración sobre adjetivo o sustantivo); con cita; ejemplo `IDrawable`. |
| 2026-11-22 | 2.9.3 | Ejemplo cambiado de `SmtpSettings`/`SMTPSettings` (nombre tomado del repositorio) a `TcpConnection`/`TCPConnection`; en la descripción, `Smtp`/`SMTP` pasa a `Tcp`/`TCP`. |
| 2026-11-22 | 2.11.2 | **Aprobada.** Título cambiado a "Nombre de interfaz sin la palabra \"Interface\""; redactada como regla; con cita; ejemplos `IDrawable` y `IDrawableInterface`. Subsección 2.11 completa. |
| 2026-11-22 | 2.12.1 | **Eliminada.** El proyecto no usa DAO. |
| 2026-11-22 | 8.1.1 | **Aprobada.** Título sin raya larga (`:` en su lugar); descripción sin la oración final sobre consistencia; cita (Microsoft, 2025); ejemplos con la constante `KnockBonusPoints` en vez del número `25`. |
| 2026-11-22 | 8.1.1 | Se agregó la oración sobre comentarios de varias líneas (mayúscula en la primera línea y punto en la última) y un comentario de dos líneas en los ejemplos. |
| 2026-11-22 | 8.1.2 | **Aprobada.** Redactada con "deben" y sin la explicación sobre Microsoft; "extensas" pasa a "ocupan varias líneas"; cita (Microsoft, 2025); ejemplos con `_timeoutTimer++` en vez de `+= 1`. |
| 2026-11-22 | 8.1.3 | **Aprobada.** Aplica a los comentarios `//` que explican código; redactada como regla y sin la oración cortada; cita Microsoft (2025) en lugar de Martin (2008); ejemplos con `PlayerTurn` y un `if` en vez de guardar un `&&` en un `bool`. |
| 2026-11-22 | 8.1.4 | **Eliminada.** Repetía la 8.1.3. |
| 2026-11-22 | 8.1.5 | **Eliminada.** Se acoplaba a la estructura del sistema y obligaba a documentar cientos de miembros. |
| 2026-11-22 | 8.1.6 | **Aprobada.** `<exception>` por cada tipo de excepción que el método lanza con `throw` en su propio cuerpo (antes "de forma documentada"); cita Microsoft (2026); ejemplos con `CardDealer`, un método con `<returns>` y constantes en vez de números sueltos. |
| 2026-11-22 | 8.1.7 | **Aprobada.** Cita Microsoft (2026) en lugar de "s.f."; se quitó la mención del código CS1570 y de la advertencia del compilador; la idea de la etiqueta abierta sin cierre pasó a la primera oración; ejemplos con `GameTable` en vez de `DeckService`. |
| 2026-11-22 | 8.1.8 | **Aprobada.** Renombrada a "Uso y formato del comentario especial `TODO`"; se quitó la oración que afirmaba que el formato es lo que activa la Task List de Visual Studio (la etiqueta no distingue mayúsculas); el ejemplo "Sin estándar" ahora solo rompe esta regla; cita Microsoft (2025). |
| 2026-11-22 | 8.1.9 | **Aprobada.** Renombrada a "Uso y formato del comentario especial `FIXME`"; se quitó la oración sobre agregar la etiqueta a la configuración de Visual Studio (no se puede auditar en el código) y la cita de Microsoft, que ya no respaldaba nada; el ejemplo "Sin estándar" ahora solo rompe esta regla. |
| 2026-11-22 | 8.1.10 | **Aprobada.** Se quitó la cita de Bass et al. (2013), que no respalda la regla; ahora es decisión del equipo; el criterio es que el código entregado no contenga `TODO` ni `FIXME` (antes "antes de cualquier entrega formal"); el ejemplo "Sin estándar" ya no depende del flujo de trabajo con Git ("before merge"). |
| 2026-11-22 | 8.1.11 | **Aprobada.** Renombrada a "Prohibición de código comentado" ("código muerto" en C# suele significar código inalcanzable); se quitó "Git como único mecanismo oficial" y se dejó el control de versiones en general; se agregó que los ejemplos de código en la documentación `///` no cuentan; el ejemplo "Sin estándar" ya no tiene número suelto ni llaves en una sola línea. |
| 2026-11-22 | 8.1.12 | **Eliminada.** Repetía las reglas 8.1.3 y 2.8.2 y no se podía medir. |
| 2026-11-22 | 2.2.2 | **Aprobada.** El README la tenía como plantilla vacía, pero el PDF de la última versión trae el texto; título "Propiedades en lugar de métodos de acceso"; redactada como "un método cuya única instrucción sea devolver o asignar un campo debe escribirse como propiedad"; se quitó "queda prohibido" y la oración explicativa; se agregó una excepción general para los métodos que el lenguaje o un framework exigen (interfaz o clase base, propiedades adjuntas de WPF); cita Microsoft (2026) y Microsoft (2025). |
| 2026-11-22 | 2.2.3 | Título actualizado de "Plantilla vacía" a "Propiedades simples", porque el PDF de la última versión trae el texto. Sigue pendiente de evaluar. |
| 2026-11-22 | 2.2.3 | **Aprobada.** Redactada por responsabilidades: el `get` solo devuelve el dato y las acciones (archivos, base de datos, red, `throw`) van en un método, sin lista cerrada; se quitó la oración de la categoría de "entrada y salida" y la mención de indexadores; cita Microsoft (2026) y Microsoft (2023); el ejemplo "Sin estándar" con el `get` en una línea (9.1.4). |
| 2026-11-22 | 2.2.4 | **Eliminada.** Repetía las reglas 2.2.1, 2.2.2 y 2.2.6; la parte que no cubrían era demasiado amplia. |
| 2026-11-22 | 2.2.5 | **Eliminada.** Solo prohibía que una propiedad se leyera o asignara a sí misma, un error que el juego muestra de inmediato al ejecutarse; el resto lo cubren las reglas 2.2.2 y 2.2.3. |
| 2026-11-22 | 2.3, 2.4 | **Eliminadas las subsecciones 2.3 y 2.4 completas** (sin reglas). Si se necesitan de nuevo, se recuperan del historial de versiones. |
| 2026-11-22 | 11.1.1 | **Eliminada.** Se acoplaba a decisiones de diseño sobre la estructura del código y de los proyectos de pruebas. |
| 2026-11-22 | 11.1.2 | **Aprobada.** Redactada como "el nombre de una clase que contiene pruebas unitarias debe ser el nombre de la clase que prueba seguido de `Tests`"; se quitó la oración del PascalCase, que repetía la 2.9.1 y citaba mal la 2.8.1 (esa regla trata los métodos de prueba); el ejemplo pasa de `CollisionHandler` (sufijo `Handler`, regla 2.12.3 pendiente) a `MeldFinder`; sin cita, decisión del equipo. |
| 2026-11-22 | 11.2.1 | **Aprobada.** Renombrada a "Estructura de las pruebas (Arrange, Act, Assert)"; se agregó "en las fases que tenga" (12 pruebas del juego no tienen las tres fases: 10 sin preparación y 2 que actúan y afirman en la misma línea); se quitó "queda estrictamente prohibido"; los ejemplos usan una prueba del juego y constantes en lugar de `50` y `0` (5.2.1), y el "Sin estándar" lleva los comentarios `// Arrange`, `// Act` y `// Assert`; cita Microsoft (2026). Pendiente en el código: quitar la línea en blanco antes de `round.DrawFromStock(...)` en `GameRoundTests`. |
| 2026-11-22 | 11.2.2 | **Aprobada.** Renombrada a "Límite de aserciones por método"; el límite de una aserción es impuesto por el profesor y no cambia; se aclaró que cuenta cualquier aserción de la biblioteca de pruebas (`Assert` o cualquier otra clase de aserciones), porque `CollectionAssert` podía no contarse; los ejemplos usan constantes en lugar de `20`, `15` y `35` (5.2.1); sin cita, decisión del profesor. Pendiente en el código: `Test_SplitIntoNeighbors_CardApart_StartsNewStretch` en `HandOrderTests` tiene tres aserciones y debe dividirse en tres pruebas. |
| 2026-11-22 | 11.2.3 | **Eliminada.** No se podía medir, obligaba a usar `[SetUp]` y se acoplaba a NUnit; en 7 clases de pruebas del juego se repetía la creación de los mismos objetos. |
| 2026-11-22 | 11.3.1 | **Eliminada.** El prefijo `Builder` no tiene respaldo y choca con la 2.6.2; "objeto complejo" no se podía medir; la parte con respaldo es una recomendación, no una regla. |
| 2026-11-22 | 11.3.2 | **Eliminada.** Repetía el límite de la 2.6.3 y dependía de la 11.3.1, eliminada. Subsección 11.3 completa. |
| 2026-11-22 | 6.1.1 | **Aprobada.** Se quitó "errores rutinarios" (no está en Microsoft y dejaba pensar que `Exception` valía para los demás errores); "es obligatorio" y "queda estrictamente prohibido" pasan a "se debe" y "no se debe"; "problemas críticos del sistema" pasa a "problemas en tiempo de ejecución y dificultar la depuración", como dice CA1031; se agregó el único caso permitido, que el bloque `catch` termine con `throw;`; "la más específica posible" se conserva porque lo pide el profesor; los ejemplos pierden la variable `ex`, que no se usaba; cita Microsoft (2026). Pendiente: confirmar con el profesor si capturar `FaultException` y `CommunicationException` (tienen tipos derivados más específicos) cumple "la más específica posible". |
| 2026-11-22 | 6.1.2 | **Aprobada.** Renombrada a "Contenido de los bloques `catch`" (el título decía "Prohibición"); redactada como "un bloque `catch` no debe estar vacío; si el error se ignora a propósito, debe contener un comentario que explique la razón"; se quitaron "queda estrictamente prohibido" y "obligatoriamente", y "error esperado, benigno y la arquitectura dicta que debe ser ignorado" por no poder medirse; se quitó la cita Microsoft (2024) porque no se encontró una página de Microsoft sobre C# que la respalde, queda como decisión del equipo; los ejemplos pierden la variable `ex`, que no se usaba. Pendiente en el código: agregar un comentario en el `catch` vacío de `PlayerConnection.cs` (`InvalidOperationException`) y en el de `PlayRoundUseCase.cs` (`DataException`); los otros 5 `catch` vacíos del juego ya lo tienen. |
| 2026-11-22 | 6.1.3 | **Eliminada.** Repetía la 6.4.2; se conserva la 6.4.2 por ubicarse en la subsección de excepciones personalizadas. |
| 2026-11-22 | 6.2.1 | **Aprobada.** Se conserva por decisión del equipo aunque el compilador ya la exige (error CS0160: un `catch` general antes de uno específico no compila), así que no se puede violar. Renombrada a "Orden de los bloques `catch` por especificidad"; se quitó "obligatoriamente"; se agregó la cita Microsoft (2025), que el texto base no traía; los ejemplos van dentro de una clase y un método, con tema de partidas guardadas en lugar de niveles y sin la variable `ex`, que no se usaba. El ejemplo "Sin estándar" no compila, a propósito. |
| 2026-11-22 | 6.1.1 | **Ejemplos corregidos.** Ahora van dentro de una clase y un método, con los métodos auxiliares definidos, igual que en la 6.2.1; el texto de la regla no cambió. |
| 2026-11-22 | 6.2.1 | **Descripción modificada.** Se agregó "incluidas las excepciones propias del juego" para que cubra lo que decía la 6.2.2 (eliminada); el título, la cita y los ejemplos no cambian. |
| 2026-11-22 | 6.2.2 | **Eliminada.** Era la 6.2.1 aplicada a las excepciones propias; su contenido quedó dentro de la 6.2.1. |
| 2026-11-22 | 6.3.1 | **Aprobada.** Se simplificó la redacción: "para volver a lanzar una excepción capturada se debe utilizar `throw;`" (se quitó la parte de la "acción de mitigación", que confundía); "obligatoriamente" y "queda estrictamente prohibido" pasan a "se debe" y "no se debe"; se agregó la cita Microsoft (2026), que el texto base no traía; los ejemplos van dentro de una clase y un método, con tema de Gin Rummy, y el "Con estándar" no declara la variable porque no se usa. El juego no tiene ningún `throw ex;` ni `throw;`, así que hoy no la viola ni la usa. |
| 2026-11-22 | 6.3.2 | **Aprobada.** Se pasó de exigir el empaquetamiento solo al lanzar una excepción propia del dominio tras capturar una de bajo nivel, a exigirlo en toda excepción nueva lanzada dentro de un `catch`; "es obligatorio" pasa a "se debe"; se agregó la cita Microsoft (2025), que el texto base no traía. Se agregó por decisión del equipo la excepción para `FaultException`, con la cita Microsoft (2021): los servicios WCF del juego lanzan unos 50 `FaultException` dentro de un `catch` sin pasar la excepción original, ese tipo no recibe una excepción interna y la fuente advierte que las excepciones pueden exponer información interna a los clientes WCF. Los `throw new` dentro de un `catch` del juego (7 `InvalidAccessTokenException`) ya pasan la excepción original. Los ejemplos van dentro de una clase y un método, con tema de partidas guardadas; todos los `catch` usan `FileNotFoundException` por la 6.1.1 y el "Sin estándar" no declara `ex` porque no se usa. |
| 2026-11-22 | 6.4.1 | **Aprobada.** Se quitó "Todas las demás excepciones lógicas del juego deberán derivar de esta" (la 6.4.3 ya lo cubre), "obligatoria" y "su nombre debe reflejar el núcleo del sistema", que no se puede medir; se aclaró que el equipo de desarrollo elige el nombre de la clase y que solo debe terminar en `Exception`; "System.Exception" pasa a `Exception`; se agregó la cita Microsoft (2025), que el texto base no traía. Que la clase base sea única es decisión del equipo. Los ejemplos son los del estándar base. El juego la cumple: solo `GameCoreException` hereda directamente de `Exception`. |
| 2026-11-22 | 6.4.2 | **Aprobada.** Se quitó "obligatoriamente"; "con mayor exactitud" pasa a "que corresponda al error" y "adecuadamente" a "se aplique al error"; la condición "la capa superior necesite atraparla programáticamente para aplicar una lógica de recuperación muy específica" pasa a "el error deba manejarse de forma distinta a cualquier otra excepción existente"; la cita pasa de Microsoft (2024) a Microsoft (2025) y se agrega Cwalina (2006), un blog archivado en Microsoft Learn que respalda la segunda condición. El ejemplo "Sin estándar" define `NullSessionTokenException` para que compile. El juego la cumple: sus 18 excepciones propias tienen al menos un `catch` por su tipo. Esta regla cubre lo que decía la 6.1.3 (eliminada). |
| 2026-11-22 | 6.4.3 | **Aprobada.** "Queda estrictamente prohibido" y "obligatoriamente" pasan a "deben"; se quitaron los argumentos de extensibilidad y *accountability* (Bass et al., 2013; ISO, 2011), que no se verificaron; la cita Microsoft (s.f.) se reemplaza por Microsoft (2006), que respalda evitar jerarquías profundas. Esa fuente no dice que la jerarquía deba ser de exactamente un nivel; eso es decisión del equipo. El ejemplo "Sin estándar" define `MatchLogicException` para que compile. El juego la cumple: sus 18 excepciones propias heredan directamente de `GameCoreException`, sin clases intermedias. |
| 2026-11-22 | 6.5.2 | **Eliminada.** La declaración `using` sin llaves requiere C# 8.0 y el proyecto usa C# 7.3, así que la regla no se puede cumplir. |
| 2026-11-22 | 6.5.3 | **Eliminada.** Con la 6.5.2 eliminada, la forma con llaves es la única en C# 7.3 y "liberación anticipada" no se puede medir. |
| 2026-11-22 | 6.5.1 | **Eliminada.** El equipo decidió eliminarla porque no se entendía; el texto base obligaba a usar `using` en todo objeto `IDisposable`, lo que no se puede cumplir con campos de clase ni con clientes de WCF. Subsección 6.5 completa. |
| 2026-11-22 | 5.6.1 | **Eliminada.** El equipo decidió eliminarla porque no hay tiempo para definirla; el texto base era una plantilla vacía. |
| 2026-11-22 | 5.6.2 | **Eliminada.** El equipo decidió eliminarla porque no hay tiempo para definirla; el texto base era una plantilla vacía. |
| 2026-11-22 | 5.6.3 | **Eliminada.** El equipo decidió eliminarla porque no hay tiempo para definirla; el texto base era una plantilla vacía. Subsección 5.6 completa. |
| 2026-11-22 | 13.1.1 | **Aprobada (nueva).** El estándar base no tenía reglas para los DTOs. Una clase que se envía entre el cliente y el servidor lleva `[DataContract]`, y cada una de sus propiedades públicas `[DataMember]`; exigir el contrato explícito es decisión del equipo (la fuente permite que el serializador lo infiera). El juego la cumple: sus 19 clases y 99 propiedades. |
| 2026-11-22 | 13.1.2, 13.1.3 | Reglas nuevas propuestas para los DTOs (solo propiedades; sin herencia). Quedan como **Regla pendiente de revisión**. |
| 2026-11-22 | 13.1.2 | **Eliminada.** Regla nueva propuesta que el equipo no aprobó. |
| 2026-11-22 | 13.1.3 | **Eliminada.** Regla nueva propuesta que el equipo no aprobó. |
| 2026-11-22 | 4.1.1 | **Aprobada sin cambios.** Se conserva el texto del estándar base. |
| 2026-11-22 | 4.1.2 | **Aprobada sin cambios.** Se conserva el texto del estándar base. |
| 2026-11-22 | 4.1.3 | **Aprobada sin cambios.** Se conserva el texto del estándar base. |
| 2026-11-22 | 4.2.1 | **Aprobada sin cambios.** Se conserva el texto del estándar base. |
| 2026-11-22 | 4.2.2 | **Aprobada sin cambios.** Se conserva el texto del estándar base. |
| 2026-11-22 | 4.2.3 | **Aprobada sin cambios.** Se conserva el texto del estándar base. |
| 2026-11-22 | 4.2.4 | **Aprobada sin cambios.** Se conserva el texto del estándar base. |
| 2026-11-22 | 4.2.5 | **Aprobada sin cambios.** Se conserva el texto del estándar base. |
| 2026-11-22 | 4.2.6 | **Aprobada sin cambios.** Se conserva el texto del estándar base. |
| 2026-11-22 | 4.2.7 | **Aprobada sin cambios.** Se conserva el texto del estándar base. |
| 2026-11-22 | 4.2.8 | **Aprobada sin cambios.** Se conserva el texto del estándar base. |
| 2026-11-22 | 4.3.1 | **Aprobada sin cambios.** Se conserva el texto del estándar base. |
| 2026-11-22 | 4.3.2 | **Aprobada sin cambios.** Se conserva el texto del estándar base. |
| 2026-11-22 | 4.3.3 | **Aprobada sin cambios.** Se conserva el texto del estándar base. |
