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
