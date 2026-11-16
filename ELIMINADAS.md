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
