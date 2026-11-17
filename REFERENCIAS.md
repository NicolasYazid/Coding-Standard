# 📚 Referencias por regla

> Fuentes en formato **APA 7** vinculadas a cada regla **aprobada** del estándar.
> El índice de reglas está en [README.md](README.md). Solo se agregan reglas aquí cuando se aprueban.

**Cómo leer cada entrada**
- **Cita en el texto:** la cita que aparece dentro de la descripción de la regla.
- **Referencia:** la referencia completa que va en la lista final del estándar.
- **Qué respalda:** lo que la fuente dice y por qué sostiene la regla.

> ⚠️ **Nota para el documento final:** cuando un mismo autor tenga varias referencias del mismo año (por ejemplo, varias "Microsoft (2023)"), APA 7 exige distinguirlas con letras (2023a, 2023b). Las letras se asignan al armar el documento final, ordenando por título.

---

## 1. Idioma

### 1.1.1 — Identificadores en inglés
**Cita en el texto:** (Microsoft, 2023), (Microsoft, 2016)

- **Referencia:** Microsoft. (2016, 15 de noviembre). *CA1704: Identifiers should be spelled correctly*. Microsoft Learn. https://learn.microsoft.com/en-us/previous-versions/visualstudio/visual-studio-2015/code-quality/ca1704-identifiers-should-be-spelled-correctly
  **Qué respalda:** el analizador de Microsoft divide cada identificador en palabras y revisa su ortografía con el diccionario en inglés; no existen diccionarios de otros idiomas.
- **Referencia:** Microsoft. (2023, 3 de octubre). *General naming conventions*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/general-naming-conventions
  **Qué respalda:** pide elegir identificadores fáciles de leer y pone como ejemplo que `HorizontalAlignment` se lee mejor en inglés que `AlignmentHorizontal`.

### 1.1.2 — Idioma de los comentarios y la documentación
**Cita en el texto:** (ABB, 2019)

- **Referencia:** ABB. (2019, 9 de abril). *C# coding standards* (Documento 9AAD134036, rev. D). https://library.e.abb.com/public/c9cbb85cca364efe85bf65f651c97ef8/ABB-Dev-CS%20Coding%20Standards%20(9AAD134036-D).pdf
  **Qué respalda:** la regla C#302 de este estándar de C# pide que todos los comentarios y variables se escriban en inglés, sean gramaticalmente correctos y tengan la puntuación apropiada.

---

## 2. Reglas de nombrado

### 2.1.1 — Formato de variables locales
**Cita en el texto:** (Microsoft, 2026)

- **Referencia:** Microsoft. (2026, 14 de julio). *C# identifier naming rules and conventions*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/identifier-names
  **Qué respalda:** pide camelCase para los argumentos de métodos y las variables locales, y evitar abreviaturas o acrónimos en los nombres, excepto los ampliamente conocidos y aceptados.

### 2.1.2 — Variables de instancia
**Cita en el texto:** (Microsoft, 2026)

- **Referencia:** Microsoft. (2026, 14 de julio). *C# identifier naming rules and conventions*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/identifier-names
  **Qué respalda:** indica que los campos de instancia privados e internos que no son constantes empiezan con guion bajo (`_`) y usan camelCase.

### 2.1.3 — Contadores de bucle
**Cita en el texto:** (Microsoft, 2026)

- **Referencia:** Microsoft. (2026, 14 de julio). *C# identifier naming rules and conventions*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/identifier-names
  **Qué respalda:** pide evitar los nombres de una sola letra, excepto en contadores de bucles simples.

### 2.1.4 — Colecciones
**Cita en el texto:** (Microsoft, 2023)

- **Referencia:** Microsoft. (2023, 3 de octubre). *Names of type members*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-type-members
  **Qué respalda:** pide nombrar las colecciones con una frase en plural que describa sus elementos, en lugar de una frase en singular seguida de "List" o "Collection".

### 2.1.5 — Booleanos con prefijo "is" (estado)
**Cita en el texto:** (Microsoft, 2023)

- **Referencia:** Microsoft. (2023, 3 de octubre). *Names of type members*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-type-members
  **Qué respalda:** pide nombrar los booleanos con una frase afirmativa y permite los prefijos "Is", "Can" o "Has" cuando aportan significado.

### 2.1.6 — Booleanos con prefijo "has" (posesión o estado completado)
**Cita en el texto:** (Microsoft, 2023)

- **Referencia:** Microsoft. (2023, 3 de octubre). *Names of type members*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-type-members
  **Qué respalda:** pide nombrar los booleanos con una frase afirmativa y permite los prefijos "Is", "Can" o "Has" cuando aportan significado.

### 2.1.7 — Booleanos con prefijo "can" (capacidad o permiso)
**Cita en el texto:** (Microsoft, 2023)

- **Referencia:** Microsoft. (2023, 3 de octubre). *Names of type members*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-type-members
  **Qué respalda:** pide nombrar los booleanos con una frase afirmativa y permite los prefijos "Is", "Can" o "Has" cuando aportan significado.

