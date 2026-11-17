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

---

## 9.4.1 — Elección del switch

### Antes
Cuando un mismo valor se compara contra varias constantes, se usa switch en lugar de una cadena de else if, ya que un switch se lee con más claridad que una cadena larga de else if al comparar un solo valor contra varios casos discretos (Microsoft, s.f.).

El ejemplo con estándar contenía la línea `End Round();`, que no compila.

### Después
Cuando un mismo valor se compara contra dos o más constantes, se usa switch en lugar de una cadena de else if, ya que un switch se lee con más claridad que una cadena larga de else if al comparar un solo valor contra varios casos discretos (Microsoft, s.f.-a).

**Con estándar**
```csharp
public class MatchStateHandler
{
    public void ProcessState(MatchState currentState)
    {
        switch (currentState)
        {
            case MatchState.Dealing:
                DealCards();
                break;
            case MatchState.PlayerTurn:
                WaitForMove();
                break;
            default:
                EndRound();
                break;
        }
    }

    private void DealCards()
    {
    }

    private void WaitForMove()
    {
    }

    private void EndRound()
    {
    }
}
```

---

## 9.4.2 — Uso de llaves en el cuerpo de un case

### Antes
Un case no requiere llaves propias por defecto, ya que es una etiqueta dentro del bloque único del switch, no una estructura de control independiente. Sin embargo, si un case declara una variable local, su cuerpo debe envolverse obligatoriamente en llaves, ya que sin ellas la variable comparte el ámbito de todo el switch y provoca el error de compilación CS0136 si otro case declara una variable con el mismo nombre (Microsoft, s.f.).

Los ejemplos usaban números sueltos (10 y 0), no tenían default y el ejemplo sin estándar no compilaba.

### Después
Un case no requiere llaves propias por defecto, ya que es una etiqueta dentro del bloque único del switch, no una estructura de control independiente. Sin embargo, si un case declara una variable local, su cuerpo debe envolverse obligatoriamente en llaves, ya que sin ellas la variable comparte el ámbito de todo el switch y provoca un error de compilación si otro case declara una variable con el mismo nombre (Microsoft, s.f.-b).

**Con estándar**
```csharp
public class MatchStateHandler
{
    private const int InitialHandSize = 10;

    public void ProcessState(MatchState currentState)
    {
        switch (currentState)
        {
            case MatchState.Dealing:
            {
                int cardsToDeal = InitialHandSize;
                DealCards(cardsToDeal);
                break;
            }
            default:
                WaitForMove();
                break;
        }
    }

    private void DealCards(int cardsToDeal)
    {
    }

    private void WaitForMove()
    {
    }
}
```

**Sin estándar**
```csharp
public class MatchStateHandler
{
    private const int InitialHandSize = 10;

    public void ProcessState(MatchState currentState)
    {
        switch (currentState)
        {
            case MatchState.Dealing:
                int cardsToDeal = InitialHandSize;
                DealCards(cardsToDeal);
                break;
            default:
                WaitForMove();
                break;
        }
    }

    private void DealCards(int cardsToDeal)
    {
    }

    private void WaitForMove()
    {
    }
}
```

---

## 9.4.4 — Agrupación de etiquetas

### Antes / Después
Mismo texto; la cita (Microsoft, s.f.) pasa a (Microsoft, 2026e), con la página verificada. **Ejemplos sin cambios.**

---

## 9.4.5 — Cuerpo de la sección

### Antes / Después
Mismo texto. El ejemplo sin estándar tenía el número suelto `30`; ahora usa una constante.

**Sin estándar**
```csharp
public class TurnStateHandler
{
    private const int MaxTurnSeconds = 30;
    private int _turnTimer;

    public void Handle(TurnState currentState)
    {
        switch (currentState)
        {
            case TurnState.PlayerTurn:
                _turnTimer++;
                if (_turnTimer > MaxTurnSeconds)
                {
                    _turnTimer = 0;
                }
                break;
            default:
                _turnTimer = 0;
                break;
        }
    }
}
```

---

## 9.4.3 — Cláusula default obligatoria

### Antes
Todo switch incluye una cláusula default, ya que sin ella el control simplemente atraviesa la sentencia sin ejecutar nada cuando ningún caso coincide, dejando el valor no contemplado sin manejo alguno (Microsoft, s.f.).

