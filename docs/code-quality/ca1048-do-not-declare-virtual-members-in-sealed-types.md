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
ms.openlocfilehash: 84db1db9061eff1373ee3ad4f0316a1f3dba0474
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55924503"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: Nie deklaruj wirtualnych składowych w typach zapieczętowanych

|||
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny jest zapieczętowany i deklaruje metodę, która jest zarówno `virtual` (`Overridable` w języku Visual Basic) i nie jest final. Ta zasada nie raportuje naruszenia typami delegatów, które muszą korzystać z tego wzoru.

## <a name="rule-description"></a>Opis reguły
 Metody wirtualne są zadeklarowane w typach tak, aby typy dziedziczące mogły zmieniać implementację metod wirtualnych. Zgodnie z definicją nie może dziedziczyć od typu zapieczętowanego podjęcia metoda wirtualna w typie zapieczętowanym ta nie ma znaczenia.

 Kompilatory języków Visual Basic i C# nie zezwalają na typy narusza tę regułę.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, wprowadzić metody na niewirtualną lub zmień typ dziedziczone.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Pozostawienie typ w jego bieżącym stanie może spowodować problemy z konserwacji i nie zapewnia żadnych korzyści.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza tę regułę.

 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]