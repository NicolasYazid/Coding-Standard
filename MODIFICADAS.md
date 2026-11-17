# ✏️ Reglas modificadas

> Cada entrada muestra la regla **como estaba** en el estándar base y **como quedó** en el estándar definitivo.
> Índice de reglas: [README.md](README.md).

---

## 1.1.1 — Identificadores en inglés

### Antes: Prohibición de identificadores en español
Todo el código fuente debe escribirse obligatoriamente en inglés. Esto incluye los nombres de clases, interfaces, métodos, propiedades, constantes, variables y parámetros. Queda estrictamente prohibido utilizar palabras en español, spanglish o mezclar idiomas en los identificadores.

**Con estándar**
```csharp
public class PlayerStats
{
    private int _remainingLives;
}
```

**Sin estándar**
```csharp
public class PlayerStats
{
    private int _vidasRestantes;
}
```

### Después: Identificadores en inglés
Todo identificador (el nombre que se le da a un tipo, miembro, variable o namespace) debe formarse solo con palabras en inglés. No se permiten palabras en español ni nombres que mezclen ambos idiomas. Las convenciones de nombres de .NET están pensadas para que los nombres se lean en inglés (Microsoft, 2023), y el analizador de ortografía de identificadores de Microsoft solo tiene diccionario en inglés (Microsoft, 2016).

**Con estándar**
```csharp
public class PlayerHand
{
    private int _deadwoodPoints;

    public void AddDeadwoodPoints(int cardPoints)
    {
        _deadwoodPoints += cardPoints;
    }
}
```

**Sin estándar**
```csharp
public class ManoJugador
{
    private int _puntosMuertos;

    public void AddPuntos(int cardPoints)
    {
        _puntosMuertos += cardPoints;
    }
}
```

---

## 1.1.2 — Idioma de los comentarios y la documentación

### Antes
Todo comentario debe escribirse en inglés, tanto comentarios de implementación como de documentación.

**Con estándar**
```csharp
public class Hand
{
    private readonly List<Card> _cards = new List<Card>();

    public void Discard(Card card)
    {
        // The card is removed from the hand because it now belongs to the discard pile.
        _cards.Remove(card);
    }
}
```

**Sin estándar**
```csharp
public class Hand
{
    private readonly List<Card> _cards = new List<Card>();

    public void Discard(Card card)
    {
        // La carta se quita de la mano porque ahora pertenece a la pila de descarte.
        _cards.Remove(card);
    }
}
```

### Después
Todo comentario debe escribirse en inglés, tanto comentarios de implementación como de documentación XML (`///`). Así, quien lee el código no cambia de idioma entre el código y su explicación (ABB, 2019).

**Con estándar**
```csharp
public class MatchScorer
{
    private int _knockerScore;

    public void ApplyUndercutPenalty(int undercutPoints)
    {
        // The knocker loses points because the opponent finished with equal or lower deadwood.
        _knockerScore -= undercutPoints;
    }
}
```

**Sin estándar**
```csharp
public class MatchScorer
{
    private int _knockerScore;

    public void ApplyUndercutPenalty(int undercutPoints)
    {
        // El que tocó pierde puntos porque el rival terminó con igual o menos deadwood.
        _knockerScore -= undercutPoints;
    }
}
```

---

## 2.1.1 — Formato de variables locales

### Antes
Las variables locales deben escribirse utilizando camelCase. Deben ser palabras o frases descriptivas en inglés. Queda estrictamente prohibido el uso de abreviaturas incomprensibles.

**Con estándar**
```csharp
int playerHealth = 100;
```

**Sin estándar**
```csharp
int ph = 100;
```

### Después
Las variables locales y los parámetros de los métodos se escriben en camelCase, con palabras completas o frases que describan lo que guardan. Queda prohibido usar abreviaturas, a menos que sean ampliamente conocidas y aceptadas (Microsoft, 2026).

**Con estándar**
```csharp
public class DeadwoodCalculator
{
    public int CalculateRemainingDeadwood(int handDeadwood, int meldedPoints)
    {
        int remainingDeadwood = handDeadwood - meldedPoints;

        return remainingDeadwood;
    }
}
```

**Sin estándar**
```csharp
public class DeadwoodCalculator
{
    public int CalculateRemainingDeadwood(int HandDeadwood, int mldPts)
    {
        int remDw = HandDeadwood - mldPts;

        return remDw;
    }
}
```

