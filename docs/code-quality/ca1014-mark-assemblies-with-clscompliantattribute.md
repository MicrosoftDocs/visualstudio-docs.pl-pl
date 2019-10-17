---
title: 'CA1014: Oznacz zestawy za pomocą CLSCompliantAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c615015fac5e8e9b60425679e116b8c7680ea637
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72441642"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Oznacz zestawy za pomocą CLSCompliantAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Kategoria|Microsoft. Design|
|Zmiana podziału|Nieprzerwanie|

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

[!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
[!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
[!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>Zobacz także

- <xref:System.CLSCompliantAttribute?displayProperty=fullName>
- [Niezależność od języka i składniki niezależne od języka](/dotnet/standard/language-independence-and-language-independent-components)
