---
title: 'CA1048: Nie deklaruj wirtualnych składowych w typach zapieczętowanych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cdb2f9cfaa7f12d560601323a2fe96e74958fbd9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990969"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: Nie deklaruj wirtualnych składowych w typach zapieczętowanych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 Kompilatory języków Visual Basic .NET i języka C# nie zezwalają na typy narusza tę regułę.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, wprowadzić metody na niewirtualną lub zmień typ dziedziczone.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Pozostawienie typ w jego bieżącym stanie może spowodować problemy z konserwacji i nie zapewnia żadnych korzyści.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza tę regułę.

 [!code-cpp[FxCop.Design.SealedVirtual#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedVirtual/cpp/FxCop.Design.SealedVirtual.cpp#1)]
