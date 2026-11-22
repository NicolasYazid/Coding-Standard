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

### 9.4.3 — Cláusula default obligatoria
**Cita en el texto:** (Microsoft, 2026e)

- **Referencia:** Microsoft. (2026, 20 de enero). *Selection statements - if, if-else, and switch*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/selection-statements
  **Qué respalda:** si ninguna etiqueta coincide y no hay default, el control sale del switch sin ejecutar nada.

### 9.5.1 — Ámbito de uso
**Cita en el texto:** (Microsoft, 2026f)

- **Referencia:** Microsoft. (2026, 24 de enero). *?: operator - the ternary conditional operator*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/conditional-operator
  **Qué respalda:** el ternario evalúa una condición y devuelve el resultado de una de dos expresiones; conviene usarlo cuando se necesita calcular un valor de forma condicional.

### 9.5.2 — Prohibición del ternario anidado
**Cita en el texto:** (DeepSource, s.f.)

- **Referencia:** DeepSource. (s.f.). *Avoid nested ternary expressions (CS-R1114)*. Recuperado el 17 de noviembre de 2026, de https://deepsource.com/directory/csharp/issues/CS-R1114
  **Qué respalda:** regla de un analizador de código C#: el ternario anidado afecta la legibilidad y se recomienda no anidarlo. No existe una fuente de Microsoft que lo prohíba.

### 9.5.4 — Extensión del ternario
**Cita en el texto:** (Microsoft, 2025d)

- **Referencia:** Microsoft. (2025, 21 de agosto). *Blank line not allowed after conditional expression token (IDE2005)*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/ide2005
  **Qué respalda:** el ternario partido en varias líneas, con `?` y `:` al inicio de cada línea y 4 espacios más de sangría (regla experimental).

### 9.5.3 — Ramas booleanas explícitas
**Cita en el texto:** (Microsoft, 2022b)

- **Referencia:** Microsoft. (2022, 25 de junio). *Simplify conditional expression (IDE0075)*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/ide0075
  **Qué respalda:** con la opción `dotnet_style_prefer_simplified_boolean_expressions = false`, Microsoft muestra como forma válida el ternario `M1() && M2() ? true : false`. El `.editorconfig` debe incluir esa opción en `false`.

### 2.5.1 — Nomenclatura (PascalCase)
**Cita en el texto:** (Microsoft, 2026)

- **Referencia:** Microsoft. (2026, 14 de julio). *C# identifier naming rules and conventions*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/identifier-names
  **Qué respalda:** usar PascalCase en los nombres de constantes, tanto campos como constantes locales, incluidas las `private` e `internal`.

### 2.5.2 — Uso de const
**Cita en el texto:** (Microsoft, 2023; Microsoft, 2026g)

- **Referencia:** Microsoft. (2023, 3 de octubre). *Field design*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/field
  **Qué respalda:** usar campos constantes para las constantes que nunca cambiarán.
- **Referencia:** Microsoft. (2026, 2 de abril). *CA1802: Use literals where appropriate*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/quality-rules/ca1802
  **Qué respalda:** un campo `static readonly` cuyo valor se puede calcular al compilar debe cambiarse a `const`.

### 2.5.3 — Uso de static readonly
**Cita en el texto:** (Microsoft, 2023; Microsoft, 2026g)

- **Referencia:** Microsoft. (2023, 3 de octubre). *Field design*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/field
  **Qué respalda:** usar campos `static readonly` para las instancias de objetos predefinidas.
- **Referencia:** Microsoft. (2026, 2 de abril). *CA1802: Use literals where appropriate*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/quality-rules/ca1802
  **Qué respalda:** el valor de un campo `static readonly` se calcula al ejecutar el programa; el de un `const`, al compilar.

### 2.6.1 — Nomenclatura (PascalCase)
**Cita en el texto:** (Microsoft, 2026)

- **Referencia:** Microsoft. (2026, 14 de julio). *C# identifier naming rules and conventions*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/identifier-names
  **Qué respalda:** usar PascalCase en los nombres de clases y métodos.

### 2.6.2 — Verbos o frases verbales
**Cita en el texto:** (Microsoft, 2023)

- **Referencia:** Microsoft. (2023, 3 de octubre). *Names of type members*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-type-members
  **Qué respalda:** los nombres de los métodos deben ser verbos o frases verbales.

### 2.6.3 — Límite de parámetros
**Cita en el texto:** (SonarSource, s.f.)

- **Referencia:** SonarSource. (s.f.). *Methods should not have too many parameters (S107)*. Recuperado el 17 de noviembre de 2026, de https://rules.sonarsource.com/csharp/tag/brain-overload/RSPEC-107
  **Qué respalda:** regla de análisis de código para C# que marca los métodos con más parámetros que el límite configurado (el del equipo es tres).

### 2.7.1 — Prefijo On (método que lanza un evento)
**Cita en el texto:** (Microsoft, 2026h)

- **Referencia:** Microsoft. (2026, 23 de marzo). *Handling and raising events*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/standard/events/
  **Qué respalda:** el método que lanza un evento se nombra `On<EventName>`, por ejemplo `OnDataReceived`.

### 2.7.2 — Prefijo Handle (método que reacciona a un evento)
**Cita en el texto:** (Microsoft, 2021)

- **Referencia:** Microsoft. (2021, 12 de octubre). *How to subscribe to and unsubscribe from events*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events
  **Qué respalda:** su ejemplo nombra `HandleCustomEvent` al método que reacciona a un evento (ejemplo de código, no indicación escrita).