---

## 2.1.2 — Variables de instancia

### Antes
Los campos privados a nivel de clase (variables de instancia) deben llevar el prefijo guion bajo (_) seguido del formato camelCase, para distinguirlas visualmente de las variables locales dentro de los métodos.

**Con estándar**
```csharp
private int _currentHealth;
```

**Sin estándar**
```csharp
private int currentHealth;
```

### Después
Las variables de instancia (campos de la clase que no son `static` ni `const`) que sean privadas o internas se escriben con el prefijo guion bajo (`_`) seguido de camelCase, para distinguirlas de las variables locales y los parámetros (Microsoft, 2026).

**Con estándar**
```csharp
public class GameTable
{
    private int _roundNumber;

    public void StartNextRound()
    {
        _roundNumber++;
    }
}
```

**Sin estándar**
```csharp
public class GameTable
{
    private int roundNumber;

    public void StartNextRound()
    {
        roundNumber++;
    }
}
```

---

## 2.1.3 — Contadores de bucle

### Antes
El uso de variables de un solo carácter (como i, j, k) está permitido única y exclusivamente para contadores de bucles, siempre y cuando el bloque de código del bucle no supere las 3 líneas.

**Con estándar**
```csharp
for (int i = 0; i < 3; i++)
{
    SpawnEnemy();
}
```

**Sin estándar**
```csharp
// Variable de un solo carácter utilizada fuera de un bucle corto
int c = 10;
```

### Después
Se permite un nombre de una sola letra únicamente para el contador de un bucle, siempre que el cuerpo del bucle no supere las 3 líneas, las letras disponibles son (i, j, k), si se necesita otra letra más entonces el código debe ser refactorizado. Microsoft pide evitar los nombres de una sola letra, excepto en contadores de bucles simples (Microsoft, 2026).

**Con estándar**
```csharp
public class CardDealer
{
    private const int InitialHandSize = 10;

    public void DealInitialHand(List<Card> deckCards, List<Card> handCards)
    {
        for (int i = 0; i < InitialHandSize; i++)
        {
            handCards.Add(deckCards[i]);
        }
    }
}
```

**Sin estándar**
```csharp
public class CardDealer
{
    private const int InitialHandSize = 10;
    private int _dealtCardsCount;

    public void DealInitialHand(List<Card> deckCards, List<Card> handCards)
    {
        for (int i = 0; i < InitialHandSize; i++)
        {
            Card dealtCard = deckCards[i];
            dealtCard.IsFaceUp = false;
            handCards.Add(dealtCard);
            _dealtCardsCount++;
        }
    }
}
```

---

## 2.1.4 — Colecciones

### Antes
Las variables que representan colecciones deben nombrarse siempre en plural para indicar la contención de múltiples valores.

**Con estándar**
```csharp
List<string> collectedItems;
```

**Sin estándar**
```csharp
List<string> collectedItem;
```

### Después
Toda variable, parámetro, campo o propiedad que guarde una colección se nombra en plural, describiendo los elementos que contiene. Queda prohibido nombrarla en singular o tener los sufijos "List" o "Collection". En caso de sustantivos incontables o sin plural, se deben usar términos colectivos descriptivos (Microsoft, 2023).

**Con estándar**
```csharp
public class PlayerHand
{
    private readonly List<Card> _heldCards = new List<Card>();

    public void AddDrawnCard(Card drawnCard)
    {
        _heldCards.Add(drawnCard);
    }
}
```

**Sin estándar**
```csharp
public class PlayerHand
{
    private readonly List<Card> _heldCardList = new List<Card>();

    public void AddDrawnCard(Card drawnCard)
    {
        _heldCardList.Add(drawnCard);
    }
}
```

---

## 2.1.5 — Booleanos con prefijo "is" (Estado)

### Antes
El prefijo is debe utilizarse para variables booleanas que describan un estado físico, lógico o una condición actual en la que se encuentra una entidad o sistema.

**Con estándar**
```csharp
bool isPoisoned;
```

**Sin estándar**
```csharp
bool poisoned;
```

### Después
El prefijo is debe utilizarse para variables booleanas que describan un estado físico, lógico o una condición actual en la que se encuentra una entidad o sistema (Microsoft, 2023).

