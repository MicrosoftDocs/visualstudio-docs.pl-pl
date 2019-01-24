---
title: 'CA1405: Typy podstawowe typu widocznego modelu COM powinny być widoczne dla modelu COM | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2b107e1aa24b51de3efca8a97972c473f40a3da4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54787502"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: Typy podstawowe typów widocznych dla modelu COM powinny być widoczne dla modelu COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|DependsOnFix|

## <a name="cause"></a>Przyczyna
 Typ widoczny Component Object Model (COM) pochodzi z typu, który nie jest widoczne dla modelu COM.

## <a name="rule-description"></a>Opis reguły
 Gdy typem widoczne dla modelu COM, elementy członkowskie są dodawane w nowej wersji, należy przestrzegać ścisłe wytyczne w celu uniknięcia przerwanie klientów COM powiązanych do bieżącej wersji. Typ, który jest niewidoczna dla modelu COM przyjęto założenie, że nie trzeba należy wykonać następujące czynności COM wersji powoduje dodanie nowych elementów członkowskich. Jeśli jednak widoczne dla modelu COM typ pochodzi od typu niewidoczne COM i udostępnia interfejs klasy <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> lub <xref:System.Runtime.InteropServices.ClassInterfaceType> (ustawienie domyślne), wszystkie publiczne elementy członkowskie tego typu podstawowego (o ile są wyraźnie oznaczone jako COM niewidoczne, który zbyteczna) są widoczne dla modelu COM. Jeśli typ podstawowy dodaje nowych elementów członkowskich w kolejnej wersji, mogą przestać działać żadnych klientów COM, który należy powiązać interfejsu klasy typu pochodnego. Typy widoczne dla modelu COM powinny pochodzić tylko w typach widocznych dla modelu COM, aby zmniejszyć prawdopodobieństwo przerwanie klientów modelu COM.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, ukrywanie typów podstawowych widoczne dla modelu COM lub typu pochodnego COM.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę.

 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/cs/FxCop.Interoperability.ComBaseTypes.cs#1)]
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/vb/FxCop.Interoperability.ComBaseTypes.vb#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName> [Wprowadzenie interfejsu klasy](http://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [współdziałanie z niezarządzanego kodu](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
