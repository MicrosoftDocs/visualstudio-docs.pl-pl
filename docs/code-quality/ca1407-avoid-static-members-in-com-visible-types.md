---
title: 'CA1407: Unikaj statycznych składowych w typach widocznych dla modelu COM'
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
ms.openlocfilehash: 631be1a93318cd24af4251fefbc710294fa52bf7
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922009"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Unikaj statycznych składowych w typach widocznych dla modelu COM

|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Typ, który jest jawnie oznaczony jako widoczny dla Component Object Model (com) zawiera `public``static` metodę.

## <a name="rule-description"></a>Opis reguły
Model com nie obsługuje `static` metod.

Ta reguła ignoruje metody dostępu do właściwości i zdarzeń, metod przeciążania operatora lub metod, które są oznaczone przy użyciu <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atrybutu <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> lub atrybutu.

Domyślnie następujące elementy są widoczne dla modelu COM: zestawy, typy publiczne, składowe wystąpienia publicznego w typach publicznych oraz wszystkie elementy członkowskie publicznych typów wartości.

Aby ta reguła miała <xref:System.Runtime.InteropServices.ComVisibleAttribute> miejsce, na poziomie zestawu musi być `false` ustawiona wartość i Klasa- <xref:System.Runtime.InteropServices.ComVisibleAttribute> musi być ustawiona na `true`, jak pokazano w poniższym kodzie.

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
Aby naprawić naruszenie tej zasady, należy zmienić projekt tak, aby korzystał z metody wystąpienia, która zapewnia te same funkcje co `static` Metoda.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Jeśli klient com nie wymaga dostępu do funkcji dostarczonych przez `static` metodę, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example-violation"></a>Przykładowe naruszenie

### <a name="description"></a>Opis
Poniższy przykład przedstawia `static` metodę, która narusza tę regułę.

### <a name="code"></a>Kod
[!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]

### <a name="comments"></a>Komentarze
W tym przykładzie nie można wywołać metody **Book. FromPages** z modelu com.

## <a name="example-fix"></a>Przykład naprawy

### <a name="description"></a>Opis
Aby naprawić naruszenie w poprzednim przykładzie, można zmienić metodę na wystąpienie, ale nie ma sensu w tym wystąpieniu. Lepszym rozwiązaniem jest jawne zastosowanie `ComVisible(false)` metody w celu poprawienia jej od innych deweloperów, którzy nie mogą zobaczyć metody z modelu com.

Poniższy przykład dotyczy <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> metody.

### <a name="code"></a>Kod
[!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]

## <a name="related-rules"></a>Powiązane reguły
[CA1017 Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

[CA1406: Unikaj argumentów Int64 dla Visual Basic 6 klientów](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

[CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Zobacz także
[Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)