**Con estándar**
```csharp
public class PlayerConnection
{
    public void UpdateConnectionStatus(bool isConnected)
    {
    }
}
```

**Sin estándar**
```csharp
public class PlayerConnection
{
    public void UpdateConnectionStatus(bool connected)
    {
    }
}
```

---

## 2.1.6 — Booleanos con prefijo "has" (Posesión o estado completado)

### Antes
El prefijo has debe utilizarse para variables booleanas que indiquen la posesión de un objeto, atributo, o bien, que un evento ya ha ocurrido o finalizado.

**Con estándar**
```csharp
bool hasBossKey;
```

**Sin estándar**
```csharp
bool bossKey;
```

### Después
El prefijo has debe utilizarse para variables booleanas que indiquen la posesión de un objeto, atributo, o bien, que un evento ya ha ocurrido o finalizado (Microsoft, 2023).

**Con estándar**
```csharp
public class TurnValidator
{
    private const int HandSizeBeforeDraw = 10;

    public bool CheckDrawCompleted(int heldCardsCount)
    {
        bool hasDrawnCard = heldCardsCount > HandSizeBeforeDraw;

        return hasDrawnCard;
    }
}
```

**Sin estándar**
```csharp
public class TurnValidator
{
    private const int HandSizeBeforeDraw = 10;

    public bool CheckDrawCompleted(int heldCardsCount)
    {
        bool drawnCard = heldCardsCount > HandSizeBeforeDraw;

        return drawnCard;
    }
}
```

---

## 2.1.7 — Booleanos con prefijo "can" (Capacidad o permiso)

### Antes
El prefijo can debe utilizarse para variables booleanas que determinen si una entidad tiene la capacidad, el permiso o los requisitos cumplidos para realizar una acción específica.

**Con estándar**
```csharp
bool canDoubleJump;
```

**Sin estándar**
```csharp
bool doubleJump;
```

### Después
El prefijo can debe utilizarse para variables booleanas que determinen si una entidad tiene la capacidad, el permiso o los requisitos cumplidos para realizar una acción específica (Microsoft, 2023).

**Con estándar**
```csharp
public class PlayerTurn
{
    public void DeclareKnock(bool canKnock)
    {
    }
}
```

**Sin estándar**
```csharp
public class PlayerTurn
{
    public void DeclareKnock(bool knock)
    {
    }
}
```

---

## 2.1.8 — Declaración única

### Antes
Se debe declarar estrictamente una sola variable por línea de código para facilitar su lectura y el control de versiones.

**Con estándar**
```csharp
int maxSlots = 5;
int currentSlots = 0;
```

**Sin estándar**
```csharp
int maxSlots = 5, currentSlots = 0;
```

### Después
Se debe declarar estrictamente una sola variable por línea de código para facilitar su lectura y el control de versiones (Microsoft, 2025).

**Con estándar**
```csharp
public class MatchScore
{
    private int _knockerPoints;
    private int _opponentPoints;
}
```

**Sin estándar**
```csharp
public class MatchScore
{
    private int _knockerPoints, _opponentPoints;
}
```

---

## 2.1.10 — Exención de abreviatura para excepciones (`ex`)

### Antes
Como excepción directa a la regla de prohibición de abreviaturas, se permite y estandariza el uso estricto de la variable ex para capturar excepciones, única y exclusivamente dentro de la declaración de los bloques catch. Queda prohibido el uso de otras abreviaturas heredadas de otros lenguajes (como la letra e o err).

**Con estándar**
```csharp
try
{
    ConnectToMultiplayerServer();
}
catch (TimeoutException ex)
{
    RetryConnection();
}
```

**Sin estándar**
```csharp
try
{
       ConnectToMultiplayerServer();
}
catch (TimeoutException e)
{
    RetryConnection();
}
```

### Después
La variable que recibe la excepción en un bloque `catch` se llama siempre `ex`; queda prohibido cualquier otro nombre. Es el nombre que usa Microsoft en sus convenciones de código de C# (Microsoft, 2025).

**Con estándar**
```csharp
public class MatchConnector
{
    public void ConnectToServer()
    {
        try
        {
            OpenTcpConnection();
        }
        catch (SocketException ex)
        {
            throw new InvalidOperationException("The match server is unreachable.", ex);
        }
    }

    private void OpenTcpConnection()
    {
    }
}
```

