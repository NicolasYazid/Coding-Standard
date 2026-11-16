# 🆕 Reglas nuevas

> Reglas que **no existían** en el estándar base (118 páginas) y se agregaron al estándar definitivo.
> Índice de reglas: [README.md](README.md).

---

## 2.2.6 — Set restringido

**Origen:** separada de la regla "Declaración correcta de propiedades" del estándar base, que mezclaba varios temas y ya pedía restringir el `set`.

El `set` de una propiedad se declara `private` cuando su valor solo se asigna dentro de la propia clase. Solo se declara público cuando el diseño requiere que otra clase asigne el valor. Así se evita que otra clase cambie un valor que no le corresponde (Microsoft, 2023).

**Con estándar**
```csharp
public class PlayerTurn
{
    public bool HasKnocked { get; private set; }

    public void DeclareKnock()
    {
        HasKnocked = true;
    }
}
```

**Sin estándar**
```csharp
public class PlayerTurn
{
    public bool HasKnocked { get; set; }

    public void DeclareKnock()
    {
        HasKnocked = true;
    }
}
```

---

## 9.1.4 — Formato de los accesores

**Origen:** separada de la regla 9.1.1 para que cada regla trate un solo tema; el estándar base no decía cómo escribir los accesores.

Las auto-propiedades se escriben en una sola línea: `{ get; private set; }`. Un `get` o `set` con una sola instrucción va en una sola línea: `get { return _totalScore; }`. Si tiene dos o más instrucciones, cada llave va en su propia línea. Visual Studio conserva por defecto los bloques escritos en una sola línea (Microsoft, 2025b).

**Con estándar**
```csharp
public class PlayerScore
{
    private const int MinimumScore = 0;
    private int _totalScore;

    public int TotalScore
    {
        get { return _totalScore; }
        private set
        {
            int validScore = Math.Max(MinimumScore, value);
            _totalScore = validScore;
        }
    }
}
```

**Sin estándar**
```csharp
public class PlayerScore
{
    private const int MinimumScore = 0;
    private int _totalScore;

    public int TotalScore
    {
        get
        {
            return _totalScore;
        }
        private set
        {
            int validScore = Math.Max(MinimumScore, value);
            _totalScore = validScore;
        }
    }
}
```

---

## 9.1.7 — Formato de los tipos anónimos

**Origen:** el estándar base no decía cómo escribir los tipos anónimos; surgió al definir las excepciones de la regla 9.1.1.

Un tipo anónimo con un solo miembro va en una sola línea. Si tiene dos o más miembros, cada llave y cada miembro van en su propia línea, que es el formato predeterminado de Visual Studio para los tipos anónimos (Microsoft, 2025b).

**Con estándar**
```csharp
public class RankingQuery
{
    public object CreatePlayerKey(PlayerProfile profile)
    {
        object playerKey = new
        {
            profile.PlayerAccountId,
            profile.Username
        };

        return playerKey;
    }
}
```

**Sin estándar**
```csharp
public class RankingQuery
{
    public object CreatePlayerKey(PlayerProfile profile)
    {
        object playerKey = new { profile.PlayerAccountId, profile.Username };

        return playerKey;
    }
}
```

---

## 9.1.6 — Formato de los inicializadores de colección

**Origen:** el estándar base no decía cómo escribir los inicializadores de colección; surgió al definir las excepciones de la regla 9.1.1.

Un inicializador de colección cuyos elementos son valores simples (variables, constantes o literales) va en una sola línea. Si sus elementos son objetos creados con `new`, cada llave y cada elemento van en su propia línea, como en los ejemplos de Microsoft (Microsoft, 2026a).

**Con estándar**
```csharp
public class MatchSetup
{
    public void PrepareTable(string hostName, string guestName)
    {
        List<string> playerNames = new List<string> { hostName, guestName };
        List<Card> aceCards = new List<Card>
        {
            new Card(Suit.Hearts, CardRank.Ace),
            new Card(Suit.Spades, CardRank.Ace)
        };
    }
}
```

**Sin estándar**
```csharp
public class MatchSetup
{
    public void PrepareTable(string hostName, string guestName)
    {
        List<string> playerNames = new List<string>
        {
            hostName,
            guestName
        };
        List<Card> aceCards = new List<Card> { new Card(Suit.Hearts, CardRank.Ace), new Card(Suit.Spades, CardRank.Ace) };
    }
}
```
