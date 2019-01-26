---
title: 'CA2104: Nie deklaruj modyfikowalnych typów referencyjnych tylko do odczytu'
ms.date: 11/01/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8c1e2ceed83564c5ccdd6de87eefe3537b410612
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037671"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Nie deklaruj modyfikowalnych typów referencyjnych tylko do odczytu

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

> [!NOTE]
> CA2104 reguły jest przestarzały i zostanie usunięta w przyszłych wersjach programu Visual Studio.

## <a name="cause"></a>Przyczyna

Typ widoczny z zewnątrz zawiera widoczne na zewnątrz pole tylko do odczytu, które jest typu referencji zmiennej.

## <a name="rule-description"></a>Opis reguły

Typ zmienny to typ, którego dane wystąpienia mogą być modyfikowane. <xref:System.Text.StringBuilder?displayProperty=fullName> Klasy jest przykładem typu referencji zmiennej. Zawiera elementy członkowskie, które można zmienić wartość wystąpienia klasy. Na przykład typ referencyjny niezmienne <xref:System.String?displayProperty=fullName> klasy. Po utworzeniu wystąpienia, jego wartość nigdy nie można zmienić.

Modyfikator tylko do odczytu ([tylko do odczytu](/dotnet/csharp/language-reference/keywords/readonly) w C#, [tylko do odczytu](/dotnet/visual-basic/language-reference/modifiers/readonly) w języku Visual Basic i [const](/cpp/cpp/const-cpp) w języku C++) na typ referencyjny zapobiega pola z pola (lub wskaźnika w języku C++) zastępowane przez inne wystąpienie typu referencyjnego. Jednak modyfikator nie uniemożliwia dane wystąpienia pola modyfikowana za pomocą typu odwołania.

Ta zasada może przypadkowo Pokaż naruszenie dla typu, jest rzeczywiście, niezmienne. W takiej sytuacji jest bezpieczne pominąć to ostrzeżenie.

Pola tablicy tylko do odczytu są wykluczone z tej reguły, ale zamiast tego spowodować naruszenie [CA2105: Pola tablicy nie można odczytać tylko](../code-quality/ca2105-array-fields-should-not-be-read-only.md) reguły.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy usunąć modyfikatora tylko do odczytu lub, jeśli istotną zmianę, Zastąp pole z typem niezmienne.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli typ pola jest niezmienny.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia deklarację pola, która powoduje naruszenie tej zasady:

[!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
[!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
[!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]