---
title: 'CA1601: nie używaj czasomierzy, które uniemożliwiają zmiany stanu baterii | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 95f13604908ad45c5f33a011fec886bba90d0bd8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669275"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: Nie używaj czasomierzy, które uniemożliwiają zmianę stanu zasilania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Kategoria|Microsoft. Mobility|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Czasomierz ma ustawiony interwał, który ma być wykonywany więcej niż jeden raz na sekundę.

## <a name="rule-description"></a>Opis reguły
 Nie sondowaj więcej niż jeden raz na sekundę lub użyj czasomierzy, które wystąpiły częściej niż jeden raz na sekundę. Wyższa częstotliwość działań okresowych sprawi, że procesor będzie zajęty, co zakłóci działanie czasomierzy bezczynności oszczędzających energię, które wyłączają ekran i dyski twarde.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Ustaw interwały czasomierza, które mają być wykonywane krócej niż jeden raz na sekundę.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Ta reguła powinna być pomijana tylko wtedy, gdy jest wymagane wyzwolenie czasomierza więcej niż jeden raz na sekundę, a zagadnienia dotyczące mobilności można bezpiecznie zignorować.
