---
title: 'CA1014: Oznacz zestawy atrybutem CLSCompliant'
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
ms.openlocfilehash: f11a93380f149648ece4ae6d71bc9c2f25df5191
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923115"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Oznacz zestawy atrybutem CLSCompliant

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Zestaw nie ma <xref:System.CLSCompliantAttribute?displayProperty=fullName> zastosowanego atrybutu.

## <a name="rule-description"></a>Opis reguły
The Common Language Specification (CLS) definiuje ograniczenia nazw, typów danych i reguł, z którymi muszą być zgodne zestawy, jeśli zostaną użyte w językach programowania. Dobry projekt wymusza, że wszystkie zestawy jawnie wskazują zgodność ze specyfikacją CLS z <xref:System.CLSCompliantAttribute>. Jeśli atrybut nie jest obecny w zestawie, zestaw nie jest zgodny.

Istnieje możliwość, że zestaw zgodny ze specyfikacją CLS zawiera typy lub elementy członkowskie typu, które nie są zgodne.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Dodaj atrybut do zestawu. Zamiast oznaczać cały zestaw jako niezgodny, należy określić, który typ lub elementy członkowskie typu nie są zgodne, i oznaczyć te elementy jako takie. Jeśli to możliwe, należy zapewnić zgodność ze specyfikacją CLS alternatywę dla niezgodnych elementów członkowskich, aby możliwie najszerszej grupie odbiorców mógł uzyskać dostęp do wszystkich funkcji zestawu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły. Jeśli nie chcesz, aby zestaw był zgodny, zastosuj atrybut i ustaw jego wartość na `false`.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje zestaw, który ma <xref:System.CLSCompliantAttribute?displayProperty=fullName> atrybut zastosowany, który deklaruje zgodny ze specyfikacją CLS.

[!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
[!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
[!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>Zobacz także

- <xref:System.CLSCompliantAttribute?displayProperty=fullName>
- [Niezależność od języka i składniki niezależne od języka](/dotnet/standard/language-independence-and-language-independent-components)