**Con estándar**
```csharp
public class MessageDispatcher
{
    public void Dispatch(NetworkMessageType messageType)
    {
        switch (messageType)
        {
            case NetworkMessageType.Draw:
                ProcessDraw();
                break;
            case NetworkMessageType.Discard:
                ProcessDiscard();
                break;
            default:
                RejectMessage();
                break;
        }
    }

    private void ProcessDraw()
    {
    }

    private void ProcessDiscard()
    {
    }

    private void RejectMessage()
    {
    }
}
```

**Sin estándar**
```csharp
public class MessageDispatcher
{
    public void Dispatch(NetworkMessageType messageType)
    {
        switch (messageType)
        {
            case NetworkMessageType.Draw:
                ProcessDraw();
                break;
            case NetworkMessageType.Discard:
                ProcessDiscard();
                break;
        }
    }

    private void ProcessDraw()
    {
    }

    private void ProcessDiscard()
    {
    }
}
```

### Después
Todo switch incluye una cláusula default, porque sin ella, cuando ningún caso coincide, el switch no hace nada (Microsoft, 2026e). El default se encarga de los valores que no tienen su propio case: si esos valores necesitan una acción, el default la ejecuta; si no necesitan ninguna, el default contiene solo `break;`.

**Con estándar**
```csharp
public class MessageDispatcher
{
    public void Dispatch(NetworkMessageType messageType)
    {
        switch (messageType)
        {
            case NetworkMessageType.Draw:
                ProcessDraw();
                break;
            case NetworkMessageType.Discard:
                ProcessDiscard();
                break;
            default:
                RejectMessage();
                break;
        }
    }

    public void DispatchTurnMessage(NetworkMessageType messageType)
    {
        switch (messageType)
        {
            case NetworkMessageType.Draw:
                ProcessDraw();
                break;
            default:
                break;
        }
    }

    private void ProcessDraw()
    {
    }

    private void ProcessDiscard()
    {
    }

    private void RejectMessage()
    {
    }
}
```

**Sin estándar**
```csharp
public class MessageDispatcher
{
    public void Dispatch(NetworkMessageType messageType)
    {
        switch (messageType)
        {
            case NetworkMessageType.Draw:
                ProcessDraw();
                break;
            case NetworkMessageType.Discard:
                ProcessDiscard();
                break;
        }
    }

    private void ProcessDraw()
    {
    }

    private void ProcessDiscard()
    {
    }
}
```

---

## 9.5.1 — Ámbito de uso

### Antes
El operador ternario se usa únicamente para calcular un valor. Queda prohibido emplearlo para ejecutar acciones.

**Con estándar**
```csharp
int appliedDamage = _isShieldActive ? 0 : _incomingDamage;
```

**Sin estándar**
```csharp
_ = _isShieldActive ? BlockDamage() : ApplyDamage();
```

### Después
El operador ternario solo se usa para calcular un valor que el código utiliza (Microsoft, 2026f). Queda prohibido descartar su resultado con `_ =` para que solo se ejecute el método de la rama elegida.

**Con estándar**
```csharp
public class RoundScorer
{
    private const int GinBonus = 25;
    private bool _isGin;
    private int _totalScore;

    public void AddRoundPoints(int deadwoodDifference)
    {
        _totalScore += _isGin ? GinBonus : deadwoodDifference;
    }
}
```

**Sin estándar**
```csharp
public class RoundScorer
{
    private const int GinBonus = 25;
    private bool _isGin;
    private int _totalScore;

    public void AddRoundPoints(int deadwoodDifference)
    {
        _ = _isGin ? AddGinBonus() : AddDeadwood(deadwoodDifference);
    }

    private int AddGinBonus()
    {
        _totalScore += GinBonus;

        return _totalScore;
    }

    private int AddDeadwood(int deadwoodDifference)
    {
        _totalScore += deadwoodDifference;

        return _totalScore;
    }
}
```

---

## 9.5.2 — Prohibición del ternario anidado

### Antes
Queda prohibido anidar un operador ternario dentro de otro.

**Con estándar**
```csharp
int bonusPoints = _isPerfectRun ? PerfectBonus : GetSecondaryBonus();
```

