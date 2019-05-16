---
title: 'CA1406: Unikaj argumentów Int64 dla klientów w języku Visual Basic 6 | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7cf2fc4e9160f44f51ac565619bd8d52bff8b22b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705722"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Unikaj używania argumentów typu Int64 w klientach w języku Visual Basic 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ, który jest specjalnie oznaczony jako widoczny na Component Object Model (COM) deklaruje element członkowski tego przyjmuje <xref:System.Int64?displayProperty=fullName> argumentu.

## <a name="rule-description"></a>Opis reguły
 Klienci Visual Basic 6 COM nie może uzyskać dostęp do 64-bitowych liczb całkowitych.

 Domyślnie widoczny dla modelu COM są następujące: zestawy, typy publiczne, składowe publiczne wystąpienia w publicznych typach i wszystkich elementów członkowskich typów publicznych wartości. Aby zmniejszyć liczbę fałszywych alarmów, ta reguła wymaga jednak widoczność COM typu, który ma być jawnie określony; muszą być oznaczone zawierające zestaw <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> równa `false` i typ musi być oznaczony przez <xref:System.Runtime.InteropServices.ComVisibleAttribute> równa `true`.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady dla parametru, którego wartość, zawsze może być wyrażona jako całkowite 32-bitowych, Zmień typ parametru na <xref:System.Int32?displayProperty=fullName>. Jeśli wartość parametru może być większy niż może być wyrażona jako całkowite 32-bitowych, Zmień typ parametru na <xref:System.Decimal?displayProperty=fullName>. Należy pamiętać, że oba <xref:System.Single?displayProperty=fullName> i <xref:System.Double?displayProperty=fullName> tracić dokładność w prawym górnym zakresy <xref:System.Int64> typu danych. Jeśli element członkowski nie jest przeznaczona do być widoczne dla modelu COM, oznacz ją za pomocą <xref:System.Runtime.InteropServices.ComVisibleAttribute> równa `false`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli ma pewności, czy klienci Visual Basic 6 COM nie będą miały dostęp typu.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę.

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/cs/FxCop.Interoperability.LongArgument.cs#1)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/vb/FxCop.Interoperability.LongArgument.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Unikaj statycznych elementów członkowskich w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Zobacz też
 [Współdziałanie z niezarządzanego kodu](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [Long — typ danych](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516)
