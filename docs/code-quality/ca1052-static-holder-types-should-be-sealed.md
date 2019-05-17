---
title: 'CA1052: Statyczne typy przechowujące powinny być zapieczętowane'
ms.date: 03/11/2019
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
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 346a7f4cc7c7a8e6f579f94c6294ce9577fa01c7
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842094"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: Statyczne typy przechowujące powinny być zapieczętowane

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Typem nieabstrakcyjnym zawiera tylko statyczne elementy członkowskie i nie jest zadeklarowana za pomocą [zapieczętowanego](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) modyfikator.

Domyślnie ta reguła przegląda tylko typy widoczne na zewnątrz, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

CA1052 reguły przyjęto założenie, że typ, który zawiera tylko statyczne elementy członkowskie nie służy do dziedziczone, ponieważ typ nie zapewnia żadnej funkcji, która może zostać zastąpiona w typie pochodnym. Typ, który nie jest przeznaczona do dziedziczone powinien być oznaczony przez `sealed` lub `NotInheritable` modyfikator, aby uniemożliwić jego użycie jako typu podstawowego. Ta zasada nie zostanie wywołane dla klasy abstrakcyjnej.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, oznacz typ jako `sealed` lub `NotInheritable`. Jeśli są przeznaczone dla .NET Framework 2.0 lub nowszej, lepszym rozwiązaniem jest Oznacz typ jako `static` lub `Shared`. W ten sposób nie trzeba zadeklarować Konstruktor prywatny, aby uniemożliwić tworzonych przez klasy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Pomijaj ostrzeżeń dla tej reguły, tylko wtedy, gdy typ jest przeznaczony do być dziedziczona. Brak `sealed` lub `NotInheritable` modyfikator sugeruje, że typ jest przydatne jako typu podstawowego.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```ini
dotnet_code_quality.ca1052.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Przykładem naruszenia

Typ, który narusza regułę określającą, można znaleźć w poniższym przykładzie:

[!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
[!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
[!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Usuń z modyfikator statyczny

Poniższy przykład pokazuje, jak naprawić naruszenie tej zasady, oznaczając typu za pomocą `static` modyfikator w C#:

[!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1053: Statyczne typy przechowujące nie powinny mieć konstruktorów](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)