**Sin estándar**
```csharp
int bonusPoints = _isPerfectRun ? PerfectBonus : _hasAllCollectibles ? CollectibleBonus : 0;
```

### Después
Queda prohibido escribir un ternario dentro de otro, porque dificulta saber qué valor resulta (DeepSource, s.f.). Si hay que elegir entre más de dos valores, cada ternario guarda su resultado en su propia variable.

**Con estándar**
```csharp
public class GinBonusCalculator
{
    private const int BigGinBonus = 31;
    private const int GinBonus = 25;
    private const int NoBonus = 0;
    private bool _isBigGin;
    private bool _isGin;

    public int CalculateBonus()
    {
        int ginBonus = _isGin ? GinBonus : NoBonus;
        int bonusPoints = _isBigGin ? BigGinBonus : ginBonus;

        return bonusPoints;
    }
}
```

**Sin estándar**
```csharp
public class GinBonusCalculator
{
    private const int BigGinBonus = 31;
    private const int GinBonus = 25;
    private const int NoBonus = 0;
    private bool _isBigGin;
    private bool _isGin;

    public int CalculateBonus()
    {
        int bonusPoints = _isBigGin ? BigGinBonus : _isGin ? GinBonus : NoBonus;

        return bonusPoints;
    }
}
```

---

## 9.5.4 — Extensión del ternario

### Antes
El ternario debe caber en una sola línea. Si no cabe, se sustituye por una sentencia condicional.

**Con estándar**
```csharp
float appliedGravity = _isFalling ? FallGravity : BaseGravity;
```

**Sin estándar**
```csharp
float appliedGravity = _isFalling
    ? FallGravity
    : BaseGravity;
```

### Después
Un ternario se escribe en una sola línea si cabe en el límite de 140 caracteres (regla 4.1.2). Si no cabe, se parte en tres líneas: la condición, una línea que empieza con `?` y una línea que empieza con `:`; estas dos últimas llevan 4 espacios más de sangría (Microsoft, 2025d).

**Con estándar**
```csharp
public class RoundScorer
{
    private const int GinBonus = 25;
    private const int NoBonus = 0;
    private const int UndercutBonus = 25;

    public int CalculateBonusPoints(bool isGin)
    {
        int bonusPoints = isGin ? GinBonus : NoBonus;

        return bonusPoints;
    }

    public int CalculateRoundPoints(bool isUndercut, int knockerDeadwoodPoints, int opponentDeadwoodPoints)
    {
        int roundPoints = isUndercut
            ? knockerDeadwoodPoints - opponentDeadwoodPoints + UndercutBonus
            : opponentDeadwoodPoints - knockerDeadwoodPoints;

        return roundPoints;
    }
}
```

**Sin estándar**
```csharp
public class RoundScorer
{
    private const int UndercutBonus = 25;

    public int CalculateRoundPoints(bool isUndercut, int knockerDeadwoodPoints, int opponentDeadwoodPoints)
    {
        int roundPoints = isUndercut ?
            knockerDeadwoodPoints - opponentDeadwoodPoints + UndercutBonus :
            opponentDeadwoodPoints - knockerDeadwoodPoints;

        return roundPoints;
    }
}
```

---

## 9.5.3 — Ramas booleanas explícitas (antes: Prohibición de literales booleanos)

### Antes
Queda prohibido el ternario cuyas ramas son true y false. La condición se asigna directamente.

**Con estándar**
```csharp
bool canOpenGate = _hasGateKey && _isGateReachable;
```

**Sin estándar**
```csharp
bool canOpenGate = _hasGateKey && _isGateReachable ? true : false;
```

### Después
Las ramas `true` y `false` de un ternario se escriben de forma explícita, para que se vea qué valor resulta en cada caso (Microsoft, 2022b). Queda prohibido omitirlas y dejar solo la condición.

**Con estándar**
```csharp
public class TurnValidator
{
    public bool CheckKnockAllowed(bool hasDrawnCard, bool isDeadwoodInRange)
    {
        bool canKnock = hasDrawnCard && isDeadwoodInRange ? true : false;

        return canKnock;
    }

    public bool CheckRoundOver(bool hasKnocked, bool isStockEmpty)
    {
        bool isRoundOver = hasKnocked || isStockEmpty ? true : false;

        return isRoundOver;
    }
}
```

