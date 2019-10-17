---
title: 'CA1034: Zagnieżdżone typy nie powinny być widoczne'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0726b6f02de37c9a5537db59b264802c3dad9a07
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440863"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: Zagnieżdżone typy nie powinny być widoczne

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|Kategoria|Microsoft. Design|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ widoczny na zewnątrz zawiera niejawnie widoczną deklarację typu. Zagnieżdżone wyliczenia i typy chronione są wykluczone z tej reguły.

## <a name="rule-description"></a>Opis reguły
Typ zagnieżdżony jest zadeklarowany w zakresie innego typu. Zagnieżdżone typy są przydatne do hermetyzowania prywatnych szczegółów implementacji typu zawierającego. Używane w tym celu typy zagnieżdżone nie powinny być widoczne na zewnątrz.

Nie należy używać widocznych na zewnątrz zagnieżdżonych typów dla logicznego grupowania lub w celu uniknięcia kolizji nazw; Zamiast tego należy użyć przestrzeni nazw.

Zagnieżdżone typy obejmują pojęcie dostępności elementów członkowskich, które nie są jasno zrozumiałe dla niektórych programistów.

Typy chronione mogą być używane w podklasach i zagnieżdżonych typach w scenariuszach dostosowywania z wyprzedzeniem.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Jeśli typ zagnieżdżony nie ma być widoczny na zewnątrz, Zmień dostępność typu. W przeciwnym razie Usuń Typ zagnieżdżony z jego elementu nadrzędnego. Jeśli celem zagnieżdżenia jest kategoryzowanie typu zagnieżdżonego, zamiast tego należy użyć przestrzeni nazw do utworzenia hierarchii.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje typ, który narusza regułę.

[!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
[!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
[!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]
