---
title: Projektant przepływu pracy — Projektant działań z opóźnieniem
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: abfd625a248c14f646683c7b035065e6ca096f68
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876115"
---
# <a name="delay-activity-designer"></a>Delay, projektant działań

Projektant działań **opóźnionych** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Delay> działania.

## <a name="the-delay-activity"></a>Działanie Opóźnij

<xref:System.Activities.Statements.Delay>Działanie opóźnia wykonywanie przepływu pracy przez określoną ilość czasu.

### <a name="use-the-delay-activity-designer"></a>Korzystanie z projektanta działań opóźnionych

Projektanta aktywności **opóźnienia** można znaleźć w kategorii elementy **pierwotne** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** w Projektant przepływu pracy. Alternatywnie możesz wybrać **Przybornik** z menu **Widok** lub nacisnąć **klawisze CTRL** + **Alt** + **X**.

Projektanta aktywności **opóźnienia** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Porzucenie projektanta działań powoduje utworzenie <xref:System.Activities.Statements.Delay> działania z domyślnym <xref:System.Activities.Activity.DisplayName%2A> opóźnieniem. <xref:System.Activities.Activity.DisplayName%2A>Można edytować w nagłówku projektanta działań **opóźnionych** lub w polu **DisplayName** siatki właściwości.

### <a name="the-delay-properties"></a>Właściwości opóźnienia

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Delay> właściwości i opisano, jak są one używane w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na powierzchni Projektant przepływu pracy.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa <xref:System.Activities.Statements.Delay> działania. Wartość domyślna to opóźnienie. Chociaż <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Prawda|Czas opóźnienia przepływu pracy. Ta właściwość jest ustawiana w siatce właściwości. Wpisz w postaci literału w <xref:System.TimeSpan> formacie 00:00:00 lub Visual Basic wyrażenie, aby określić ilość czasu.|

## <a name="see-also"></a>Zobacz także

- [Typy pierwotne](../workflow-designer/primitives-activity-designers.md)
- [Ponownie](../workflow-designer/assign-activity-designer.md)
- [Delay, projektant działań](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)