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

---

## 2.8.3 — Cobertura de lógica central y flujos existentes

**Motivo de eliminación:** no regulaba nombres (tema de la sección 2) y no se podía medir ("priorizar", "cobertura artificial"); la parte de nomenclatura ya la cubren las reglas 2.8.1 y 2.8.2. La idea pasó como texto introductorio, sin obligación, al inicio de la subsección 2.8.

### Regla original
Las pruebas unitarias deben priorizar obligatoriamente la capa de lógica pura del videojuego (como el cálculo de puntuación y las reglas de la partida), evitando forzar una cobertura absoluta artificial que genere fragilidad en el código (Microsoft, 2024). La nomenclatura de la prueba debe reflejar con exactitud el escenario evaluado (flujo principal, alterno o de excepción). Se evaluarán única y exclusivamente los flujos alternos que la arquitectura del método posea realmente.

**Con estándar**
```csharp
[Test]
public void Test_CalculateScore_PlayerKnocks_AddsBonusPoints()
{
}
```

**Sin estándar**
```csharp
[Test]
public void Test_CalculateScore_NormalFlow_Works()
{
}
```

---

## 2.10.1 — Sufijo obligatorio y nomenclatura completa

**Motivo de eliminación:** se eliminó la subsección 2.10 completa porque el proyecto no usa controladores (patrón MVC).

### Regla original
Las clases que actúan como controladores principales de una entidad, sistema lógico o flujo del juego deben definirse en PascalCase y terminar obligatoriamente con el sufijo Controller. Queda prohibido el uso de abreviaturas como "Ctrl".

**Con estándar**
```csharp
public class GameStateController
{
}
```

**Sin estándar**
```csharp
public class GameStateCtrl
{
}
```

---

## 2.10.2 — Eliminación de prefijos tecnológicos

**Motivo de eliminación:** se eliminó la subsección 2.10 completa porque el proyecto no usa controladores (patrón MVC).

### Regla original
El nombre del controlador debe comenzar directamente con el concepto del juego que administra. Queda estrictamente prohibido el uso de prefijos que denoten la tecnología subyacente, el motor de juego o su naturaleza de script (como Script, Unity, Godot, o similares).

**Con estándar**
```csharp
public class PlayerController
{
}
```

**Sin estándar**
```csharp
public class ScriptPlayerController
{
}
```

---

## 2.9.4 — Acrónimo arquitectónico (Dto)

**Motivo de eliminación:** la regla 2.9.3 ya cubre cualquier acrónimo de tres o más letras en el nombre de una clase, incluido `Dto`; además, el proyecto no usa DTO.

### Regla original
De igual manera, el sufijo para los objetos de transferencia de datos debe escribirse siempre en PascalCase (Dto). El uso de mayúsculas sostenidas en acrónimos largos rompe la convención estructural de las clases en C# y genera advertencias en las herramientas de análisis de código estático (Microsoft, 2024).

**Con estándar**
```csharp
public class MatchStateDto
{
}
```

**Sin estándar**
```csharp
public class MatchStateDTO
{
}
```

---

## 2.12.1 — Acceso a datos (Dao)

**Motivo de eliminación:** el proyecto no usa DAO (en la versión 9 del estándar se decidió trabajar con repositorios y unidad de trabajo); la regla obligaba a un patrón que no se usa. Además, el texto decía "nombre del método" cuando hablaba de clases.

### Regla original
Las clases destinadas exclusivamente al acceso a bases de datos o persistencia de archivos locales deben llevar obligatoriamente el sufijo Dao al final del nombre del método (Data Access Object).

**Con estándar**
```csharp
public class PlayerProgressDao
{
}
```

**Sin estándar**
```csharp
public class PlayerProgressDatabase
{
}
```

---

## 8.1.4 — Prohibición de comentarios redundantes

**Motivo de eliminación:** la regla 8.1.3 ya pide que el comentario `//` no repita con otras palabras lo que dice la línea de código que comenta; el "Sin estándar" de la 8.1.4 ya violaba la 8.1.3. Además, al hablar de "comentarios" en general alcanzaba a los `///`, que las reglas 8.1.5 y 8.1.6 exigen con `<summary>`.