**Sin estándar**
```csharp
public class TurnValidator
{
    public bool CheckKnockAllowed(bool hasDrawnCard, bool isDeadwoodInRange)
    {
        bool canKnock = hasDrawnCard && isDeadwoodInRange;

        return canKnock;
    }

    public bool CheckRoundOver(bool hasKnocked, bool isStockEmpty)
    {
        bool isRoundOver = hasKnocked || isStockEmpty;

        return isRoundOver;
    }
}
```

---

## 2.5.1 — Nomenclatura (PascalCase)

### Antes
Para asegurar la compatibilidad directa con las herramientas de análisis de código del ecosistema .NET, los nombres de todas las constantes deben definirse utilizando estrictamente el formato PascalCase. Queda obsoleto el formato UPPER_SNAKE_CASE utilizado en versiones anteriores.

**Con estándar**
```csharp
public const int MaxPlayerLives = 3;
```

**Sin estándar**
```csharp
public const int MAX_PLAYER_LIVES = 3;
```

### Después
Los nombres de las constantes (`const`) se escriben en PascalCase, tanto en los campos como en las constantes locales y con cualquier nivel de acceso (`public`, `private` o `internal`). Queda prohibido el formato UPPER_SNAKE_CASE (Microsoft, 2026).

**Con estándar**
```csharp
public class ScoreBoard
{
    private const int WinningScore = 100;

    public int CalculateFinalScore(int playerScore)
    {
        const int GameBonus = 100;
        int finalScore = playerScore;

        if (playerScore >= WinningScore)
        {
            finalScore += GameBonus;
        }

        return finalScore;
    }
}
```

**Sin estándar**
```csharp
public class ScoreBoard
{
    private const int WINNING_SCORE = 100;

    public int CalculateFinalScore(int playerScore)
    {
        const int GAME_BONUS = 100;
        int finalScore = playerScore;

        if (playerScore >= WINNING_SCORE)
        {
            finalScore += GAME_BONUS;
        }

        return finalScore;
    }
}
```

---

## 2.5.2 — Uso de const (antes: Inmutabilidad en tiempo de compilación)

### Antes
El modificador const se utilizará única y exclusivamente para valores estáticos que jamás cambiarán y que se conocen por completo en tiempo de compilación (como números base o nombres por defecto).

**Con estándar**
```csharp
public const float BaseGravity = -9.81f;
```

**Sin estándar**
```csharp
public float BaseGravity = -9.81f;
```

### Después
Un campo que recibe en su declaración un valor escrito directamente en el código (un número, un texto, un carácter, `true` o `false`) y al que nunca se le asigna otro valor se declara `const` (Microsoft, 2023; Microsoft, 2026g). Queda prohibido declararlo como campo modificable o como `static readonly`.

**Con estándar**
```csharp
public class GameRules
{
    private const int MaxKnockDeadwood = 10;
    private const string DefaultPlayerName = "Guest";
    private const char CardSeparator = ',';
    private const bool IsBigGinAllowed = true;
}
```

**Sin estándar**
```csharp
public class GameRules
{
    private int _maxKnockDeadwood = 10;
    private string _defaultPlayerName = "Guest";
    private static readonly char s_cardSeparator = ',';
    private bool _isBigGinAllowed = true;
}
```

---

## 2.5.3 — Uso de static readonly (antes: Inmutabilidad en tiempo de ejecución)

### Antes
Cuando un valor no debe ser modificado tras su inicialización, pero requiere ser calculado en tiempo de ejecución o se trata de una instancia de un objeto complejo (tipos de referencia), se debe utilizar obligatoriamente static readonly.

**Con estándar**
```csharp
public static readonly Vector2 DefaultRespawnPoint = new Vector2(0f, 5f);
```

**Sin estándar**
```csharp
public const Vector2 DefaultRespawnPoint = new Vector2(0f, 5f);
```

### Después
Un campo `static` al que nunca se le asigna otro valor después de su declaración, y que no puede ser `const` porque su valor se calcula al ejecutar el programa o es un objeto creado con `new`, se declara `static readonly` (Microsoft, 2023; Microsoft, 2026g). Queda prohibido declararlo `static` sin `readonly`.

