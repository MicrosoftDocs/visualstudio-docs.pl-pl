---
title: CA2153 reguł analizy kodu dla uszkodzony wyjątków stanu
ms.date: 02/19/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b75e45b8a199265eaefe3a2b3c37ed62039e0eb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542160"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Unikaj obsługi wyjątków stan uszkodzony

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

[Uszkodzony stan wyjątków (CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx) wskazać, że pamięć uszkodzenie istnieje w procesie. Przechwytywanie tych zamiast zezwalać awarię procesu może prowadzić do luk w zabezpieczeniach, jeśli osoba atakująca może wykorzystać do regionu pamięci uszkodzony.

## <a name="rule-description"></a>Opis reguły

Rozszerzenie klienta wskazuje, że stan procesu został uszkodzony i nie zgłoszony przez system. W tym scenariuszu uszkodzony ogólny program obsługi tylko przechwytuje wyjątek po oznaczeniu metodę z <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName> atrybutu. Domyślnie [środowiska uruchomieniowego języka wspólnego (CLR)](/dotnet/standard/clr) obsługi catch nie jest wywoływany w przypadku rozszerzeń klienta.

Najbezpieczniej jest, aby zezwolić na awarię procesu bez wychwytywanie tych rodzajów wyjątków. Nawet rejestrowania kodu może umożliwić atakującemu wykorzystać błędy uszkodzenia pamięci.

To ostrzeżenie uaktywnia Przechwytywanie rozszerzeń klienta za pomocą ogólny program obsługi, który przechwytuje wszystkie wyjątki, na przykład `catch (System.Exception e)` lub `catch` w przypadku braku parametrów wyjątku.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby rozwiązać tego ostrzeżenia, wykonaj jedną z następujących czynności:

- Usuń <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atrybutu. Przywraca domyślne zachowanie środowiska uruchomieniowego, gdzie rozszerzeń klienta nie zostaną przekazane do obsługi catch.

- Usuń procedurę obsługi catch ogólne, in preference of programów obsługi, które Przechwytuj typów wyjątków określonych. Może to obejmować rozszerzeń klienta, przy założeniu, że kod procedury obsługi bezpiecznie mógł je obsłużyć (rzadkiego).

- Zgłoś ponownie rozszerzenie klienta w obsługi catch, który przekazuje wyjątek do obiektu wywołującego i powinno dawać wynik końcowy uruchomionego procesu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="pseudo-code-example"></a>Przykładowy pseudo-kod

### <a name="violation"></a>Naruszenie zasad

Poniższy pseudo-kod przedstawiono wzorzec wykryte przez tę regułę.

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

### <a name="solution-1---remove-the-attribute"></a>Rozwiązanie 1. Usuń atrybut

Usuwanie <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atrybutu zapewnia uszkodzony stan wyjątki nie są obsługiwane przez metodę.

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

### <a name="solution-2---catch-specific-exceptions"></a>Rozwiązanie 2 - określonych wyjątków catch

Usuń procedurę obsługi catch ogólne i przechwytywać tylko typy określonego wyjątku.

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

### <a name="solution-3---rethrow"></a>Zgłoś ponownie rozwiązanie 3-

Zgłoś ponownie wyjątek.

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