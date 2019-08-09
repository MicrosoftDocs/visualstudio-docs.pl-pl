---
title: 'CA1600: Nie używaj priorytetu procesu o wartości Bezczynny'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c37affc585653807912d00c1cfe365853fd6260b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921811"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Nie używaj priorytetu procesu o wartości Bezczynny

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Kategoria|Microsoft. Mobility|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Ta reguła występuje, gdy procesy są ustawione `ProcessPriorityClass.Idle`na.

## <a name="rule-description"></a>Opis reguły
Nie należy ustawiać priorytetu procesu na Idle. Procesy, które `System.Diagnostics.ProcessPriorityClass.Idle` mają zajmować procesor CPU, gdy byłyby w stanie bezczynności, w związku z tym blokują zablokowanie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Ustaw procesy na `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Ta reguła powinna być pomijana tylko wtedy, gdy wymagany jest priorytet bezczynnego procesu, a zagadnienia dotyczące mobilności można bezpiecznie zignorować.