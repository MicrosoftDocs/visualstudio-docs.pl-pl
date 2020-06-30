---
title: 'CA1407: Unikaj statycznych elementów członkowskich w typach widocznych dla modelu COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 436a8614c18c296c072d91116143306d898f0436
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538856"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Unikaj statycznych składowych w typach widocznych dla modelu COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Typ, który jest jawnie oznaczony jako widoczny dla Component Object Model (COM) zawiera `public``static` metodę.

## <a name="rule-description"></a>Opis reguły
 Model COM nie obsługuje `static` metod.

 Ta reguła ignoruje metody dostępu do właściwości i zdarzeń, metod przeciążania operatora lub metod, które są oznaczone przy użyciu <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atrybutu lub <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atrybutu.

 Domyślnie następujące elementy są widoczne dla modelu COM: zestawy, typy publiczne, składowe wystąpienia publicznego w typach publicznych oraz wszystkie elementy członkowskie publicznych typów wartości.

 Aby ta reguła miała miejsce, na poziomie zestawu <xref:System.Runtime.InteropServices.ComVisibleAttribute> musi być ustawiona wartość `false` i Klasa- <xref:System.Runtime.InteropServices.ComVisibleAttribute> musi być ustawiona na `true` , jak pokazano w poniższym kodzie.

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
 Jeśli klient COM nie wymaga dostępu do funkcji dostarczonych przez metodę, można bezpiecznie pominąć ostrzeżenie z tej reguły `static` .

## <a name="example-violation"></a>Przykładowe naruszenie

### <a name="description"></a>Opis
 Poniższy przykład przedstawia `static` metodę, która narusza tę regułę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersViolation/cs/FxCop.Interoperability.ComVisibleStaticMembersViolation.cs#1)]

### <a name="comments"></a>Komentarze
 W tym przykładzie nie można wywołać metody **Book. FromPages** z modelu com.

## <a name="example-fix"></a>Przykład naprawy

### <a name="description"></a>Opis
 Aby naprawić naruszenie w poprzednim przykładzie, można zmienić metodę na wystąpienie, ale nie ma sensu w tym wystąpieniu. Lepszym rozwiązaniem jest jawne zastosowanie `ComVisible(false)` metody w celu poprawienia jej od innych deweloperów, którzy nie mogą zobaczyć metody z modelu com.

 Poniższy przykład dotyczy <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> metody.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersFixed/cs/FxCop.Interoperability.ComVisibleStaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: Unikaj używania argumentów typu Int64 w klientach w języku Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: Unikaj niepublicznych pól w typach wartości widocznych w modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Zobacz też
 [Współdziałanie z kodem niezarządzanym](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
