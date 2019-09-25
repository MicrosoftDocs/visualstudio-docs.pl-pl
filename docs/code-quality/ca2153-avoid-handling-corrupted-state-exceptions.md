---
title: Reguła analizy kodu CA2153 dla wyjątków uszkodzonych Stanów
ms.date: 02/19/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36442ad0792ef712acd322d17688d8ceb21444cb
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231892"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Unikaj obsługi wyjątków uszkodzonego stanu

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

[Wyjątki uszkodzonych Stanów (rozszerzeń klienta)](https://msdn.microsoft.com/magazine/dd419661.aspx) wskazują, że uszkodzenie pamięci istnieje w procesie. Ich przechwycenie zamiast zezwalania na awarię procesu może prowadzić do luk w zabezpieczeniach, jeśli osoba atakująca może wykorzystać lukę w uszkodzonym regionie pamięci.

## <a name="rule-description"></a>Opis reguły

Rozszerzenie klienta wskazuje, że stan procesu został uszkodzony i nie został przechwycony przez system. W scenariuszu uszkodzenia stanu ogólna procedura obsługi przechwytuje wyjątek tylko wtedy, gdy oznaczy metodę przy użyciu <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName> atrybutu. Domyślnie [środowisko uruchomieniowe języka wspólnego (CLR)](/dotnet/standard/clr) nie wywołuje obsługi catch dla rozszerzeń klienta.

Najbezpieczniejsza opcja polega na tym, aby proces mógł ulec awarii bez przechwycenia tych rodzajów wyjątków. Nawet rejestrowanie kodu może pozwolić osobom atakującym na korzystanie z usterek awarii pamięci.

To ostrzeżenie jest wyzwalane podczas przechwytywania rozszerzeń klienta z użyciem ogólnej procedury obsługi, która przechwytuje wszystkie wyjątki `catch (System.Exception e)` , `catch` na przykład lub bez parametru wyjątku.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby rozwiązać ten problem, wykonaj jedną z następujących czynności:

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> Usuń atrybut. Spowoduje to przywrócenie domyślnego zachowania środowiska uruchomieniowego, w którym rozszerzeń klienta nie są przenoszone do obsługi catch.

- Usuń ogólny program obsługi catch w preferencjach obsługi, które przechwytują określone typy wyjątków. Może to obejmować rozszerzeń klienta, przy założeniu, że kod procedury obsługi może bezpiecznie obsłużyć je (rzadki).

- Ponownie zgłoś rozszerzenie klienta w obsłudze catch, które przekazuje wyjątek do obiektu wywołującego i powinno spowodować zakończenie uruchomionego procesu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="pseudo-code-example"></a>Przykład pseudo kodu

### <a name="violation"></a>Krocz

Poniższy pseudo kodu ilustruje wzorzec wykryty przez tę regułę.

```csharp
[HandleProcessCorruptedStateExceptions]
// Method that handles CSE exceptions.
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-1---remove-the-attribute"></a>Rozwiązanie 1 — Usuwanie atrybutu

<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> Usunięcie atrybutu gwarantuje, że wyjątki uszkodzonych stanów nie są obsługiwane przez metodę.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-2---catch-specific-exceptions"></a>Rozwiązanie 2 — Przechwytywanie określonych wyjątków

Usuń ogólny program obsługi catch i Przechwyć tylko określone typy wyjątków.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle IOException.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle UnauthorizedAccessException.
    }
}
```

### <a name="solution-3---rethrow"></a>Rozwiązanie 3 — ponowne zgłoszenie

Ponownie Zgłoś wyjątek.

```csharp
[HandleProcessCorruptedStateExceptions]
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Rethrow the exception.
        throw;
    }
}
```