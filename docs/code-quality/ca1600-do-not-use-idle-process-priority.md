---
title: 'CA1600: Nie używaj priorytetu procesu o wartości Bezczynny'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: f9eb25ace4ee255348f616abefcccd84713715ff
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037528"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Nie używaj priorytetu procesu o wartości Bezczynny

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Kategoria|Microsoft.Mobility|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Ta reguła jest uruchamiana podczas procesów są ustawione na `ProcessPriorityClass.Idle`.

## <a name="rule-description"></a>Opis reguły
 Nie należy ustawiać priorytetu procesu na Idle. Procesy, które mają `System.Diagnostics.ProcessPriorityClass.Idle` , zajmują Procesor, może być bezczynne, a zatem będą blokować stan wstrzymania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Ustaw procesy `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Ta reguła ma być pomijana, tylko wtedy, gdy priorytetu procesu bezczynności jest wymagany i zagadnienia dotyczące mobilności można bezpiecznie zignorować.