### 2.1.8 — Declaración única
**Cita en el texto:** (Microsoft, 2025)

- **Referencia:** Microsoft. (2025, 18 de enero). *.NET coding conventions*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions
  **Qué respalda:** pide escribir una sola declaración por línea.

### 2.1.10 — Exención de abreviatura para excepciones (`ex`)
**Cita en el texto:** (Microsoft, 2025)

- **Referencia:** Microsoft. (2025, 18 de enero). *.NET coding conventions*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions
  **Qué respalda:** el ejemplo de `try-catch` de las convenciones oficiales de C# nombra `ex` a la excepción capturada. No existe una regla escrita de Microsoft sobre ese nombre; el respaldo es su ejemplo oficial.

### 2.1.11 — Prefijo estático `s_`
**Cita en el texto:** (Microsoft, 2026)

- **Referencia:** Microsoft. (2026, 14 de julio). *C# identifier naming rules and conventions*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/identifier-names
  **Qué respalda:** indica que los campos `static` privados o internos usan el prefijo `s_`; aclara que no es el comportamiento predeterminado de Visual Studio, pero se puede configurar en editorconfig.

### 2.2.1 — Nomenclatura de propiedades
**Cita en el texto:** (Microsoft, 2023)

- **Referencia:** Microsoft. (2023, 3 de octubre). *Capitalization conventions*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/capitalization-conventions
  **Qué respalda:** pide PascalCase para todos los nombres de miembros públicos, tipos y espacios de nombres; su tabla de ejemplos incluye las propiedades.

### 2.2.6 — Set restringido
**Cita en el texto:** (Microsoft, 2023)

- **Referencia:** Microsoft. (2023, 3 de octubre). *Property design*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/property
  **Qué respalda:** pide crear propiedades de solo lectura si quien las usa no debe poder cambiar su valor.