**Con estándar**
```csharp
public class PlayerNameValidator
{
    private const int TurnTimeLimitSeconds = 30;
    private const string UsernamePattern = "^[a-zA-Z0-9]+$";
    private static readonly TimeSpan s_turnTimeLimit = TimeSpan.FromSeconds(TurnTimeLimitSeconds);
    private static readonly Regex s_usernameRegex = new Regex(UsernamePattern);
}
```

**Sin estándar**
```csharp
public class PlayerNameValidator
{
    private const int TurnTimeLimitSeconds = 30;
    private const string UsernamePattern = "^[a-zA-Z0-9]+$";
    private static TimeSpan s_turnTimeLimit = TimeSpan.FromSeconds(TurnTimeLimitSeconds);
    private static Regex s_usernameRegex = new Regex(UsernamePattern);
}
```

---

## 2.6.1 — Nomenclatura (PascalCase)

### Antes
Los nombres de los métodos deben definirse utilizando estrictamente el formato PascalCase (la primera letra de cada palabra en mayúscula), alineándose con las convenciones oficiales de Microsoft para C#.

**Con estándar**
```csharp
public void CalculateScore()
{
}
```

**Sin estándar**
```csharp
public void calculateScore()
{
}
```

### Después
Los nombres de los métodos deben definirse utilizando estrictamente el formato PascalCase, con la primera letra de cada palabra en mayúscula (Microsoft, 2026).

**Con estándar**
```csharp
public class ScoreCalculator
{
    public void CalculateScore()
    {
    }
}
```

**Sin estándar**
```csharp
public class ScoreCalculator
{
    public void calculateScore()
    {
    }
}
```

---

## 2.6.2 — Verbos o frases verbales

### Antes
Los nombres de los métodos deberán ser obligatoriamente verbos o frases verbales que describan con precisión la acción que ejecutan. Queda prohibido el uso de sustantivos estáticos para nombrar una acción.

**Con estándar**
```csharp
public void SpawnEnemy()
{
}
```

**Sin estándar**
```csharp
public void Enemy()
{
}
```

### Después
Los nombres de los métodos deberán ser obligatoriamente verbos o frases verbales que empiecen con el verbo y describan con precisión la acción que ejecutan (Microsoft, 2023). Queda prohibido el uso de sustantivos para nombrar una acción. Quedan fuera los constructores y el método `Main`, porque C# les impone su nombre.

**Con estándar**
```csharp
public class GameRound
{
    public GameRound()
    {
    }

    public void DealCards()
    {
    }
}
```

**Sin estándar**
```csharp
public class GameRound
{
    public GameRound()
    {
    }

    public void Cards()
    {
    }
}
```

---

## 2.6.3 — Límite de parámetros

### Antes
Para evitar firmas excesivamente complejas y mantener el código claro, los métodos deberán recibir como máximo tres parámetros. Si un método requiere una mayor cantidad de datos de entrada, se debe refactorizar utilizando un objeto de transferencia de datos (DTO) o una estructura que encapsule dicha información.

**Con estándar**
```csharp
public void MovePlayer(float speed, float directionX, bool isDashing)
{
}
```

**Sin estándar**
```csharp
public void MovePlayer(float speed, float directionX, bool isDashing, float jumpForce)
{
}
```

### Después
Un método o constructor recibe como máximo tres parámetros, para que su firma sea clara (SonarSource, s.f.). Si necesita más datos, se pueden agrupar en una clase y el método recibe esa clase. Quedan fuera los métodos que implementan una interfaz de .NET, porque su firma la define .NET.

**Con estándar**
```csharp
public class MatchHistory
{
    public void RegisterKnock(int knockerId, int deadwoodPoints, bool isGin)
    {
    }

    public void RegisterRoundResult(RoundResult roundResult)
    {
    }
}
```

**Sin estándar**
```csharp
public class MatchHistory
{
    public void RegisterRoundResult(int winnerId, int loserId, int deadwoodDifference, bool isGin)
    {
    }
}
```

---

## 2.7.1 — Prefijo On (antes: reacción a eventos del sistema; ahora: método que lanza un evento)

