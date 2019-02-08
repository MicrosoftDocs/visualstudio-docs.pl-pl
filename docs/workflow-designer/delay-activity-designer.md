---
title: Projektant przepływu pracy — Delay, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e69c82899cb5f7aa24235641ae517709686170a7
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55932849"
---
# <a name="delay-activity-designer"></a>Delay, projektant działań

**Opóźnienie** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Delay> działania.

## <a name="the-delay-activity"></a>Działanie opóźnienia

<xref:System.Activities.Statements.Delay> Działania opóźnia wykonywania przepływu pracy przez określony przedział czasu.

### <a name="use-the-delay-activity-designer"></a>Użyj Delay, Projektant działań

**Opóźnienie** projektanta działań można znaleźć w **podstawowych** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**kartę projektanta przepływów pracy. Można także wybrać **przybornika** z **widoku** menu lub naciśnij klawisz **Ctrl**+**Alt** + **X**.

**Opóźnienie** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy wszędzie tam, gdzie działań są zazwyczaj umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Projektant działań porzucenie tworzy <xref:System.Activities.Statements.Delay> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> z opóźnieniem. <xref:System.Activities.Activity.DisplayName%2A> Mogą być edytowane w nagłówku **opóźnienie** projektanta działań lub **DisplayName** pola siatki właściwości.

### <a name="the-delay-properties"></a>Właściwości opóźnienia

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Delay> właściwości oraz opisano sposoby ich używania w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich mogą być edytowane na powierzchni projektanta przepływów pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.Delay> działania. Wartość domyślna to opóźnienie. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest bezwzględnie konieczne, jest najlepszym rozwiązaniem, aby użyć jednego.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Prawda|Ilość czasu, opóźnienie przepływu pracy. Ta właściwość jest ustawiona w siatce właściwości. Wpisz jeden literał <xref:System.TimeSpan> w formacie 00:00:00 lub wyrażenie języka Visual Basic, aby określić ilość czasu.|

## <a name="see-also"></a>Zobacz także

- [Typy pierwotne](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay, projektant działań](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)