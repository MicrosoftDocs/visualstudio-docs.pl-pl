---
title: 'CA1812: Unikaj klas wewnętrznych bez wystąpień'
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f924e9530a7ee43ec2222366141c3af6be2efc29
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233613"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Unikaj klas wewnętrznych bez wystąpień

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Kategoria|Microsoft.Performance|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Typ wewnętrzny (na poziomie zestawu) nigdy nie jest tworzona.

## <a name="rule-description"></a>Opis reguły

Ta reguła próbuje zlokalizować wywołanie jednego z konstruktorów typu i zgłasza naruszenie, jeśli nie zostanie znalezione wywołanie.

Następujące typy nie są badane przez tę regułę:

- Typy wartości

- Typy abstrakcyjne

- Wyliczenia

- Delegaty

- Typy tablic emitowane przez kompilator

- Typy, których nie można utworzyć, i które definiują [`static`](/dotnet/csharp/language-reference/keywords/static) tylko metody ([ `Shared` w Visual Basic](/dotnet/visual-basic/language-reference/modifiers/shared)).

W przypadku zastosowania <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> do zestawu, który jest analizowany, ta reguła nie będzie flagować typów, które są oznaczone jako [`internal`](/dotnet/csharp/language-reference/keywords/internal) ([ `Friend` w Visual Basic](/dotnet/visual-basic/language-reference/modifiers/friend)), ponieważ pole może być używane przez zestaw zaprzyjaźniony.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Usuń typ lub Dodaj kod, który go używa. Jeśli typ zawiera tylko `static` metody, należy dodać jeden z następujących elementów do typu, aby uniemożliwić kompilatorowi emitowanie domyślnego publicznego konstruktora wystąpień:

- Modyfikator dla typów C# , które są przeznaczone dla .NET Framework 2,0 lub nowszych. `static`

- Konstruktor prywatny dla typów, które są przeznaczone dla .NET Framework wersje 1,0 i 1,1.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Można bezpiecznie pominąć ostrzeżenie z tej reguły. Zaleca się, aby pominąć to ostrzeżenie w następujących sytuacjach:

- Klasa jest tworzona za pomocą metod odbicia z późnym wiązaniem, takich jak <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

- Klasa jest tworzona automatycznie przez środowisko uruchomieniowe lub ASP.NET. Przykłady automatycznie utworzonych klas to te, które implementują <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> lub <xref:System.Web.IHttpHandler?displayProperty=fullName>.

- Klasa jest przenoszona jako parametr typu, który ma [ `new` ograniczenie](/dotnet/csharp/language-reference/keywords/new-constraint). Następujący przykład zostanie oflagowany przez regułę CA1812:

    ```csharp
    internal class MyClass
    {
        public DoSomething()
        {
        }
    }
    public class MyGeneric<T> where T : new()
    {
        public T Create()
        {
            return new T();
        }
    }

    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
    mc.Create();
    ```

## <a name="related-rules"></a>Powiązane reguły

- [CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)
- [CA1801: Przejrzyj nieużywane parametry](../code-quality/ca1801-review-unused-parameters.md)
- [CA1804: Usuń nieużywane elementy lokalne](../code-quality/ca1804-remove-unused-locals.md)