---
title: 'CA1406: Unikaj argumentów Int64 dla Visual Basic 6 klientów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b6ab93c24cd97d498ae886c7a9184fd4a5f111f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534917"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Unikaj używania argumentów typu Int64 w klientach w języku Visual Basic 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ, który jest jawnie oznaczony jako widoczny dla Component Object Model (COM) deklaruje element członkowski przyjmujący <xref:System.Int64?displayProperty=fullName> argument.

## <a name="rule-description"></a>Opis reguły
 Klienci Visual Basic 6 COM nie mogą uzyskać dostępu do 64-bitowych liczb całkowitych.

 Domyślnie następujące elementy są widoczne dla modelu COM: zestawy, typy publiczne, składowe wystąpienia publicznego w typach publicznych oraz wszystkie elementy członkowskie publicznych typów wartości. Jednak aby zmniejszyć liczbę fałszywych wartości dodatnich, ta reguła wymaga jawnego określenia widoczności COM typu; zestaw zawierający musi być oznaczony <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> zestawem do `false` , a typ musi być oznaczony z <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawioną na `true` .

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły dla parametru, którego wartość może być zawsze wyrażona jako liczba całkowita 32-bitowa, Zmień typ parametru na <xref:System.Int32?displayProperty=fullName> . Jeśli wartość parametru może być większa niż może być wyrażona jako liczba całkowita 32-bitowa, Zmień typ parametru na <xref:System.Decimal?displayProperty=fullName> . Należy zauważyć, że obie <xref:System.Single?displayProperty=fullName> i <xref:System.Double?displayProperty=fullName> tracą dokładność w górnych zakresach <xref:System.Int64> typu danych. Jeśli element członkowski nie ma być widoczny dla modelu COM, oznacz go z <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawionym na `false` .

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 W przypadku, gdy okaże się, że Visual Basic 6 klienci COM nie będą mieć dostępu do tego typu, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę.

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/cs/FxCop.Interoperability.LongArgument.cs#1)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/vb/FxCop.Interoperability.LongArgument.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1413: Unikaj niepublicznych pól w typach wartości widocznych w modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Unikaj statycznych składowych w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Zobacz też
 [Współdziałanie z niezarządzanym](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [typem danych long](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516) Code
