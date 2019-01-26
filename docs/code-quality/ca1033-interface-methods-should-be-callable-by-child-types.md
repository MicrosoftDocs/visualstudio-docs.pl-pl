---
title: 'CA1033: Metody interfejsu powinny móc zostać wywołane przez typy podrzędne'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: c6d1fa4152b0906db89efbb4df68356c58c60416
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996535"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: Metody interfejsu powinny móc zostać wywołane przez typy podrzędne

|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Niezapieczętowany typ widoczny na zewnątrz zapewnia jawną implementację metody interfejsu publicznego i nie dostarcza alternatywnej metody widocznej z zewnątrz o tej samej nazwie.

## <a name="rule-description"></a>Opis reguły
 Należy wziąć pod uwagę typu podstawowego, który jawnie implementuje metodę interfejsu publicznego. Typ, który pochodzi od typu podstawowego mogą uzyskiwać dostęp do metody dziedziczony interfejs wyłącznie za pośrednictwem odwołanie do bieżącego wystąpienia (`this` w języku C#), jest rzutowane na interfejs. Jeśli typ pochodny reimplements (jawne) metoda dziedziczony interfejs, Podstawowa implementacja nie jest już możliwy. Wywołanie przez odwołanie do bieżącego wystąpienia wywoła pochodnej; Powoduje to rekursji i przepełnienie stosu ostateczną.

 Ta zasada zgłasza naruszenie dla jawnych implementacji <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> gdy jest to widoczne na zewnątrz `Close()` lub `System.IDisposable.Dispose(Boolean)` podana metoda.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, zaimplementuj nową metodę uwidacznia taką samą funkcjonalność, która jest widoczna dla typów pochodnych, lub zmień niejawne implementacji. Jeśli istotną zmianę, alternatywą jest zapewnienie typu zapieczętowany.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli metoda widoczna na zewnątrz, ma taką samą funkcjonalność, ale inną nazwę niż metoda jawnie implementowane.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano typu, `ViolatingBase`, który narusza regułę i typu `FixedBase`, który zawiera poprawkę rozwiązującą naruszenia.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]

## <a name="see-also"></a>Zobacz także
 [Interfejsy](/dotnet/csharp/programming-guide/interfaces/index)