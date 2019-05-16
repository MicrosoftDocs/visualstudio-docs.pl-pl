---
title: 'CA1014: Oznacz zestawy atrybutem CLSCompliant | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 324f52eaac86a6ff48b71a98714b866dfca8b239
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704269"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Oznacz zestawy atrybutem CLSCompliant
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Zestaw nie ma <xref:System.CLSCompliantAttribute?displayProperty=fullName> zastosowany do niego.

## <a name="rule-description"></a>Opis reguły
 The Common Language Specification (CLS) definiuje ograniczenia nazw, typów danych i reguł, z którymi muszą być zgodne zestawy, jeśli zostaną użyte w językach programowania. Zasada dobrego projektowania nakazuje, aby wszystkie zestawy jawnie wskazywały zgodność ze specyfikacją CLS przy użyciu <xref:System.CLSCompliantAttribute>. Jeśli ten atrybut nie jest obecny w zestawie, zestaw nie jest zgodne.

 Istnieje możliwość zgodne ze specyfikacją CLS zestawu zawierają typy lub elementy członkowskie, które nie są zgodne typu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Dodaj atrybut do zestawu. Zamiast Oznaczanie całego zestawu jako niezgodne, należy określić, które typów lub elementów członkowskich typu nie są zgodne i oznaczyć te elementy w związku z tym. Jeśli to możliwe należy podać zgodny ze specyfikacją CLS alternatywę dla członków niezgodnych tak, aby najszerszych możliwych odbiorców mogą uzyskiwać dostęp do wszystkich funkcji zestawu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Jeśli nie chcesz zestawie, który ma być zgodne, zastosuj atrybut i ustawić jej wartość na `false`.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono zestaw, który ma <xref:System.CLSCompliantAttribute?displayProperty=fullName> atrybut zastosowany, która deklaruje na zgodny ze specyfikacją CLS.

 [!code-cpp[FxCop.Design.AssembliesCls#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cpp/FxCop.Design.AssembliesCls.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCls#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cs/FxCop.Design.AssembliesCls.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/vb/FxCop.Design.AssembliesCls.vb#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.CLSCompliantAttribute?displayProperty=fullName> [Niezależność od języka i składniki niezależne od języka](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
