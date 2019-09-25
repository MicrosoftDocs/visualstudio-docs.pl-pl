---
title: 'CA1601: Nie używaj czasomierzy, które uniemożliwiają zmiany stanu zasilania'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1300b733cbd4808359089787ceebeb0750de6723
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234346"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: Nie używaj czasomierzy, które uniemożliwiają zmiany stanu zasilania

|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Kategoria|Microsoft. Mobility|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Czasomierz ma ustawiony interwał, który ma być wykonywany więcej niż jeden raz na sekundę.

## <a name="rule-description"></a>Opis reguły
Nie sondowaj więcej niż jeden raz na sekundę lub użyj czasomierzy, które wystąpiły częściej niż jeden raz na sekundę. Wyższa częstotliwość działań okresowych sprawi, że procesor będzie zajęty, co zakłóci działanie czasomierzy bezczynności oszczędzających energię, które wyłączają ekran i dyski twarde.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Ustaw interwały czasomierza, które mają być wykonywane krócej niż jeden raz na sekundę.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Ta reguła powinna być pomijana tylko wtedy, gdy jest wymagane wyzwolenie czasomierza więcej niż jeden raz na sekundę, a zagadnienia dotyczące mobilności można bezpiecznie zignorować.