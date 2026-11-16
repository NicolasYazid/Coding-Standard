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
public class MatchSession
{
    private bool _isPaused;

    public void PauseMatch()
    {
        _isPaused = true;
    }
}
```

**Sin estándar**
```csharp
public class MatchSession
{
    private bool _paused;

    public void PauseMatch()
    {
        _paused = true;
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
public class PlayerTurn
{
    private bool _hasDrawnCard;

    public void DrawCard()
    {
        _hasDrawnCard = true;
    }
}
```

**Sin estándar**
```csharp
public class PlayerTurn
{
    private bool _drawnCard;

    public void DrawCard()
    {
        _drawnCard = true;
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
public class KnockValidator
{
    private const int MaxKnockDeadwood = 10;

    public bool CheckKnockAvailability(int deadwoodPoints)
    {
        bool canKnock = deadwoodPoints <= MaxKnockDeadwood;

        return canKnock;
    }
}
```

**Sin estándar**
```csharp
public class KnockValidator
{
    private const int MaxKnockDeadwood = 10;

    public bool CheckKnockAvailability(int deadwoodPoints)
    {
        bool knock = deadwoodPoints <= MaxKnockDeadwood;

        return knock;
    }
}
```