- **Referencia:** Microsoft. (2025, 19 de noviembre). *Properties (C# programming guide)*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/properties
  **Qué respalda:** muestra que con un `set` privado la propiedad puede leerse desde cualquier código, pero solo asignarse desde la propia clase.

---

## 9. Estructuras de control

### 9.1.3 — Interior del bloque
**Cita en el texto:** (DotNetAnalyzers, s.f.-a, s.f.-b)

- **Referencia:** DotNetAnalyzers. (s.f.-a). *SA1505: Opening braces should not be followed by blank line*. GitHub. Recuperado el 16 de noviembre de 2026, de https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1505.md
  **Qué respalda:** marca como violación una línea en blanco después de una llave de apertura.
- **Referencia:** DotNetAnalyzers. (s.f.-b). *SA1508: Closing braces should not be preceded by blank line*. GitHub. Recuperado el 16 de noviembre de 2026, de https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1508.md
  **Qué respalda:** marca como violación una línea en blanco antes de una llave de cierre.

### 9.1.2 — Obligatoriedad de las llaves
**Cita en el texto:** (Microsoft, 2023)

- **Referencia:** Microsoft. (2023, 25 de julio). *Add braces (IDE0011)*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/ide0011
  **Qué respalda:** la regla de estilo IDE0011 trata del uso de llaves para encerrar bloques de código; su valor predeterminado prefiere llaves incluso para una sola línea de código.

### 9.1.1 — Estilo de llaves (Allman)
**Cita en el texto:** (Microsoft, 2025a)

- **Referencia:** Microsoft. (2025, 18 de enero). *.NET coding conventions*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions
  **Qué respalda:** pide el estilo Allman: la llave de apertura y la de cierre en su propia línea, alineadas con el nivel de indentación actual.

### 9.1.4 — Formato de los accesores
**Cita en el texto:** (Microsoft, 2025b)

- **Referencia:** Microsoft. (2025, 30 de enero). *C# formatting options*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/csharp-formatting-options
  **Qué respalda:** la opción `csharp_preserve_single_line_blocks` tiene como valor predeterminado dejar en una sola línea los bloques de código escritos así.

### 9.1.7 — Formato de los tipos anónimos
**Cita en el texto:** (Microsoft, 2025b)

- **Referencia:** Microsoft. (2025, 30 de enero). *C# formatting options*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/csharp-formatting-options
  **Qué respalda:** la opción `csharp_new_line_before_members_in_anonymous_types` tiene como valor predeterminado exigir que los miembros de los tipos anónimos vayan en líneas separadas.

### 9.1.6 — Formato de los inicializadores de colección
**Cita en el texto:** (Microsoft, 2026a)

- **Referencia:** Microsoft. (2026, 11 de febrero). *Object and collection initializers (C# programming guide)*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers
  **Qué respalda:** sus ejemplos escriben en una sola línea las colecciones de valores simples, y en varias líneas, un objeto por línea, las colecciones de objetos. Es respaldo por ejemplos, no una indicación escrita.

### 9.1.8 — Formato de los inicializadores de arreglo
**Cita en el texto:** (Microsoft, 2026b)

- **Referencia:** Microsoft. (2026, 20 de enero). *Arrays*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/arrays
  **Qué respalda:** sus ejemplos escriben en una sola línea los arreglos de una dimensión. Es respaldo por ejemplos, no una indicación escrita.
- **Referencia:** Microsoft. (2025, 18 de enero). *.NET coding conventions*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions
  **Qué respalda:** recomienda partir en varias líneas las instrucciones largas para mejorar su lectura (caso en que se supera el límite de columna).

### 9.1.5 — Formato de los inicializadores de objeto
**Cita en el texto:** (Microsoft, 2025b)

- **Referencia:** Microsoft. (2025, 30 de enero). *C# formatting options*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/csharp-formatting-options
  **Qué respalda:** la opción `csharp_new_line_before_members_in_object_initializers` tiene como valor predeterminado exigir que los miembros de un inicializador de objeto vayan en líneas separadas.

### 9.2.1 — Agrupación de las cláusulas
**Cita en el texto:** (Microsoft, 2022)

- **Referencia:** Microsoft. (2022, 20 de octubre). *Parentheses preferences (IDE0047 and IDE0048)*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/ide0047-ide0048
  **Qué respalda:** define los operadores relacionales y su valor predeterminado usa paréntesis para aclarar la precedencia de esos operadores.

### 9.2.2 — Prohibición de comparar con literales booleanos
**Cita en el texto:** (Microsoft, 2023)

- **Referencia:** Microsoft. (2023, 25 de julio). *Remove unnecessary equality operator (IDE0100)*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/ide0100
  **Qué respalda:** marca como innecesario el operador de igualdad al comparar una expresión booleana no constante con `true` o `false`.

### 9.3.1 — Ámbito de la variable de control
**Cita en el texto:** (Microsoft, 2026c)

- **Referencia:** Microsoft. (2026, 20 de enero). *Iteration statements - for, foreach, do, and while*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/iteration-statements
  **Qué respalda:** la variable de control se declara e inicializa en la sección de inicialización del `for`, y no se puede acceder a ella desde fuera de la sentencia `for`.

### 9.3.3 — Prohibición de modificar la colección recorrida
**Cita en el texto:** (Microsoft, 2025c)

- **Referencia:** Microsoft. (2025, 1 de julio). *List<T>.GetEnumerator method*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1.getenumerator
  **Qué respalda:** si se agregan, modifican o eliminan elementos de la colección, el enumerador queda invalidado y la siguiente llamada a `MoveNext` lanza `InvalidOperationException`.

### 9.3.5 — Condición de salida en la cabecera
**Cita en el texto:** (Microsoft, s.f.)

- **Referencia:** Microsoft. (s.f.). *TcpListener class*. Microsoft Learn. Recuperado el 16 de noviembre de 2026, de https://learn.microsoft.com/en-us/dotnet/api/system.net.sockets.tcplistener
  **Qué respalda:** el ejemplo oficial usa un bucle `while(true)` que llama a `AcceptTcpClient` para escuchar conexiones (excepción de la regla).

### 9.3.2 — Recorrido de colecciones
**Cita en el texto:** (Microsoft, 2026d)

- **Referencia:** Microsoft. (2026, 13 de abril). *Refactoring to convert between a for loop and a foreach statement*. Microsoft Learn. https://learn.microsoft.com/en-us/visualstudio/ide/reference/convert-for-loop-to-foreach
  **Qué respalda:** convertir un `for` a `foreach` es útil cuando no se necesita la variable del bucle como índice y se quiere simplificar el código.

### 9.4.1 — Elección del switch
**Cita en el texto:** (Microsoft, s.f.-a)

- **Referencia:** Microsoft. (s.f.-a). *Convert if statement to switch statement or switch expression*. Microsoft Learn. Recuperado el 16 de noviembre de 2026, de https://learn.microsoft.com/en-us/visualstudio/ide/reference/convert-if-statement-to-switch-statement-or-switch-expression
  **Qué respalda:** convertir un `if` en `switch` es útil cuando el `if` sería más claro como `switch`.

### 9.4.2 — Uso de llaves en el cuerpo de un case
**Cita en el texto:** (Microsoft, s.f.-b)

- **Referencia:** Microsoft. (s.f.-b). *Statements (C# language specification)*. Microsoft Learn. Recuperado el 16 de noviembre de 2026, de https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/statements
  **Qué respalda:** el ámbito de una variable local declarada en un bloque switch es todo el bloque switch.

### 9.4.4 — Agrupación de etiquetas
**Cita en el texto:** (Microsoft, 2026e)

- **Referencia:** Microsoft. (2026, 20 de enero). *Selection statements - if, if-else, and switch*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/selection-statements
  **Qué respalda:** aplicar varias etiquetas a una misma sección es una decisión de diseño deliberada para manejar de forma concisa varios casos con lógica compartida.

### 9.4.5 — Cuerpo de la sección
**Cita en el texto:** (McConnell, 2004)

- **Referencia:** McConnell, S. (2004). *Code complete* (2.ª ed.). Microsoft Press.
  **Qué respalda:** recomienda extraer a una rutina las acciones complicadas de un caso. Fuente del estándar base; texto exacto no disponible en línea.
