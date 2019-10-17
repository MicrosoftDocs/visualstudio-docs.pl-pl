---
title: 'CA1406: Unikaj argumentów Int64 dla klientów programu Visual Basic 6'
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
ms.openlocfilehash: 7ebf218b15dcb4048129e308822042efa5f6b0c9
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440513"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Unikaj argumentów Int64 dla klientów programu Visual Basic 6

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Kategoria|Microsoft. współdziałanie|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Typ, który jest jawnie oznaczony jako widoczny dla Component Object Model (COM) deklaruje element członkowski, który przyjmuje argument <xref:System.Int64?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
Klienci Visual Basic 6 COM nie mogą uzyskać dostępu do 64-bitowych liczb całkowitych.

Domyślnie następujące elementy są widoczne dla modelu COM: zestawy, typy publiczne, składowe wystąpienia publicznego w typach publicznych oraz wszystkie elementy członkowskie publicznych typów wartości. Jednak aby zmniejszyć liczbę fałszywych wartości dodatnich, ta reguła wymaga jawnego określenia widoczności COM typu; zestaw zawierający musi być oznaczony atrybutem <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> ustawionym na wartość `false`, a typ musi być oznaczony jako <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawionym na `true`.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły dla parametru, którego wartość może być zawsze wyrażona jako liczba całkowita 32-bitowa, Zmień typ parametru na <xref:System.Int32?displayProperty=fullName>. Jeśli wartość parametru może być większa niż może być wyrażona jako liczba całkowita 32-bitowa, Zmień typ parametru na <xref:System.Decimal?displayProperty=fullName>. Należy zauważyć, że obie <xref:System.Single?displayProperty=fullName> i <xref:System.Double?displayProperty=fullName> nie mają dokładności w górnych zakresach typu danych <xref:System.Int64>. Jeśli element członkowski nie ma być widoczny dla modelu COM, oznacz go atrybutem <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawionym na wartość `false`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
W przypadku, gdy okaże się, że Visual Basic 6 klienci COM nie będą mieć dostępu do tego typu, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje typ, który narusza regułę.

[!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
[!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
[CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

[CA1407: Unikaj składowych statycznych w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Zobacz także

- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)
- [Long, typ danych](/dotnet/visual-basic/language-reference/data-types/long-data-type)
