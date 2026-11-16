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
