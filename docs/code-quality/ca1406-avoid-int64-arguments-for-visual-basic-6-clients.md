---
title: 'CA1406: Unikaj używania argumentów typu Int64 w klientach w języku Visual Basic 6'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4dfcc612e931756b0e3d817556c9b37844bc3cfd
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922036"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Unikaj używania argumentów typu Int64 w klientach w języku Visual Basic 6

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Typ, który jest jawnie oznaczony jako widoczny dla Component Object Model (com) deklaruje element członkowski przyjmujący <xref:System.Int64?displayProperty=fullName> argument.

## <a name="rule-description"></a>Opis reguły
Klienci Visual Basic 6 COM nie może uzyskać dostęp do 64-bitowych liczb całkowitych.

Domyślnie następujące elementy są widoczne dla modelu COM: zestawy, typy publiczne, składowe wystąpienia publicznego w typach publicznych oraz wszystkie elementy członkowskie publicznych typów wartości. Jednak aby zmniejszyć liczbę fałszywych wartości dodatnich, ta reguła wymaga jawnego określenia widoczności COM typu; zestaw zawierający <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> musi być oznaczony zestawem do `false` , a typ <xref:System.Runtime.InteropServices.ComVisibleAttribute> musi być oznaczony z ustawioną na `true`.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły dla parametru, którego wartość może być zawsze wyrażona jako liczba całkowita 32-bitowa, Zmień typ parametru na <xref:System.Int32?displayProperty=fullName>. Jeśli wartość parametru może być większa niż może być wyrażona jako liczba całkowita 32-bitowa, Zmień typ parametru na <xref:System.Decimal?displayProperty=fullName>. Należy zauważyć, <xref:System.Single?displayProperty=fullName> że <xref:System.Double?displayProperty=fullName> obie i tracą dokładność w górnych zakresach <xref:System.Int64> typu danych. Jeśli element członkowski nie ma być widoczny dla modelu COM, oznacz go z <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawionym na. `false`

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
W przypadku, gdy okaże się, że Visual Basic 6 klienci COM nie będą mieć dostępu do tego typu, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje typ, który narusza regułę.

[!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
[!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
[CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

[CA1407: Unikaj statycznych elementów członkowskich w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017 Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Zobacz także

- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)
- [Long, typ danych](/dotnet/visual-basic/language-reference/data-types/long-data-type)