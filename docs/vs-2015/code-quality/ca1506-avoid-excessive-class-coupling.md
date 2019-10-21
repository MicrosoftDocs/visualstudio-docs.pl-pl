---
title: 'CA1506: Unikaj nadmiernego sprzęgania klas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e85ac61e404ac9bc1afb9459716c2395233c5080
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607409"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Unikaj nadmiernego sprzężenia klas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Kategoria|Microsoft. łatwość obsługi|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ lub metoda jest sprzężona z wieloma innymi typami.

## <a name="rule-description"></a>Opis reguły
 Ta reguła mierzy sprzęgnięcie klasy przez liczenie unikatowych odwołań typów, które zawiera typ lub metoda.

 Typy i metody o wysokim stopniu sprzęgania klas mogą być trudne do utrzymania. Dobrym sposobem jest posiadanie typów i metod, które wykazują niskie sprzężenie i wysoką spójność.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać ten problem, spróbuj ponownie zaprojektować typ lub metodę w celu zmniejszenia liczby typów, do których jest sprzężona.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Wyklucz to ostrzeżenie, gdy typ lub metoda nadal są uważane za utrzymane pomimo dużej liczby zależności od innych typów.

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia dotyczące utrzymania](../code-quality/maintainability-warnings.md) [mierzące złożoność i łatwość utrzymania kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
