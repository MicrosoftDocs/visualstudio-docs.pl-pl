---
title: 'CA1048: Nie deklaruj wirtualnych składowych w typach zapieczętowanych'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 430ed0b23d62bd46a9764bfb0a3834e0decd476b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922592"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: Nie deklaruj wirtualnych składowych w typach zapieczętowanych

|||
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Typ publiczny jest zapieczętowany i deklaruje metodę, która jest zarówno `virtual` (`Overridable` w Visual Basic), a nie końcową. Ta reguła nie zgłasza naruszeń dla typów delegatów, które muszą być zgodne z tym wzorcem.

## <a name="rule-description"></a>Opis reguły
Metody wirtualne są zadeklarowane w typach tak, aby typy dziedziczące mogły zmieniać implementację metod wirtualnych. Według definicji nie można dziedziczyć z typu zapieczętowanego, co oznacza, że metoda wirtualna w typie zapieczętowanym nie ma znaczenia.

Visual Basic i C# kompilatory nie zezwalają, aby typy naruszają tę regułę.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, ustaw metodę jako niewirtualną lub Zmień typ na dziedziczony.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły. Pozostawienie tego typu w bieżącym stanie może spowodować problemy z konserwacją i nie zapewnia żadnych korzyści.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje typ, który narusza tę regułę.

[!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]