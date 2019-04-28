---
title: Projektant przepływu pracy — FinalState, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 8292e22bac6063a36286930584e1d7c227913511
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949702"
---
# <a name="finalstate-activity-designer"></a>FinalState, projektant działań

<xref:System.Activities.Core.Presentation.FinalState> Projektanta jest używany do tworzenia <xref:System.Activities.Statements.State> kończy się wystąpienia maszyny stanu.

## <a name="using-the-finalstate-activity-designer"></a>Za pomocą FinalState, Projektant działań

**FinalState** projektanta jest używany do tworzenia <xref:System.Activities.Statements.State> który został wstępnie skonfigurowany jako kończący stan w automacie stanów. A <xref:System.Activities.Statements.State> utworzonego za pomocą <xref:System.Activities.Core.Presentation.FinalState> ma projektanta działań jego <xref:System.Activities.Statements.State.IsFinal%2A> właściwością **true**, nie ma <xref:System.Activities.Statements.State.Exit%2A> działanie i żadnych przejść pochodzących z niego. Aby użyć <xref:System.Activities.Core.Presentation.FinalState> projektanta działań, aby dodać <xref:System.Activities.Statements.State> przeciągnij działanie, które są wstępnie skonfigurowane jako kończący stan w automacie stanów **FinalState** projektanta działań z **automatu stanów**części **przybornika** i upuść go na projektanta przepływów pracy. <xref:System.Activities.Core.Presentation.FinalState> Projektanta działań może być upuszczone na <xref:System.Activities.Statements.StateMachine> i przejść, dodane później; lub przejścia mogą być tworzone jako <xref:System.Activities.Core.Presentation.FinalState> projektanta działań jest porzucany. Aby uzyskać więcej informacji na temat tworzenia przejścia, zobacz [przejścia](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Właściwości stanu działania w Projektancie przepływu pracy

W poniższej tabeli przedstawiono właściwości, które można ustawić za pomocą <xref:System.Activities.Core.Presentation.FinalState> projektanta i w tym artykule opisano, jak są używane w projektancie. Niektóre z tych właściwości można edytować w siatce właściwości, a niektóre z nich mogą być edytowane na powierzchni projektowej.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.State> projektanta działań w nagłówku. Wartość domyślna to **stanu**. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku projektanta działań. <xref:System.Activities.Statements.State.DisplayName%2A> Jest używany w nadrzędnych, która jest wyświetlana w górnej części projektanta przepływów pracy.<br /><br /> Mimo że <xref:System.Activities.Statements.State.DisplayName%2A> nie jest bezwzględnie konieczne jest najlepszym rozwiązaniem, aby użyć jednego.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Określa akcję, która występuje, gdy ten stan jest przenoszone do. Tę wartość można ustawić, przeciągając działanie w **przybornika** i upuszczając go na <xref:System.Activities.Statements.State.Entry%2A> sekcja stanu.|

## <a name="see-also"></a>Zobacz także

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [State](../workflow-designer/state-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)