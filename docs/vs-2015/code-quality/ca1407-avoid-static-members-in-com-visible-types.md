---
title: 'CA1407: Unikaj statycznych elementów członkowskich w typach widocznych dla modelu COM | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 93c56c17998bbe672ed5816fc950eec5cc56b1c3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705734"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Unikaj statycznych składowych w typach widocznych dla modelu COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ, który jest specjalnie oznaczony jako widoczny na Component Object Model (COM) zawiera `public``static` metody.

## <a name="rule-description"></a>Opis reguły
 Model COM nie obsługuje `static` metody.

 Ta zasada powoduje ignorowanie właściwości i metod dostępu zdarzeń, przeciążenia metody lub metody, które są oznaczone za pomocą operatora <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atrybutu lub <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atrybutu.

 Domyślnie widoczny dla modelu COM są następujące: zestawy, typy publiczne, składowe publiczne wystąpienia w publicznych typach i wszystkich elementów członkowskich typów publicznych wartości.

 Dla tej reguły występuje, poziomie zestawu <xref:System.Runtime.InteropServices.ComVisibleAttribute> musi być równa `false` i klasa - <xref:System.Runtime.InteropServices.ComVisibleAttribute> musi być równa `true`, jak pokazano w poniższym kodzie.

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
 Aby naprawić naruszenie tej zasady, zmiany projektu przy użyciu metody wystąpienia, która zapewnia taką samą funkcjonalność jak `static` metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Bezpiecznie Pomijaj ostrzeżeń dla tej reguły, jeśli klient modelu COM nie wymaga dostępu do funkcji, w których jest świadczona przez `static` metody.

## <a name="example-violation"></a>Przykład naruszenia

### <a name="description"></a>Opis
 W poniższym przykładzie przedstawiono `static` metodę, która narusza tę regułę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersViolation/cs/FxCop.Interoperability.ComVisibleStaticMembersViolation.cs#1)]

### <a name="comments"></a>Komentarze
 W tym przykładzie **Book.FromPages** nie można wywołać metody z modelu COM.

## <a name="example-fix"></a>Przykład poprawkę

### <a name="description"></a>Opis
 Aby naprawić naruszenie w poprzednim przykładzie, można zmienić metodę z metodą wystąpienia, ale który nie ma sensu w tym wystąpieniu. Lepszym rozwiązaniem jest wyraźnie zastosujesz `ComVisible(false)` do metody, aby stał się Wyczyść, aby inni deweloperzy, że metody mogą być niewidoczne z modelu COM.

 Następujący przykład dotyczy <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> do metody.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersFixed/cs/FxCop.Interoperability.ComVisibleStaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: Unikaj argumentów Int64 dla klientów w języku Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Zobacz też
 [Współdziałanie z kodem niezarządzanym](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