### Regla original
Queda estrictamente prohibido escribir comentarios redundantes que simplemente repitan la lógica o el nombre del método de la línea inmediatamente inferior sin aportar valor. Si un comentario no dice nada nuevo que el código no exprese ya claramente por sí mismo, debe ser eliminado para evitar ruido visual y problemas de desactualización futura (Martin, 2008).

**Con estándar**
```csharp
public class TcpMessageSender
{
    public void SendPlayerDisconnectAlert()
    {
        DisconnectClient();
    }

    private void DisconnectClient()
    {
    }
}
```

**Sin estándar**
```csharp
public class TcpMessageSender
{
    // Sends the player disconnect alert.
    public void SendPlayerDisconnectAlert()
    {
        // Disconnects the client.
        DisconnectClient();
    }

    private void DisconnectClient()
    {
    }
}
```

---

## 8.1.5 — Documentación XML (`///`): cuándo se usa

**Motivo de eliminación:** la regla dependía de la estructura del sistema ("capa de servicios", "mecánicas de bajo nivel"), que cambia con el tiempo, y obligaba a documentar cientos de miembros públicos (unos 170 en `GinRummy.Services` o unos 290 en `GinRummy.Contracts`), donde un solo olvido la violaría. Microsoft solo recomienda documentar los tipos y miembros públicos, y advierte que documentar los privados expone el funcionamiento interno, pero no lo prohíbe. La documentación XML queda opcional; las reglas 8.1.6 y 8.1.7 aplican a los bloques que se escriban.

