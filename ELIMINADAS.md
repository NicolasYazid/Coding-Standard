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

---

## 9.2.3 — Cláusula de guarda

**Motivo de eliminación:** decisión del equipo. Su redacción hacía violación cualquier método `void` cuyo cuerpo fuera un solo `if` (53 métodos del proyecto y varios ejemplos de reglas aprobadas), y dependía de la regla 5.1.1 (punto único de retorno).

### Regla original
Las condiciones que impiden continuar la ejecución de un método se resuelven con una salida temprana (return), en lugar de anidar el resto del cuerpo dentro de ellas, ya que esta técnica reduce la profundidad de anidamiento y mejora la legibilidad del código (McConnell, 2004).

**Con estándar**
```csharp
public class TurnProcessor
{
    public void ProcessTurn(bool isMatchActive, bool hasCardsInStock)
    {
        if (!isMatchActive)
        {
            return;
        }
        if (!hasCardsInStock)
        {
            return;
        }
        DealNextCard();
    }

    private void DealNextCard()
    {
    }
}
```

**Sin estándar**
```csharp
public class TurnProcessor
{
    public void ProcessTurn(bool isMatchActive, bool hasCardsInStock)
    {
        if (isMatchActive)
        {
            if (hasCardsInStock)
            {
                DealNextCard();
            }
        }
    }

    private void DealNextCard()
    {
    }
}
```

---

## 9.3.4 — Elección del do-while

**Motivo de eliminación:** decisión del equipo. La regla solo describía para qué sirve un `do-while` (ejecutar el cuerpo al menos una vez), igual que decir que un `if` sirve para tomar decisiones; no prevenía ningún defecto.

### Regla original
El do-while se reserva para los casos en que el cuerpo debe ejecutarse al menos una vez antes de evaluar la condición, a diferencia del while, que puede no ejecutarse nunca (Microsoft, s.f.).

**Con estándar**
```csharp
public class ServerConnector
{
    private const int MaxAttempts = 3;
    private int _connectionAttempts;

    public void ConnectWithRetry()
    {
        do
        {
            _connectionAttempts++;
        }
        while (_connectionAttempts < MaxAttempts);
    }
}
```

**Sin estándar**
```csharp
public class ServerConnector
{
    private const int MaxAttempts = 3;
    private int _connectionAttempts;

    public void ConnectWithRetry()
    {
        bool isFirstAttempt = true;
        while (isFirstAttempt || _connectionAttempts < MaxAttempts)
        {
            isFirstAttempt = false;
            _connectionAttempts++;
        }
    }
}
```

---

## 2.7.5 — Límite de parámetros en eventos

**Motivo de eliminación:** repetía el límite de tres parámetros que la regla 2.6.3 ya fija para todo método o constructor, incluidos los manejadores de eventos.

### Regla original
Al igual que los métodos regulares, los manejadores de eventos no deben exceder el límite estricto de tres parámetros.

**Con estándar**
```csharp
public void OnCollisionEnter(string hitTag, float impactForce)
{
}
```

**Sin estándar**
```csharp
public void OnCollisionEnter(string hitTag, float impactForce, bool isCritical, int damageAmount)
{
}
```
