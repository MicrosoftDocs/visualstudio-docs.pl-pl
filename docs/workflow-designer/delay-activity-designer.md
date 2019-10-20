---
title: Projektant przepływu pracy — Projektant działań z opóźnieniem
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5190807bba08f05e176acc15ac8daf42ac028c50
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650544"
---
# <a name="delay-activity-designer"></a>Delay, projektant działań

Projektant działań **opóźnionych** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.Delay>.

## <a name="the-delay-activity"></a>Działanie Opóźnij

Działanie <xref:System.Activities.Statements.Delay> opóźnia wykonywanie przepływu pracy przez określoną ilość czasu.

### <a name="use-the-delay-activity-designer"></a>Korzystanie z projektanta działań opóźnionych

Projektanta aktywności **opóźnienia** można znaleźć w kategorii elementy **pierwotne** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** w Projektant przepływu pracy. Alternatywnie wybierz pozycję **Przybornik** z menu **Widok** lub naciśnij **klawisze CTRL** +**Alt** +**X**.

Projektanta aktywności **opóźnienia** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence>. Porzucenie projektanta działań powoduje utworzenie <xref:System.Activities.Statements.Delay> działania z domyślnym <xref:System.Activities.Activity.DisplayName%2A> opóźnienia. @No__t_0 można edytować w nagłówku projektanta działań **opóźnionych** lub w polu **DisplayName** siatki właściwości.

### <a name="the-delay-properties"></a>Właściwości opóźnienia

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.Delay> i opisano, jak są one używane w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na powierzchni Projektant przepływu pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa działania <xref:System.Activities.Statements.Delay>. Wartość domyślna to opóźnienie. Mimo że wartość <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Oznacza|Czas opóźnienia przepływu pracy. Ta właściwość jest ustawiana w siatce właściwości. Wpisz literał <xref:System.TimeSpan> w formacie 00:00:00 lub Visual Basic wyrażenie, aby określić ilość czasu.|

## <a name="see-also"></a>Zobacz także

- [Typy pierwotne](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay, projektant działań](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)