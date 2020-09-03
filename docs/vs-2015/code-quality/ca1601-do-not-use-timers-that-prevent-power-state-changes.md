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
ms.openlocfilehash: 7928b2fff8c12ca3f0cc3c58bee31fe5809517e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545642"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: Nie używaj czasomierzy, które uniemożliwiają zmiany stanu zasilania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
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
