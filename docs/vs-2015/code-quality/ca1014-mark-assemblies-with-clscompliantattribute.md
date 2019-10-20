---
title: 'CA1014: Oznacz zestawy za pomocą CLSCompliantAttribute | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9408a7b55c800a7979c39075afdf8e9e6e4c7cdb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663160"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Oznacz zestawy za pomocą CLSCompliantAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Zestaw nie ma zastosowanego atrybutu <xref:System.CLSCompliantAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 The Common Language Specification (CLS) definiuje ograniczenia nazw, typów danych i reguł, z którymi muszą być zgodne zestawy, jeśli zostaną użyte w językach programowania. Dobry projekt wymusza, że wszystkie zestawy jawnie wskazują zgodność ze specyfikacją CLS z <xref:System.CLSCompliantAttribute>. Jeśli atrybut nie jest obecny w zestawie, zestaw nie jest zgodny.

 Istnieje możliwość, że zestaw zgodny ze specyfikacją CLS zawiera typy lub elementy członkowskie typu, które nie są zgodne.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Dodaj atrybut do zestawu. Zamiast oznaczać cały zestaw jako niezgodny, należy określić, który typ lub elementy członkowskie typu nie są zgodne, i oznaczyć te elementy jako takie. Jeśli to możliwe, należy zapewnić zgodność ze specyfikacją CLS alternatywę dla niezgodnych elementów członkowskich, aby możliwie najszerszej grupie odbiorców mógł uzyskać dostęp do wszystkich funkcji zestawu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Jeśli nie chcesz, aby zestaw był zgodny, zastosuj atrybut i ustaw jego wartość na `false`.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono zestaw, który ma atrybut <xref:System.CLSCompliantAttribute?displayProperty=fullName>, który deklaruje zgodność ze specyfikacją CLS.

 [!code-cpp[FxCop.Design.AssembliesCls#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cpp/FxCop.Design.AssembliesCls.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCls#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cs/FxCop.Design.AssembliesCls.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/vb/FxCop.Design.AssembliesCls.vb#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.CLSCompliantAttribute?displayProperty=fullName> [niezależność od języka i składniki niezależne od języka](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