**Sin estándar**
```csharp
public class MatchConnector
{
    public void ConnectToServer()
    {
        try
        {
            OpenTcpConnection();
        }
        catch (SocketException socketException)
        {
            throw new InvalidOperationException("The match server is unreachable.", socketException);
        }
    }

    private void OpenTcpConnection()
    {
    }
}
```

---

## 2.1.11 — Prefijo estático `s_`

### Antes: Prohibición del prefijo estático "s_"
Los campos estáticos privados o internos usan el mismo prefijo _ que los de instancia. Queda prohibido el prefijo s_.

**Con estándar**
```csharp
private static GameSession _currentSession;
```

**Sin estándar**
```csharp
private static GameSession s_currentSession;
```

### Después: Prefijo estático `s_`
Los campos `static` privados o internos que no son `const` se escriben con el prefijo `s_` seguido de camelCase, para distinguirlos de las variables de instancia (Microsoft, 2026).

**Con estándar**
```csharp
public class MatchLobby
{
    private static int s_activeMatchesCount;
}
```

**Sin estándar**
```csharp
public class MatchLobby
{
    private static int _activeMatchesCount;
}
```

---

## 2.2.1 — Nomenclatura de propiedades

### Antes
Los nombres de las propiedades deben escribirse en PascalCase.

**Con estándar**
```csharp
public class PlayerStats
{
    public int CurrentScore { get; private set; }
}
```

**Sin estándar**
```csharp
public class PlayerStats
{
    public int currentScore { get; private set; }
}
```

### Después
Los nombres de las propiedades deben escribirse en PascalCase (Microsoft, 2023).

**Con estándar**
```csharp
public class GameTable
{
    public int CurrentRound { get; private set; }
}
```

**Sin estándar**
```csharp
public class GameTable
{
    public int currentRound { get; private set; }
}
```

---

## 9.1.3 — Interior del bloque

### Antes
El bloque no debe empezar ni terminar con una línea en blanco, ya que las líneas en blanco se reservan para separar grupos lógicos de código, no para rodear un bloque completo (Microsoft, 2024).

**Con estándar**
```csharp
public class DisconnectHandler
{
    private int _reconnectAttempts;

    public void HandleDisconnect(bool isPlayerConnected)
    {
        if (!isPlayerConnected)
        {
            _reconnectAttempts = 0;
        }
     }
}
```

**Sin estándar**
```csharp
public class DisconnectHandler
{
    private int _reconnectAttempts;

    public void HandleDisconnect(bool isPlayerConnected)
    {
        if (!isPlayerConnected)
        {

            _reconnectAttempts = 0;

        }
    }
}
```

### Después
Ningún bloque de código empieza ni termina con una línea en blanco: no se deja una línea vacía después de una llave de apertura ni antes de una llave de cierre (DotNetAnalyzers, s.f.-a, s.f.-b).

**Con estándar**
```csharp
public class PlayerConnection
{
    public bool IsDisconnected { get; private set; }

    public void HandleDisconnect(bool hasLostConnection)
    {
        if (hasLostConnection)
        {
            IsDisconnected = true;
        }
    }
}
```

**Sin estándar**
```csharp
public class PlayerConnection
{
    public bool IsDisconnected { get; private set; }

    public void HandleDisconnect(bool hasLostConnection)
    {

        if (hasLostConnection)
        {
            IsDisconnected = true;
        }

    }
}
```

---

## 9.1.2 — Obligatoriedad de las llaves

### Antes
El cuerpo de toda estructura de control se delimita con llaves, aunque conste de una sola instrucción, siguiendo la regla de análisis de Microsoft que exige llaves incluso en bloques de una sola línea (Microsoft, s.f.).

**Con estándar**
```csharp
public class DrawPileService
{
    private int _remainingCards;

    public void DrawCard(
        bool isStockEmpty)
    {
        if (isStockEmpty)
        {
            _remainingCards = 0;
        }
    }
}
```

**Sin estándar**
```csharp
public class DrawPileService
{
    private int _remainingCards;

    public void DrawCard(
        bool isStockEmpty)
    {
        if (isStockEmpty)
            _remainingCards = 0;
    }
}
```

### Después
El cuerpo de toda estructura de control se delimita con llaves, aunque conste de una sola instrucción, siguiendo la regla de análisis de Microsoft que prefiere llaves incluso en bloques de una sola línea (Microsoft, 2023).

