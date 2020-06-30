---
title: 'CA1405: typy podstawowe typu widocznego dla modelu COM powinny być widoczne dla modelu COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 779d3ec1ed520d5d48043f90e7cb6272553012a6
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535047"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: Typy podstawowe typów widocznych dla modelu COM powinny być widoczne dla modelu COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|DependsOnFix|

## <a name="cause"></a>Przyczyna
 Typ widoczny dla Component Object Model (COM) pochodzi z typu, który nie jest widoczny dla modelu COM.

## <a name="rule-description"></a>Opis reguły
 Gdy typ widoczny dla modelu COM dodaje członków w nowej wersji, musi przestrzegać ścisłych wytycznych, aby uniknąć przerwania klientów COM, które są powiązane z bieżącą wersją. Typ, który jest niewidoczny dla modelu COM, zakłada, że nie musi on być zgodny z regułami dotyczącymi obsługi wersji modelu COM podczas dodawania nowych elementów członkowskich. Jeśli jednak typ widoczny dla modelu COM pochodzi od typu niewidocznego dla modelu COM i uwidacznia interfejs klasy <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> lub <xref:System.Runtime.InteropServices.ClassInterfaceType> (domyślnie), wszystkie publiczne elementy członkowskie typu podstawowego (chyba że są one jawnie oznaczone jako niewidoczne jako com, które byłyby nadmiarowe) są udostępniane modelowi com. Jeśli typ podstawowy dodaje nowych członków w kolejnej wersji, każdy klient COM, który powiąże się z interfejsem klasy typu pochodnego może zostać zerwana. Typy widoczne dla modelu COM powinny dziedziczyć tylko z typów widocznych dla modelu COM, aby zmniejszyć prawdopodobieństwo przerwania klientów COM.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zmień typy podstawowe modelu COM widoczne lub niewidoczny typ pochodny COM.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę.

 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/cs/FxCop.Interoperability.ComBaseTypes.cs#1)]
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/vb/FxCop.Interoperability.ComBaseTypes.vb#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>[Wprowadzenie do interfejsu klasy](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [współdziałanie z kodem niezarządzanym](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