### Antes
El prefijo On debe utilizarse obligatoriamente cuando el método reacciona a un evento emitido por el sistema. Implica que la acción ya sucedió y el objeto está reaccionando a ella.

**Con estándar**
```csharp
public void OnPlayerDeath(int finalScore)
{
}
```

**Sin estándar**
```csharp
public void HandlePlayerDeath(int finalScore)
{
}
```

### Después
El método que solo se encarga de avisar que ocurrió un evento se llama `On` seguido del nombre del evento, por ejemplo `OnOpponentDisconnected` (Microsoft, 2026h). Este nombre no empieza con un verbo, y es el único método al que se le permite, a diferencia de lo que pide la regla 2.6.2.

**Con estándar**
```csharp
public class GameTable
{
    public event EventHandler OpponentDisconnected;

    protected virtual void OnOpponentDisconnected()
    {
        OpponentDisconnected?.Invoke(this, EventArgs.Empty);
    }
}
```

**Sin estándar**
```csharp
public class GameTable
{
    public event EventHandler OpponentDisconnected;

    protected virtual void NotifyOpponentDisconnected()
    {
        OpponentDisconnected?.Invoke(this, EventArgs.Empty);
    }
}
```

---

## 2.7.2 — Prefijo Handle (antes: procesamiento de entradas; ahora: método que reacciona a un evento)

### Antes
El prefijo Handle debe utilizarse cuando el método procesa directamente una entrada (input) del jugador o un comando lógico que requiere evaluación inmediata en el juego.

**Con estándar**
```csharp
public void HandleJump(float jumpForce)
{
}
```

**Sin estándar**
```csharp
public void Jump(float jumpForce)
{
}
```

### Después
El método que reacciona cuando otro método avisa que ocurrió un evento empieza con `Handle`, por ejemplo `HandleOpponentDisconnected` (Microsoft, 2021). El prefijo `Handle` no es exclusivo de estos métodos: cualquier otro método puede usarlo si describe lo que hace.

**Con estándar**
```csharp
public class GameTableViewModel
{
    public GameTableViewModel(GameTable gameTable)
    {
        gameTable.OpponentDisconnected += HandleOpponentDisconnected;
    }

    private void HandleOpponentDisconnected(object sender, EventArgs e)
    {
    }

    private void HandleCardSelection(Card selectedCard)
    {
    }
}
```

**Sin estándar**
```csharp
public class GameTableViewModel
{
    public GameTableViewModel(GameTable gameTable)
    {
        gameTable.OpponentDisconnected += OnOpponentDisconnected;
    }

    private void OnOpponentDisconnected(object sender, EventArgs e)
    {
    }
}
```

---

## 2.7.3 — Prefijo Toggle (alternancia de estados booleanos)

### Antes
El prefijo Toggle debe utilizarse exclusivamente cuando la única responsabilidad del manejador sea alternar el estado lógico (verdadero o falso) de un componente o mecánica del juego.

**Con estándar**
```csharp
public void ToggleGodMode()
{
}
```

**Sin estándar**
```csharp
public void ChangeGodModeState()
{
}
```

### Después
El prefijo `Toggle` se usa solo en los métodos que no hacen nada más que cambiar un `bool` a su valor contrario (de `true` a `false`, o de `false` a `true`). Todo método así empieza con `Toggle` seguido de lo que cambia, por ejemplo `ToggleChatFilter` (Microsoft, 2025e).

**Con estándar**
```csharp
public class ChatSettings
{
    private bool _isChatFilterEnabled;
    private bool _isSoundEnabled;
    private int _soundChangesCount;

    public void ToggleChatFilter()
    {
        _isChatFilterEnabled = !_isChatFilterEnabled;
    }

    public void ChangeSoundSetting()
    {
        _isSoundEnabled = !_isSoundEnabled;
        _soundChangesCount++;
    }
}
```

**Sin estándar**
```csharp
public class ChatSettings
{
    private bool _isChatFilterEnabled;
    private bool _isSoundEnabled;
    private int _soundChangesCount;

    public void ChangeChatFilterState()
    {
        _isChatFilterEnabled = !_isChatFilterEnabled;
    }

    public void ToggleSound()
    {
        _isSoundEnabled = !_isSoundEnabled;
        _soundChangesCount++;
    }
}
```