**Con estándar**
```csharp
public class DiscardPile
{
    public bool IsEmpty { get; private set; }

    public void ClearPile(bool isRoundOver)
    {
        if (isRoundOver)
        {
            IsEmpty = true;
        }
    }
}
```

**Sin estándar**
```csharp
public class DiscardPile
{
    public bool IsEmpty { get; private set; }

    public void ClearPile(bool isRoundOver)
    {
        if (isRoundOver)
            IsEmpty = true;
    }
}
```

---

## 9.1.1 — Estilo de llaves (Allman)

### Antes
Se usa el estilo Allman: la llave de apertura y la de cierre ocupan cada una su propia línea, al nivel de indentación de la sentencia que las abre, siguiendo la convención oficial de C# de Microsoft (Microsoft, s.f.).

**Con estándar**
```csharp
public class MatchSession
{
    private int _reconnectAttempts;

    public void ResetReconnectAttempts(
        bool isPlayerConnected)
    {
        if (isPlayerConnected)
        {
            _reconnectAttempts = 0;
        }
    }
}
```

**Sin estándar**
```csharp
public class MatchSession
{
    private int _reconnectAttempts;

    public void ResetReconnectAttempts(
        bool isPlayerConnected)
    {
        if (isPlayerConnected) {
            _reconnectAttempts = 0;
        }
    }
}
```

### Después
Cada llave `{` y `}` va en su propia línea, alineada con la línea que la abre, aunque entre ellas haya una sola instrucción (Microsoft, 2025a). Las únicas excepciones son los accesores (regla 9.1.4), los inicializadores (reglas 9.1.5 a 9.1.8) y las llaves dentro de un texto, que no son código: `$"Player {playerName}"`.

**Con estándar**
```csharp
public class GameRound
{
    public bool IsLastRound { get; private set; }

    public void FinishRound(bool hasKnocked)
    {
        if (hasKnocked)
        {
            IsLastRound = true;
        }
    }
}
```

**Sin estándar**
```csharp
public class GameRound {
    public bool IsLastRound { get; private set; }

    public void FinishRound(bool hasKnocked) {
        if (hasKnocked) {
            IsLastRound = true;
        }
    }
}
```

---

## 9.2.1 — Agrupación de las cláusulas

### Antes
Las cláusulas de una condición compuesta se agrupan con paréntesis explícitos alrededor de cada comparación relacional, siguiendo la regla de estilo de Microsoft que prefiere paréntesis para aclarar la precedencia entre operadores relacionales y lógicos (Microsoft, s.f.).

**Con estándar**
```csharp
public class ReconnectValidator
{
    public bool CanReconnect(int disconnectCount, int elapsedSeconds)
    {
        return (disconnectCount < 3) && (elapsedSeconds <= 60);
    }
}
```

**Sin estándar**
```csharp
public class ReconnectValidator
{
    public bool CanReconnect(int disconnectCount, int elapsedSeconds)
    {
        return disconnectCount < 3 && elapsedSeconds <= 60;
    }
}
```

### Después
En una expresión que une comparaciones con `&&` o `||`, cada comparación va entre paréntesis, para que el orden en que se evalúan los operadores quede claro (Microsoft, 2022). Una comparación es una expresión con `==`, `!=`, `<`, `>`, `<=`, `>=` o `is`.

**Con estándar**
```csharp
public class ReconnectValidator
{
    private const int MaxDisconnects = 3;
    private const int MaxWaitSeconds = 60;

    public bool CanReconnect(int disconnectCount, int elapsedSeconds)
    {
        return (disconnectCount < MaxDisconnects) && (elapsedSeconds <= MaxWaitSeconds);
    }
}
```

**Sin estándar**
```csharp
public class ReconnectValidator
{
    private const int MaxDisconnects = 3;
    private const int MaxWaitSeconds = 60;

    public bool CanReconnect(int disconnectCount, int elapsedSeconds)
    {
        return disconnectCount < MaxDisconnects && elapsedSeconds <= MaxWaitSeconds;
    }
}
```

---

## 9.2.2 — Prohibición de comparar con literales booleanos

### Antes
Un booleano no anulable se evalúa directamente. Queda prohibido compararlo con true o con false.

### Después
Un booleano no anulable se evalúa directamente: queda prohibido compararlo con `true` o con `false`, porque esa comparación es innecesaria (Microsoft, 2023).

