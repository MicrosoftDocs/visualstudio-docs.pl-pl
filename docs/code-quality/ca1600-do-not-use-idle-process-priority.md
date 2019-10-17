---
title: 'CA1600: Nie używaj priorytetu procesu bezczynności'
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
ms.openlocfilehash: 2075918672452e222ba4becae915712ba20ff0d0
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440015"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Nie używaj priorytetu procesu bezczynności

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Kategoria|Microsoft. Mobility|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Ta reguła występuje, gdy dla procesów ustawiono wartość `ProcessPriorityClass.Idle`.

## <a name="rule-description"></a>Opis reguły
Nie należy ustawiać priorytetu procesu na Idle. Procesy, które mają `System.Diagnostics.ProcessPriorityClass.Idle` będą zajmowały procesor CPU, gdy będzie w przeciwnym razie w stanie bezczynności.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Ustaw procesy na `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Ta reguła powinna być pomijana tylko wtedy, gdy wymagany jest priorytet bezczynnego procesu, a zagadnienia dotyczące mobilności można bezpiecznie zignorować.
