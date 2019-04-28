---
title: 'CA1812: Unikaj klas wewnętrznych bez wystąpień'
ms.date: 11/04/2016
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
ms.openlocfilehash: 08d8b907e4a211b0735f07377c21dec1c0a982c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796907"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Unikaj klas wewnętrznych bez wystąpień

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Wystąpienie typu na poziomie zestawu nie jest tworzone przez kod w zestawie.

## <a name="rule-description"></a>Opis reguły

Ta zasada próbuje zlokalizować wywołań do jednego z konstruktorów typu i zgłasza naruszenie, jeśli brak wywołania zostanie znaleziony.

Następujące typy nie są sprawdzane przez tę regułę:

- Typy wartości

- Typy abstrakcyjne

- Wyliczenia

- Delegaty

- Typy tablic emitowane przez kompilator

- Typy, którego nie można utworzyć wystąpienia i definiują `static` (`Shared` w języku Visual Basic) tylko metody.

Jeśli zastosujesz <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> do zestawu, który jest analizowana, ta zasada zostanie przeprowadzona na żadnych konstruktorów, które są oznaczone jako `internal` , ponieważ nie można sprawdzić, czy pole jest używany przez inny `friend` zestawu.

Mimo że nie można obejść to ograniczenie w Visual Studio Code Analysis, zewnętrzne autonomicznego programu FxCop wystąpi na wewnętrzny konstruktory co `friend` zestawu znajduje się w analizie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, Usuń typ lub Dodaj kod, który korzysta z niego. Jeśli typ zawiera tylko metody statyczne, Dodaj jedną z następujących do typu, aby uniemożliwić kompilatorowi emitowania publiczne wystąpienia domyślnego konstruktora:

- Konstruktor prywatny dla typów, których platformą docelową .NET Framework w wersji 1.0 i 1.1.

- `static` (`Shared` w języku Visual Basic) modyfikator dla typów, których platformą docelową [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły. Firma Microsoft zaleca, aby pominąć to ostrzeżenie w następujących sytuacjach:

- Klasa jest tworzona za pośrednictwem metody z późnym wiązaniem odbicia, takich jak <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

- Klasa jest tworzony automatycznie w czasie wykonywania lub [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Na przykład klas, które implementują <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> lub <xref:System.Web.IHttpHandler?displayProperty=fullName>.

- Klasa jest przekazywany jako parametr typu ogólnego, który ma nowe ograniczenie. Na przykład poniższy przykład zgłosi tej reguły.

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
    // [...]
    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
    mc.Create();
    ```

  W takich przypadkach zaleca się, że pominąć to ostrzeżenie.

## <a name="related-rules"></a>Powiązane reguły

[CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1801: Przejrzyj nieużywane parametry](../code-quality/ca1801-review-unused-parameters.md)

[CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)