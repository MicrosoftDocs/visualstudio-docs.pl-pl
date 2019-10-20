---
title: 'CA1600: nie używaj priorytetu procesu bezczynności | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d4260db808d9c50f78388cf6ba976f7ace52e6a3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669297"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Nie używaj priorytetu procesu bezczynności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Kategoria|Microsoft. Mobility|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Ta reguła występuje, gdy dla procesów ustawiono wartość `ProcessPriorityClass.Idle`.

## <a name="rule-description"></a>Opis reguły
 Nie należy ustawiać priorytetu procesu na Idle. Procesy, które mają `System.Diagnostics.ProcessPriorityClass.Idle` będą zajmowały procesor CPU, gdy będzie w przeciwnym razie w stanie bezczynności.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Ustaw procesy na `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Ta reguła powinna być pomijana tylko wtedy, gdy wymagany jest priorytet bezczynnego procesu, a zagadnienia dotyczące mobilności można bezpiecznie zignorować.
