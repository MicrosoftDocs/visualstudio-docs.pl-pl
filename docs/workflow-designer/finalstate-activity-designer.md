---
title: Projektant przepływu pracy — Projektant działań FinalState
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: b8f25167f3a67e2d1349354ce568c076697e3e73
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650475"
---
# <a name="finalstate-activity-designer"></a>FinalState, projektant działań

Projektant <xref:System.Activities.Core.Presentation.FinalState> służy do tworzenia <xref:System.Activities.Statements.State> kończącego wystąpienie komputera stanu.

## <a name="using-the-finalstate-activity-designer"></a>Korzystanie z projektanta działań FinalState

Projektant **FinalState** jest używany do tworzenia <xref:System.Activities.Statements.State>, który jest wstępnie skonfigurowany jako stan zakończenia na komputerze stanu. @No__t_0, który jest tworzony przy użyciu projektanta działań <xref:System.Activities.Core.Presentation.FinalState>, ma właściwość <xref:System.Activities.Statements.State.IsFinal%2A> ustawioną na **wartość true**, nie ma działania <xref:System.Activities.Statements.State.Exit%2A> i nie pochodzą z niego przejścia. Aby użyć <xref:System.Activities.Core.Presentation.FinalState> Projektant działań w celu dodania działania <xref:System.Activities.Statements.State>, które jest wstępnie skonfigurowane jako stan zakończenia na komputerze stanu, przeciągnij projektanta działań **FinalState** z sekcji **stan komputera** **przybornika** i upuść go na Projektant przepływu pracy. @No__t_0 projektanta działań można porzucić na <xref:System.Activities.Statements.StateMachine> i przejścia później. lub można utworzyć przejście, gdy <xref:System.Activities.Core.Presentation.FinalState> projektanta działań zostanie porzucony. Aby uzyskać więcej informacji na temat tworzenia przejść, zobacz [Przechodzenie](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Właściwości działania stanu w Projektant przepływu pracy

W poniższej tabeli przedstawiono właściwości, które można ustawić za pomocą projektanta <xref:System.Activities.Core.Presentation.FinalState>, i opisano sposób ich użycia w projektancie. Niektóre z tych właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na powierzchni projektanta.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.State> projektanta działań w nagłówku. Wartość domyślna to **State**. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku projektanta działań. @No__t_0 jest używana w nawigacyjnym nawigacji, który jest wyświetlany w górnej części projektanta przepływu pracy.<br /><br /> Mimo że <xref:System.Activities.Statements.State.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Określa akcję, która występuje, gdy ten stan jest przenoszony do. Tę wartość można ustawić, przeciągając działanie z **przybornika** i upuszczając je w sekcji <xref:System.Activities.Statements.State.Entry%2A> stanu.|

## <a name="see-also"></a>Zobacz także

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [State](../workflow-designer/state-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)