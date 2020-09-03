---
title: 'CA1505: Unikaj niemożliwego do utrzymania kodu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0f2f731b1ac0d87b59c7690d0cf57ade3570ed5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547826"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: Unikaj kodu trudnego w utrzymaniu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|Kategoria|Microsoft. łatwość obsługi|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Typ lub metoda ma niską wartość indeksu konserwacji.

## <a name="rule-description"></a>Opis reguły
 Indeks utrzymania jest obliczany przy użyciu następujących metryk: wierszy kodu, woluminu programowego i złożoności cyklomatyczna. Wolumin programu to miara trudności w zrozumieniu typu lub metody, która jest oparta na liczbie operatorów i operandów w kodzie. Złożoność cyklomatyczna jest miarą złożoności strukturalnej typu lub metody. Możesz dowiedzieć się więcej o metrykach kodu podczas [mierzenia złożoności i utrzymania kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).

 Niski indeks utrzymania wskazuje, że typ lub metoda prawdopodobnie trudno jest zachować i będzie to dobry kandydat do przeprojektowania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać ten problem, Zaprojektuj typ lub metodę, a następnie spróbuj podzielić go na mniejsze i bardziej ukierunkowane typy lub metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Wyklucz to ostrzeżenie, gdy typ lub metoda nadal są uznawane za utrzymane pomimo jego dużego rozmiaru lub kiedy nie można podzielić typu lub metody.

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia dotyczące utrzymania](../code-quality/maintainability-warnings.md) [mierzące złożoność i łatwość utrzymania kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
