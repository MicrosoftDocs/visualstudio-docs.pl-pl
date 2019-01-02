---
title: 'CA1052: Statyczne typy przechowujące powinny być zapieczętowane'
ms.date: 11/09/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0ec090fd11c122699bafb3d72ca1eeab13ecb830
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825948"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: Statyczne typy przechowujące powinny być zapieczętowane

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Publiczny lub chroniony, nieabstrakcyjnej typ zawiera tylko statyczne elementy członkowskie i nie jest zadeklarowana za pomocą [zapieczętowanego](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) modyfikator.

## <a name="rule-description"></a>Opis reguły

CA1052 reguły przyjęto założenie, że typ, który zawiera tylko statyczne elementy członkowskie nie służy do dziedziczone, ponieważ typ nie zapewnia żadnej funkcji, która może zostać zastąpiona w typie pochodnym. Typ, który nie jest przeznaczona do dziedziczone powinien być oznaczony przez `sealed` lub `NotInheritable` modyfikator, aby uniemożliwić jego użycie jako typu podstawowego. Ta zasada nie zostanie wywołane dla klasy abstrakcyjnej.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, oznacz typ jako `sealed` lub `NotInheritable`. Jeśli są przeznaczone dla .NET Framework 2.0 lub nowszej, lepszym rozwiązaniem jest Oznacz typ jako `static` lub `Shared`. W ten sposób nie trzeba zadeklarować Konstruktor prywatny, aby uniemożliwić tworzonych przez klasy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Pomijaj ostrzeżeń dla tej reguły, tylko wtedy, gdy typ jest przeznaczony do być dziedziczona. Brak `sealed` lub `NotInheritable` modyfikator sugeruje, że typ jest przydatne jako typu podstawowego.

## <a name="example-of-a-violation"></a>Przykładem naruszenia

Poniższy przykład pokazuje typ, który narusza regułę.

[!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
[!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
[!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Usuń z modyfikator statyczny

Poniższy przykład pokazuje, jak naprawić naruszenie tej zasady, oznaczając typu za pomocą `static` modyfikator w C#.

[!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>Powiązane reguły

[CA1053: Statyczne typy przechowujące nie powinny mieć konstruktorów](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)