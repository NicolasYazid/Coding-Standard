# 🗑️ Reglas eliminadas

> Reglas del estándar base (118 páginas) que **no pasaron** al estándar definitivo, copiadas tal como estaban.
> Índice de reglas: [README.md](README.md).

---

## 1.1.3 — Idioma de los mensajes de error (Logs y Excepciones)

**Motivo de eliminación:** no existe una fuente de C# que respalde escribir estos mensajes en inglés; Microsoft recomienda traducir los mensajes de excepción en aplicaciones localizadas, y el videojuego es localizado (español e inglés).

### Regla original
Todos los mensajes lanzados a través de excepciones o registrados en los sistemas de logs deben escribirse estrictamente en inglés.

**Con estándar**
```csharp
public class SaveSystem
{
    public void LoadGame()
    {
        throw new SaveStorageException("The save storage could not be opened.");
    }
}
```

**Sin estándar**
```csharp
public class SaveSystem
{
    public void LoadGame()
    {
        throw new SaveStorageException("No se pudo abrir el almacenamiento de partida.");
    }
}
```

---

## 2.1.9 — Prevención de sombreado de datos

**Motivo de eliminación:** el proyecto usa C# 7.3, donde el compilador ya impide que una variable local o un parámetro (incluidos los de lambdas y funciones locales) se llame igual que otra variable local del ámbito que lo contiene (error CS0136). Además, las reglas 2.1.1, 2.1.2 y 2.1.11 impiden que una variable local se llame igual que un campo, porque los campos llevan `_` o `s_`. La regla no podía violarse.

### Regla original
Está prohibido nombrar una variable local o un parámetro con el mismo nombre que una variable de mayor ámbito (como un campo de clase de instancia sin su prefijo), para evitar confusiones de lógica.

**Con estándar**
```csharp
public void UpdateHealth(int newHealth)
{
    _health = newHealth;
}
```

**Sin estándar**
```csharp
public void UpdateHealth(int _health)
{
    this._health = _health;
}
```
