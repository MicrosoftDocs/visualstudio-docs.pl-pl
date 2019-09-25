---
title: 'CA1033: Metody interfejsu powinny móc zostać wywołane przez typy podrzędne'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a0ed38a713f9e9a2ab95ad7e1062c6d5d9ab541d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236105"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: Metody interfejsu powinny móc zostać wywołane przez typy podrzędne

|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Niezapieczętowany typ widoczny na zewnątrz zapewnia jawną implementację metody interfejsu publicznego i nie dostarcza alternatywnej metody widocznej z zewnątrz o tej samej nazwie.

## <a name="rule-description"></a>Opis reguły
Rozważmy typ podstawowy, który jawnie implementuje metodę interfejsu publicznego. Typ, który pochodzi od typu podstawowego, może uzyskać dostęp do dziedziczonej metody interfejsu tylko za pośrednictwem odwołania do bieżącego`this` wystąpienia C#(w), które jest rzutowane do interfejsu. Jeśli typ pochodny ponownie implementuje metodę dziedziczonego interfejsu (jawnie), nie można już uzyskać dostępu do implementacji podstawowej. Wywołanie przez odwołanie do bieżącego wystąpienia wywoła implementację pochodną; powoduje to rekursję i ostateczne przepełnienie stosu.

Ta zasada nie zgłasza naruszenia dla jawnej implementacji <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> , gdy podano zewnętrznie widoczną `Close()` lub `System.IDisposable.Dispose(Boolean)` metodę.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, zaimplementuj nową metodę, która uwidacznia te same funkcje i jest widoczna dla typów pochodnych lub Zmień na niejawną implementację. W przypadku akceptowalnej zmiany istotne jest, aby typ był zapieczętowany.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Jeśli podano zewnętrznie widoczną metodę, która ma taką samą funkcjonalność, ale inną niż jawnie zaimplementowaną metodę, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje typ, `ViolatingBase`, który narusza regułę i typ, `FixedBase`, który pokazuje poprawkę dla naruszenia.

[!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]

## <a name="see-also"></a>Zobacz także
[Interfejsy](/dotnet/csharp/programming-guide/interfaces/index)