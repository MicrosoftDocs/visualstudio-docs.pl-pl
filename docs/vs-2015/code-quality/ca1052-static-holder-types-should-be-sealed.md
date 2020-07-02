---
title: 'CA1052: statyczne typy posiadaczy powinny być zapieczętowane | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 14231cc4dcde5aed5cabc2d8a6172a002c0ba6bf
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539753"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: Statyczne typy przechowujące powinny być zapieczętowane
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony zawiera tylko statyczne elementy członkowskie i nie jest zadeklarowany za pomocą modyfikatora [Sealed](https://msdn.microsoft.com/library/8e4ed5d3-10be-47db-9488-0da2008e6f3f) ([NotInheritable](https://msdn.microsoft.com/library/5c4da7c9-9562-4653-a947-1972e992f9f9)).

## <a name="rule-description"></a>Opis reguły
 Ta reguła zakłada, że typ, który zawiera tylko statyczne składowe, nie jest przeznaczony do dziedziczenia, ponieważ typ nie udostępnia żadnych funkcji, które mogą zostać zastąpione w typie pochodnym. Typ, który nie jest przeznaczony do dziedziczenia powinien być oznaczony `sealed` modyfikatorem, aby uniemożliwić jego użycie jako typ podstawowy.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Oznacz typ jako `sealed` . W przypadku określania wartości docelowej [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2,0 lub wcześniejszej, lepszym rozwiązaniem jest oznaczenie typu jako `static` . W ten sposób należy unikać deklarowania konstruktora prywatnego w celu uniemożliwienia tworzenia klasy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie z tej reguły tylko wtedy, gdy typ jest przeznaczony do dziedziczenia. Brak `sealed` modyfikatora sugeruje, że typ jest użyteczny jako typ podstawowy.

## <a name="example-of-a-violation"></a>Przykład naruszenia

### <a name="description"></a>Opis
 Poniższy przykład pokazuje typ, który narusza regułę.

### <a name="code"></a>Kod
 [!code-cpp[FxCop.Design.StaticMembers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cpp/FxCop.Design.StaticMembers.cpp#1)]
 [!code-csharp[FxCop.Design.StaticMembers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cs/FxCop.Design.StaticMembers.cs#1)]
 [!code-vb[FxCop.Design.StaticMembers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/vb/FxCop.Design.StaticMembers.vb#1)]

## <a name="fix-with-the-static-modifier"></a>Popraw przy użyciu modyfikatora statycznego

### <a name="description"></a>Opis
 Poniższy przykład pokazuje, jak naprawić naruszenie tej reguły przez oznaczenie typu z `static` modyfikatorem.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembersFixed/cs/FxCop.Design.StaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1053: Statyczne typy przechowujące nie powinny mieć konstruktorów](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
