---
title: 'CA1034: Typy zagnieżdżone nie powinny być widoczne'
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
ms.openlocfilehash: ead932af202bd1a44464025a1b09baa698acb7b1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236033"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: Typy zagnieżdżone nie powinny być widoczne

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|Kategoria|Microsoft.Design|
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