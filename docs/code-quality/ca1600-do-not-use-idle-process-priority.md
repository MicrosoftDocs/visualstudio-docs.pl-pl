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
ms.openlocfilehash: 686929471ee8b6b5d1896f61bcbcd97a59135462
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234377"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Nie używaj priorytetu procesu o wartości Bezczynny

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Kategoria|Microsoft. Mobility|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Ta reguła występuje, gdy procesy są ustawione `ProcessPriorityClass.Idle`na.

## <a name="rule-description"></a>Opis reguły
Nie należy ustawiać priorytetu procesu na Idle. Procesy, które `System.Diagnostics.ProcessPriorityClass.Idle` mają zajmować procesor CPU, gdy byłyby w stanie bezczynności, w związku z tym blokują zablokowanie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Ustaw procesy na `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Ta reguła powinna być pomijana tylko wtedy, gdy wymagany jest priorytet bezczynnego procesu, a zagadnienia dotyczące mobilności można bezpiecznie zignorować.