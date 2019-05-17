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
ms.openlocfilehash: def22bd4aee4f64b5e14f2bbe7978a0dfa061261
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841433"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Unikaj klas wewnętrznych bez wystąpień

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Wewnętrzny typ (w poziomie zestawu) nigdy nie zostanie uruchomiony.

## <a name="rule-description"></a>Opis reguły

Ta zasada próbuje zlokalizować wywołań do jednego z konstruktorów typu i zgłasza naruszenie, jeśli brak wywołania zostanie znaleziony.

Następujące typy nie są sprawdzane przez tę regułę:

- Typy wartości

- Typy abstrakcyjne

- Wyliczenia

- Delegaty

- Typy tablic emitowane przez kompilator

- Typy, nie można utworzyć wystąpienia i tylko definiują [ `static` ](/dotnet/csharp/language-reference/keywords/static) ([ `Shared` w języku Visual Basic](/dotnet/visual-basic/language-reference/modifiers/shared)) metody.

Jeśli zastosujesz <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> do zestawu, który jest analizowana, ta zasada nie oznaczy typy, które są oznaczone jako [ `internal` ](/dotnet/csharp/language-reference/keywords/internal) ([ `Friend` w języku Visual Basic](/dotnet/visual-basic/language-reference/modifiers/friend)) może być polem używane przez zestaw przyjazny.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, Usuń typ lub Dodaj kod, który korzysta z niego. Jeśli typ zawiera tylko `static` metod, Dodaj jedną z następujących do typu, aby uniemożliwić kompilatorowi emitowania publiczne wystąpienia domyślnego konstruktora:

- Konstruktor prywatny dla typów, których platformą docelową .NET Framework w wersji 1.0 i 1.1.

- `static` Modyfikator C# typów, których platformą docelową [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] lub nowszej.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły. Firma Microsoft zaleca, aby pominąć to ostrzeżenie w następujących sytuacjach:

- Klasa jest tworzona za pośrednictwem metody z późnym wiązaniem odbicia, takich jak <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

- Klasa jest tworzona automatycznie przez środowisko uruchomieniowe lub ASP.NET. Niektóre przykłady automatycznie utworzone klasy są tymi, które implementują <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> lub <xref:System.Web.IHttpHandler?displayProperty=fullName>.

- Klasa jest przekazywany jako parametr typu, który ma [ `new` ograniczenie](/dotnet/csharp/language-reference/keywords/new-constraint). Poniższy przykład zostaną oflagowane przez regułę CA1812:

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
- [CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)