### 2.7.3 — Prefijo Toggle (alternancia de estados booleanos)
**Cita en el texto:** (Microsoft, 2025e)

- **Referencia:** Microsoft. (2025e). *IToggleProvider.Toggle method*. Microsoft Learn. Recuperado el 17 de noviembre de 2026, de https://learn.microsoft.com/en-us/dotnet/api/system.windows.automation.provider.itoggleprovider.toggle
  **Qué respalda:** en .NET, `Toggle` nombra la acción de pasar de un estado al otro ("Cycles through the toggle states of a control").

### 2.7.4 — Descriptores directos (sin prefijo)
**Cita en el texto:** (Microsoft, 2023)

- **Referencia:** Microsoft. (2023, 3 de octubre). *Names of type members*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-type-members
  **Qué respalda:** pide dar a los métodos nombres que sean verbos o frases verbales ("DO give methods names that are verbs or verb phrases").

### 2.8.1 — Estructura de nomenclatura (prefijo Test)
**Cita en el texto:** (Microsoft, 2026i)

- **Referencia:** Microsoft. (2026i, 6 de noviembre). *Unit testing best practices for .NET*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices
  **Qué respalda:** el nombre de una prueba tiene tres partes: el método que se prueba, el escenario y el comportamiento esperado (ejemplo `Add_SingleNumber_ReturnsSameNumber`). El prefijo `Test` es decisión del equipo.

### 2.8.2 — Nombres descriptivos vs. genéricos
**Cita en el texto:** (Microsoft, 2026i)

- **Referencia:** Microsoft. (2026i, 6 de noviembre). *Unit testing best practices for .NET*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices
  **Qué respalda:** el nombre de la prueba debe tener el método, el escenario y el comportamiento esperado; en su ejemplo de código cambia el nombre genérico `Test_Single` por `Add_SingleNumber_ReturnsSameNumber`.

### 2.8.4 — Atributos de prueba
**Cita en el texto:** (NUnit Project, s.f.)

- **Referencia:** NUnit Project. (s.f.). *Test attribute*. NUnit Docs. https://docs.nunit.org/articles/nunit/writing-tests/attributes/test.html
  **Qué respalda:** el atributo `Test` es lo que marca un método dentro de una clase de pruebas como prueba ("The Test attribute marks a method inside a test fixture as a test").

### 5.1.1 — Punto único de retorno en métodos con valor de retorno
**Cita en el texto:** ninguna.

- **Sin referencia:** regla del equipo. No se encontró una fuente oficial de C# que exija un solo `return`; la regla S1142 de SonarSource solo existe para otros lenguajes y permite hasta tres.

### 5.2.1 — Prevención de números mágicos
**Cita en el texto:** ninguna.

- **Sin referencia:** el equipo retiró la cita "(Microsoft, s.f.)" porque no apuntaba a una página concreta.

### 5.3.1 — Número máximo de operaciones en expresiones
**Cita en el texto:** ninguna.

- **Sin referencia:** regla del equipo (límite de tres operadores fijado por el equipo).

### 5.4.1 — Complejidad ciclomática
**Cita en el texto:** (Microsoft, s.f.)

- **Referencia:** Microsoft. (s.f.). *Code metrics - Cyclomatic complexity*. Microsoft Learn. https://learn.microsoft.com/en-us/visualstudio/code-quality/code-metrics-cyclomatic-complexity
  **Qué respalda:** recomienda 10 como límite de complejidad ciclomática (citando a NIST 500-235) y reserva los límites mayores a 10 para casos justificados.

### 5.5.1 — Prohibición de retorno nulo en colecciones
**Cita en el texto:** (Microsoft, 2021)

- **Referencia:** Microsoft. (2021, 15 de septiembre). *Guidelines for collections*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/guidelines-for-collections
  **Qué respalda:** "DO NOT return null values from collection properties or from methods returning collections. Return an empty collection or an empty array instead."

### 2.9.1 — Nomenclatura base (PascalCase)
**Cita en el texto:** (Microsoft, 2023)

- **Referencia:** Microsoft. (2023, 3 de octubre). *Names of classes, structs, and interfaces*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-classes-structs-and-interfaces
  **Qué respalda:** "DO name classes and structs with nouns or noun phrases, using PascalCasing", para distinguir los nombres de tipos de los métodos, que se nombran con frases verbales.

### 2.9.2 — Nombre de clase sin prefijo
**Cita en el texto:** (Microsoft, 2023)

- **Referencia:** Microsoft. (2023, 3 de octubre). *Names of classes, structs, and interfaces*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-classes-structs-and-interfaces
  **Qué respalda:** "DO NOT give class names a prefix (e.g., "C")."

### 2.9.3 — Acrónimos en el nombre de una clase
**Cita en el texto:** (Microsoft, 2023)

- **Referencia:** Microsoft. (2023, 3 de octubre). *Capitalization conventions*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/capitalization-conventions
  **Qué respalda:** PascalCasing pone en mayúscula la primera letra de cada palabra, "including acronyms over two letters in length".

### 2.11.1 — Prefijo obligatorio y convención base (PascalCase)
**Cita en el texto:** (Microsoft, 2023)

- **Referencia:** Microsoft. (2023, 3 de octubre). *Names of classes, structs, and interfaces*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-classes-structs-and-interfaces
  **Qué respalda:** "DO name interfaces with adjective phrases, or occasionally with nouns or noun phrases" y "DO prefix interface names with the letter I, to indicate that the type is an interface."
