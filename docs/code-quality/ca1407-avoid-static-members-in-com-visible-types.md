---
title: 'CA1407: Unikaj statycznych elementów członkowskich w typach widocznych dla modelu COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ea59bee887948fcb9fe293af338f49bfb9f8dfc
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444211"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Unikaj statycznych elementów członkowskich w typach widocznych dla modelu COM

|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Kategoria|Microsoft. współdziałanie|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Typ, który jest jawnie oznaczony jako widoczny dla Component Object Model (COM) zawiera metodę `public``static`.

## <a name="rule-description"></a>Opis reguły
Model COM nie obsługuje metod `static`.

Ta reguła ignoruje metody dostępu do właściwości i zdarzeń, metod przeciążania operatora lub metod, które są oznaczone za pomocą atrybutu <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> lub atrybutu <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.

Domyślnie następujące elementy są widoczne dla modelu COM: zestawy, typy publiczne, składowe wystąpienia publicznego w typach publicznych oraz wszystkie elementy członkowskie publicznych typów wartości.

Aby ta reguła miała miejsce, na poziomie zestawu <xref:System.Runtime.InteropServices.ComVisibleAttribute> musi być ustawiona wartość `false`, a Klasa-<xref:System.Runtime.InteropServices.ComVisibleAttribute> musi być ustawiona na `true`, jak pokazano w poniższym kodzie.

```csharp
using System;
using System.Runtime.InteropServices;

[assembly: ComVisible(false)]
namespace Samples
{
    [ComVisible(true)]
    public class MyClass
    {
        public static void DoSomething()
        {
        }
    }
}
```

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, należy zmienić projekt tak, aby korzystał z metody wystąpienia, która zapewnia te same funkcje co Metoda `static`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Jeśli klient COM nie wymaga dostępu do funkcji dostarczonych przez metodę `static`, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example-violation"></a>Przykładowe naruszenie

### <a name="description"></a>Opis
Poniższy przykład przedstawia metodę `static`, która narusza tę regułę.

### <a name="code"></a>Kod
[!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]

### <a name="comments"></a>Komentarze
W tym przykładzie nie można wywołać metody **Book. FromPages** z modelu com.

## <a name="example-fix"></a>Przykład naprawy

### <a name="description"></a>Opis
Aby naprawić naruszenie w poprzednim przykładzie, można zmienić metodę na wystąpienie, ale nie ma sensu w tym wystąpieniu. Lepszym rozwiązaniem jest jawne zastosowanie `ComVisible(false)` do metody, aby było jasne dla innych deweloperów, którzy nie mogą zobaczyć metody z modelu COM.

W poniższym przykładzie zastosowano <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> do metody.

### <a name="code"></a>Kod
[!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]

## <a name="related-rules"></a>Powiązane reguły
[CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

[CA1406: Unikaj argumentów typu Int64 w przypadku klientów programu Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

[CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Zobacz także
[Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)