**Ejemplos (sin cambios respecto al estándar base)**

**Con estándar**
```csharp
public class ConnectionMonitor
{
    private bool _isPlayerConnected;
    private int _timeoutSeconds;

    public void CheckConnection()
    {
        if (_isPlayerConnected)
        {
            _timeoutSeconds = 0;
        }
    }
}
```

**Sin estándar**
```csharp
public class ConnectionMonitor
{
    private bool _isPlayerConnected;
    private int _timeoutSeconds;

    public void CheckConnection()
    {
        if (_isPlayerConnected == true)
        {
            _timeoutSeconds = 0;
        }
    }
}
```

---

## 9.3.1 — Ámbito de la variable de control

### Antes
La variable de control del bucle for se debe declarar e inicializar en la propia cabecera del bucle, minimizando su alcance para evitar que quede accesible fuera del bloque que la usa (Software Engineering Institute, s.f.).

### Después
La variable de control del bucle for se debe declarar e inicializar en la propia cabecera del bucle, minimizando su alcance para evitar que quede accesible fuera del bloque que la usa (Microsoft, 2026c).

**Ejemplos sin cambios respecto al estándar base.**

---

## 9.3.3 — Prohibición de modificar la colección recorrida

### Antes
Queda prohibido agregar o eliminar elementos de una colección dentro de un foreach que la recorre, ya que modificarla invalida el enumerador y provoca una excepción InvalidOperationException en tiempo de ejecución (Microsoft, s.f.).

**Con estándar**
```csharp
public class LobbyManager
{
    private List<Player> _connectedPlayers;

    public void RemoveDisconnected()
    {
        for (int i = _connectedPlayers.Count - 1; i >= 0; i--)
        {
            if (_connectedPlayers[i].IsDisconnected)
            {
                _connectedPlayers.RemoveAt(i);
            }
        }
    }
}
```

**Sin estándar**
```csharp
public class LobbyManager
{
    private List<Player> _connectedPlayers;

    public void RemoveDisconnected()
    {
        foreach (Player player in _connectedPlayers)
        {
            if (player.IsDisconnected)
            {
                _connectedPlayers.Remove(player);
            }
        }
    }
}
```

### Después
Queda prohibido agregar o eliminar elementos de una colección dentro de un foreach que la recorre, ya que modificarla invalida el enumerador y provoca una excepción InvalidOperationException en tiempo de ejecución (Microsoft, 2025c).

**Con estándar**
```csharp
public class LobbyRoster
{
    private List<Player> _connectedPlayers;

    public void RemoveDisconnected()
    {
        for (int i = _connectedPlayers.Count - 1; i >= 0; i--)
        {
            if (_connectedPlayers[i].IsDisconnected)
            {
                _connectedPlayers.RemoveAt(i);
            }
        }
    }
}
```

**Sin estándar**
```csharp
public class LobbyRoster
{
    private List<Player> _connectedPlayers;

    public void RemoveDisconnected()
    {
        foreach (Player player in _connectedPlayers)
        {
            if (player.IsDisconnected)
            {
                _connectedPlayers.Remove(player);
            }
        }
    }
}
```

---

## 9.3.5 — Condición de salida en la cabecera

### Antes
La condición que termina el bucle se declara en su cabecera; queda prohibido el bucle infinito interrumpido desde dentro, salvo en bucles de escucha de conexiones destinados a ejecutarse durante toda la vida del proceso del servidor, patrón que la propia documentación de Microsoft utiliza para TcpListener.AcceptTcpClient (Microsoft, s.f.).

### Después
Mismo texto; la cita (Microsoft, s.f.) ahora remite a la página verificada de la clase `TcpListener`. **Ejemplos sin cambios respecto al estándar base.**

---

## 9.3.2 — Recorrido de colecciones

### Antes
Cuando se recorre una colección completa y no se necesita el índice, se usa foreach, ya que es el ciclo recomendado para lectura de colecciones al no requerir gestión manual de índices ni exponerse a errores de desbordamiento (Microsoft, s.f.).

### Después
Cuando se recorre una colección completa y no se necesita el índice, se usa foreach, ya que simplifica el código al no requerir la variable del índice (Microsoft, 2026d).

**Ejemplos sin cambios respecto al estándar base.**
