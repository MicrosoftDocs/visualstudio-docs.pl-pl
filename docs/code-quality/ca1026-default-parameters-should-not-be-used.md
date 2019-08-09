---
title: 'CA1026: Nie należy używać parametrów domyślnych'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 888e1b5d551e357eb732dfe3f7661d51cbdf089d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923139"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Nie należy używać parametrów domyślnych

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Typ widoczny na zewnątrz zawiera zewnętrznie widoczną metodę, która używa domyślnego parametru.

## <a name="rule-description"></a>Opis reguły
Metody korzystające z parametrów domyślnych są dozwolone pod Common Language Specification (CLS); jednak specyfikacja CLS umożliwia kompilatorom ignorowanie wartości, które są przypisane do tych parametrów. Kod Zapisano dla kompilatorów, które ignorują domyślne wartości parametrów, muszą jawnie podawać argumenty dla każdego domyślnego parametru. Aby zachować zachowanie w różnych językach programowania, metody, które używają parametrów domyślnych, powinny być zastępowane przeciążeniami metod, które udostępniają parametry domyślne.

Kompilator ignoruje wartości domyślnych parametrów dla rozszerzenia zarządzanego, C++ gdy uzyskuje dostęp do kodu zarządzanego. Kompilator Visual Basic obsługuje metody, które mają domyślne parametry, które używają [opcjonalnego](/dotnet/visual-basic/language-reference/modifiers/optional) słowa kluczowego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Zastąp metodę, która używa domyślnych parametrów z przeciążeniami metod, które dostarczają parametry domyślne.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład przedstawia metodę, która używa parametrów domyślnych i przeciążonych metod, które zapewniają równoważną funkcjonalność.

[!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
[CA1025: Zastąp powtarzalne argumenty tablicą parametrów](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Zobacz także
[Niezależność od języka i składniki niezależne od języka](/dotnet/standard/language-independence-and-language-independent-components)