### Regla original
La documentación formal mediante comentarios XML (///) es obligatoria exclusivamente para los tipos y miembros públicos que residen dentro de la capa de servicios del proyecto. Queda explícitamente prohibido el uso de comentarios XML en clases internas, métodos privados o mecánicas de bajo nivel, manteniendo el autocompletado del entorno (IntelliSense) enfocado únicamente en las interfaces de red o mecánicas principales expuestas (Microsoft, s.f.).

**Con estándar**
```csharp
public class MatchService
{
    /// <summary>
    /// Starts a new network match and resets the scores.
    /// </summary>
    public void StartMatch()
    {
    }
}
```

**Sin estándar**
```csharp
public class MatchService
{
    /// <summary>
    /// Randomizes the card arrangement in the deck array.
    /// </summary>
    private void ShuffleDeck()
    {
    }
}
```

---

## 8.1.12 — Balance y densidad de comentarios (evitar sobre-comentar)

**Motivo de eliminación:** la regla repite lo que ya piden otras: la 8.1.3 limita el comentario `//` a lo que el código no expresa y la 2.8.2 pide nombres descriptivos. No define un umbral para "balance estricto" ni para "sobre-comentar", así que no se puede comprobar, y su ejemplo "Sin estándar" ya violaba la 8.1.3.

### Regla original
Se debe mantener un balance estricto en la densidad de comentarios, reservando su uso exclusivamente para explicar código cuya intención no sea evidente. Queda prohibido sobre-comentar; los nombres de clases, métodos y variables deben ser lo suficientemente explícitos por sí mismos (código auto-documentado), mitigando así el riesgo crítico de conservar comentarios que se desactualizan cuando el código evoluciona (Martin, 2008).

**Con estándar**
```csharp
public class MatchValidator
{
    public bool IsValidGin(int deadwoodPoints)
    {
        return deadwoodPoints == GinDeadwoodThreshold;
    }
}
```

**Sin estándar**
```csharp
public class MatchValidator
{
    // Method that validates if the player has Gin.
    public bool IsValidGin(int deadwoodPoints)
    {
        // Returns true if the deadwood points are exactly zero.
        return deadwoodPoints == GinDeadwoodThreshold;
    }
}
```

---

## 2.2.4 — Declaración correcta de propiedades

**Motivo de eliminación:** la regla repite temas que ya cubren otras: la 2.2.1 pide PascalCase en las propiedades, la 2.2.2 pide que los métodos que solo devuelven o asignan un campo sean propiedades y la 2.2.6 pide el `set` restringido. Lo que esas reglas no cubren, prohibir cualquier método `Get...` o `Set...` que obtenga o modifique el estado, era demasiado amplio: alcanzaría a métodos normales como `SetCulture`.

### Regla original
Queda estrictamente prohibido utilizar métodos tradicionales explícitos (como GetValue() o SetValue()) para obtener o modificar el estado de un objeto. En su lugar, se debe utilizar la sintaxis nativa de propiedades declaradas obligatoriamente en formato PascalCase. Se deben emplear auto-propiedades con el descriptor de acceso set restringido (como private set o protected set) para proteger el encapsulamiento de los datos, a menos que la lógica requiera exponer su modificación externa.

**Con estándar**
```csharp
public class CharacterStats
{
    public int CurrentScore { get; private set; }

    public bool IsInvincible { get; protected set; }
}
```

**Sin estándar**
```csharp
public class CharacterStats
{
    private int _currentScore;

    public int GetCurrentScore()
    {
        return _currentScore;
    }

    public void SetCurrentScore(int value)
    {
        _currentScore = value;
    }
}
```

---

## 2.2.5 — Modificación de valor en propiedades

**Motivo de eliminación:** lo único que la regla pedía que se pudiera comprobar era que una propiedad no se lea ni se asigne a sí misma. Ese error hace que el juego se caiga con `StackOverflowException` apenas se ejecuta la línea, así que no puede pasar desapercibido. El campo de respaldo para la lógica del `set` ya queda cubierto por las reglas 2.2.2 y 2.2.3, y el texto original chocaba con las propiedades de dependencia de WPF, que no usan campo de respaldo.

### Regla original
Si la asignación de una propiedad requiere validación o cálculos lógicos, debe declararse un campo privado de respaldo (backing field). La lógica debe ejecutarse dentro del bloque set, evaluando la palabra clave value y asignando el resultado únicamente al campo de respaldo. Queda estrictamente prohibido que una propiedad se referencie o asigne a sí misma, ya que esto provocará un ciclo infinito.

**Con estándar**
```csharp
public class PlayerStats
{
    private int _currentHealth;

    public int CurrentHealth
    {
        get { return _currentHealth; }
        private set
        {
            _currentHealth = Math.Max(0, value);
        }
    }
}
```

**Sin estándar**
```csharp
public class PlayerStats
{
    public int CurrentHealth
    {
        get { return CurrentHealth; }
        private set
        {
            CurrentHealth = Math.Max(0, value);
        }
    }
}
```

---

## 11.1.1 — Ubicación lógica (namespaces)

**Motivo de eliminación:** la regla se acoplaba a decisiones de diseño sobre la estructura: pedía que el namespace de las pruebas replicara el del código de producción (con carpetas como `Entities`, `UseCases` o `Ports`, que pueden cambiar) y que terminara en `.Tests`. Lo único comprobable, que el namespace lleve `.Tests`, ya lo cumple el nombre de los proyectos de pruebas, así que no hace falta una regla.

### Regla original
Las clases de pruebas unitarias deben estar lógicamente separadas del código de producción. Deben ubicarse dentro de un espacio de nombres (namespace) que replique la estructura original del componente a evaluar, añadiendo obligatoriamente el sufijo .Tests al final.

**Con estándar**
```csharp
namespace VideoGame.Combat.Tests
{
}
```

**Sin estándar**
```csharp
namespace VideoGame.Pruebas.Combat
{
}
```

---

## 11.2.3 — Configuración inicial compartida

**Motivo de eliminación:** la regla no se podía medir: "múltiples métodos de prueba" no indica cuántos y "los mismos objetos" no indica si deben ser idénticos o parecidos. Además obligaba a usar un método de inicialización (`[SetUp]`), lo que la acoplaba a NUnit, y un método auxiliar normal no la cumplía. Microsoft recomienda crear los objetos en cada prueba o en métodos auxiliares, y deja la preparación compartida para cuando todas las pruebas de la clase necesitan la misma inicialización (Microsoft, 2026). En 7 clases de pruebas del juego (`PlayRoundUseCaseTests`, `ChallengeBoardTests`, `GameMatchTests`, `GameRoundTests`, `PlayerStatsTests`, `LeaderboardRulesTests` y `MatchRegistryTests`) se repetía la creación de los mismos objetos.

### Regla original
Cuando múltiples métodos de prueba requieran la instanciación de los mismos objetos, esta preparación común debe extraerse obligatoriamente a un método exclusivo marcado con el atributo de inicialización correspondiente (como [SetUp] en NUnit), en lugar de repetirse en cada prueba.

**Con estándar**
```csharp
[SetUp]
public void SetUp()
{
    _playerStats = new PlayerStats();
    _weaponSystem = new WeaponSystem();
}
```

**Sin estándar**
```csharp
public void InitializeConfig()
{
    _playerStats = new PlayerStats();
    _weaponSystem = new WeaponSystem();
}
```

---

## 11.3.1 — Nomenclatura y visibilidad

**Motivo de eliminación:** el prefijo `Builder` no tiene respaldo en ninguna fuente consultada: en el patrón Test Data Builder, "Builder" es el final del nombre de una clase (por ejemplo `AddressDTOBuilder`) con métodos `WithX()` y `Build()`, no un prefijo de método. Además choca con la regla 2.6.2, que pide nombres de métodos con verbo, y "objeto complejo" no tiene una medida. Lo que sí tiene respaldo, extraer la construcción de objetos a un método auxiliar privado de la misma clase de pruebas (Microsoft, 2026), es una recomendación que no se puede convertir en regla sin fijar un límite arbitrario.

### Regla original
Cuando un caso de prueba requiera construir un objeto complejo, esta lógica debe extraerse a un método auxiliar de acceso estrictamente privado (private) dentro de la misma clase de prueba. El nombre del método debe definirse en PascalCase comenzando obligatoriamente con el prefijo Builder seguido de la entidad que se está instanciando.

**Con estándar**
```csharp
private EnemyStats BuilderEnemyStats()
{
}
```

**Sin estándar**
```csharp
public EnemyStats builderEnemyStats()
{
}
```

---

## 11.3.2 — Límite de parámetros en constructores auxiliares e inicialización por defecto

**Motivo de eliminación:** la primera frase repetía el límite de tres parámetros de la regla 2.6.3, que ya aplica a todos los métodos, incluidos los auxiliares de las pruebas. El resto dependía de los conceptos "método builder" y "objeto complejo" de la regla 11.3.1, eliminada, así que ya no tenía de qué hablar, y "los valores más críticos de la prueba" no se podía medir. Sus ejemplos tampoco cumplían las reglas 2.6.2 (nombre `BuilderEnemyStats`) y 5.2.1 (números sueltos `5.5f` y `1`). Se eliminó la subsección 11.3 completa.

### Regla original
Al igual que los métodos operativos regulares, los métodos builder auxiliares no deben recibir más de tres parámetros. Si el objeto complejo requiere una mayor cantidad de atributos para ser instanciado, los parámetros permitidos se usarán para los valores más críticos de la prueba, mientras que los valores sobrantes deberán inicializarse obligatoriamente con datos por defecto dentro del cuerpo del método.

**Con estándar**
```csharp
private EnemyStats BuilderEnemyStats(int maxHealth, float attackDamage, bool isEnraged)
{
    EnemyStats enemyStats = new EnemyStats(maxHealth, attackDamage, isEnraged);
    enemyStats.MovementSpeed = 5.5f;
    enemyStats.ArmorLevel = 1;
    return enemyStats;
}
```

**Sin estándar**
```csharp
private EnemyStats BuilderEnemyStats(int maxHealth, float attackDamage, bool isEnraged,
float movementSpeed, int armorLevel)
{
    EnemyStats enemyStats = new EnemyStats(maxHealth, attackDamage, isEnraged);
    enemyStats.MovementSpeed = movementSpeed;
    enemyStats.ArmorLevel = armorLevel;
    return enemyStats;
}
```

## 6.1.3 — Priorización de excepciones del sistema

**Motivo de eliminación:** repetía la regla 6.4.2, que tiene el mismo título y casi el mismo texto (cambian los ejemplos, `ArgumentOutOfRangeException` en esta y `ArgumentNullException` en la otra). La regla trata de qué excepción lanzar o crear, no de cómo capturarla, así que encaja en la subsección 6.4 (excepciones personalizadas) y no en la 6.1. Su contenido se evalúa en la 6.4.2.

### Regla original
Se debe lanzar obligatoriamente el tipo de excepción predefinido de .NET que describa con exactitud el error antes de crear uno personalizado. Solo se define una excepción propia cuando ningún tipo del sistema la describa adecuadamente, o cuando el bloque que la captura necesite distinguirla programáticamente de otras para aplicar una lógica de recuperación específica (Microsoft, 2024).

**Con estándar**
```csharp
public class ScoreValidator
{
    public void ValidateKnock(int deadwoodScore)
    {
        if (deadwoodScore < 0)
        {
            throw new ArgumentOutOfRangeException(nameof(deadwoodScore));
        }
    }
}
```

**Sin estándar**
```csharp
public class ScoreValidator
{
    public void ValidateKnock(int deadwoodScore)
    {
        if (deadwoodScore < 0)
        {
            throw new InvalidDeadwoodException();
        }
    }
}
```

## 6.2.2 — Jerarquía con excepciones personalizadas

**Motivo de eliminación:** decía que se aplicara "la misma regla jerárquica" de la 6.2.1 a las excepciones propias del juego, sin ningún criterio nuevo que se pudiera revisar; ponerlas en el orden contrario tampoco compila (error CS0160). Usaba `GameSystemException` como excepción base, pero el juego y la regla 6.4.1 usan `GameCoreException`. Su contenido quedó dentro de la 6.2.1, que ahora dice "incluidas las excepciones propias del juego".

### Regla original
Si el sistema implementa excepciones personalizadas para el dominio del videojuego (que heredan de una excepción base propia), se debe aplicar la misma regla jerárquica: la excepción derivada específica del error va primero, y la excepción base del juego se coloca después para capturar cualquier otro error no contemplado del mismo dominio.

**Con estándar**
```csharp
try
{
    ParsePlayerData();
}
catch (SaveFileCorruptedException ex)
{
    RestoreBackup();
}
catch (GameSystemException ex)
{
    NotifyPlayerError();
}
```

**Sin estándar**
```csharp
try
{
    ParsePlayerData();
}
catch (GameSystemException ex)
{
    NotifyPlayerError();
}
catch (SaveFileCorruptedException ex)
{
    RestoreBackup();
}
```

## 6.5.2 — Preferencia por la declaración simplificada (C# 8.0+)

**Motivo de eliminación:** la declaración `using` sin llaves (`using StreamReader replayReader = ...;`) se agregó en C# 8.0, según la lista de novedades de esa versión, y el proyecto usa C# 7.3, así que el ejemplo "Con estándar" no compila. Una regla que el proyecto no puede cumplir no se puede dejar en el estándar. Referencia: Microsoft. (2026, 12 de noviembre). *The history of C#*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-version-history

### Regla original
Para evitar la anidación innecesaria de llaves y reducir la complejidad visual, se debe utilizar preferentemente la declaración simplificada de using (sin llaves) cuando el recurso deba existir durante todo el alcance (scope) del método (Microsoft, 2024).

**Con estándar**
```csharp
public class MatchReplayParser
{
    public void ParseGinRummyHistory(string replayFilePath)
    {
        using StreamReader replayReader = new StreamReader(replayFilePath);
        replayReader.ReadToEnd();
    }
}
```

**Sin estándar**
```csharp
public class MatchReplayParser
{
    public void ParseGinRummyHistory(string replayFilePath)
    {
        using (StreamReader replayReader = new StreamReader(replayFilePath))
        {
            replayReader.ReadToEnd();
        }
    }
}
```

## 6.5.3 — Uso del bloque tradicional para liberación anticipada

**Motivo de eliminación:** con la regla 6.5.2 eliminada, la sentencia `using` con llaves es la única forma que existe en C# 7.3, así que cualquier `using` ya cumple lo que pedía. Lo que quedaba, cerrar el recurso antes de que termine el método ("liberación anticipada"), no tiene un criterio que se pueda medir, y la documentación de Microsoft solo describe cuándo se libera el objeto, no pide hacerlo. Referencia: Microsoft. (2026, 20 de enero). *using statement: ensure the correct use of disposable objects*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/using

### Regla original
Si un recurso debe cerrarse y liberarse explícitamente antes de que finalice el método (por ejemplo, para no retener el archivo abierto mientras se ejecutan operaciones de red posteriores), es obligatorio utilizar la declaración tradicional de using con llaves para delimitar su alcance exacto (Microsoft, 2024).

**Con estándar**
```csharp
public class MatchDealer
{
    public void LoadDeckAndDeal(string deckConfigPath)
    {
        using (StreamReader deckReader = new StreamReader(deckConfigPath))
        {
            deckReader.ReadToEnd();
        }

        DealCardsToPlayers();
    }

    private void DealCardsToPlayers()
    {
    }
}
```

**Sin estándar**
```csharp
public class MatchDealer
{
    public void LoadDeckAndDeal(string deckConfigPath)
    {
        using StreamReader deckReader = new StreamReader(deckConfigPath);
        deckReader.ReadToEnd();

        DealCardsToPlayers();
    }

    private void DealCardsToPlayers()
    {
    }
}
```

## 6.5.1 — Prohibición de liberación manual (`Dispose`)

**Motivo de eliminación:** el equipo decidió eliminarla porque no se entendía. Además, el texto base obligaba a que todo objeto `IDisposable` se creara con `using`, y eso no se puede cumplir con los objetos guardados en campos de una clase (como `_context` y `_transaction` de `EntityFrameworkUnitOfWork`) ni con los clientes de WCF, que Microsoft indica cerrar con `Close()` y `Abort()` en lugar de `using`. Referencia: Microsoft. (2021, 15 de septiembre). *Use Close and Abort to release WCF client resources*. Microsoft Learn. https://learn.microsoft.com/en-us/dotnet/framework/wcf/samples/use-close-abort-release-wcf-client-resources

### Regla original
Todo objeto que implemente la interfaz `IDisposable` (como flujos de archivos o sockets de red) debe instanciarse obligatoriamente empleando la sentencia `using`. Queda estrictamente prohibido intentar liberar los recursos manualmente llamando al método `Dispose()` dentro de un bloque `finally`, ya que `using` automatiza y garantiza esta operación a nivel de compilador. Si es necesario capturar errores operativos, se debe envolver la sentencia `using` completamente dentro de un bloque `try-catch`, manteniendo así el manejo de errores intacto sin sacrificar la delegación automática de la memoria (Microsoft, 2024).

**Con estándar**
```csharp
public class MatchStateStorage
{
    public void SaveMatchLog(string logFilePath)
    {
        try
        {
            using (FileStream logStream = new FileStream(logFilePath, FileMode.OpenOrCreate))
            {
                logStream.Flush();
            }
        }
        catch (IOException ex)
        {
            throw new MatchLogException("Failed to save match log.", ex);
        }
    }
}
```

**Sin estándar**
```csharp
public class MatchStateStorage
{
    public void SaveMatchLog(string logFilePath)
    {
        FileStream logStream = new FileStream(logFilePath, FileMode.OpenOrCreate);
        try
        {
            logStream.Flush();
        }
        catch (IOException ex)
        {
            throw new MatchLogException("Failed to save match log.", ex);
        }
        finally
        {
            logStream.Dispose();
        }
    }
}
```

## 5.6.1 — Tipo de los parámetros de una lambda

**Motivo de eliminación:** el equipo decidió eliminarla porque no hay tiempo para definirla. El texto base era una plantilla vacía ("El título de la regla falta por definirse"), y el juego puede funcionar sin una regla sobre lambdas: que el código use lambdas no viola nada si el estándar no dice nada sobre ellas.

### Regla original
El título de la regla falta por definirse

La regla falta por definirse

## 5.6.2 — Paréntesis de los parámetros de una lambda

**Motivo de eliminación:** regla nueva creada el 2026-11-17 al separar la plantilla vacía 5.6.1; nunca se redactó. El equipo decidió eliminarla porque no hay tiempo para definirla, y que el código use lambdas no viola nada si el estándar no dice nada sobre ellas.

### Regla original
Regla nueva sin texto: quedó como "Regla pendiente de revisión" y nunca se redactó.
