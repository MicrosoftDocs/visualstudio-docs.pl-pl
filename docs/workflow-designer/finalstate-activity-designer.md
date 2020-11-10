---
title: Projektant przepływu pracy — Projektant działań FinalState
description: Dowiedz się, jak za pomocą projektanta FinalState utworzyć stan kończący wystąpienie komputera stanu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2af8887a11b04679789f57f15f32ca03b7b4acf3
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435824"
---
# <a name="finalstate-activity-designer"></a>FinalState, projektant działań

<xref:System.Activities.Core.Presentation.FinalState>Projektant służy do tworzenia <xref:System.Activities.Statements.State> , który kończy wystąpienie komputera stanu.

## <a name="using-the-finalstate-activity-designer"></a>Korzystanie z projektanta działań FinalState

Projektant **FinalState** służy do tworzenia <xref:System.Activities.Statements.State> wstępnie skonfigurowanego stanu zakończenia w maszynie stanu. Obiekt <xref:System.Activities.Statements.State> , który jest tworzony przy użyciu <xref:System.Activities.Core.Presentation.FinalState> projektanta działań <xref:System.Activities.Statements.State.IsFinal%2A> , ma właściwość ustawioną na **wartość true** , nie ma <xref:System.Activities.Statements.State.Exit%2A> działania i nie pochodzi od niego przejścia. Aby skorzystać z <xref:System.Activities.Core.Presentation.FinalState> projektanta działań w celu dodania <xref:System.Activities.Statements.State> działania, które jest wstępnie skonfigurowane jako stan zakończenia na komputerze stanu, przeciągnij projektanta działań **FinalState** z sekcji **stan komputera** **przybornika** i upuść go w Projektancie przepływu pracy. <xref:System.Activities.Core.Presentation.FinalState>Projektanta aktywności można porzucić do <xref:System.Activities.Statements.StateMachine> i przejoć później, lub można utworzyć przejście, gdy <xref:System.Activities.Core.Presentation.FinalState> Projektant działań zostanie porzucony. Aby uzyskać więcej informacji na temat tworzenia przejść, zobacz [Przechodzenie](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Właściwości działania stanu w Projektant przepływu pracy

W poniższej tabeli przedstawiono właściwości, które można ustawić za pomocą <xref:System.Activities.Core.Presentation.FinalState> projektanta, i opisano sposób ich użycia w projektancie. Niektóre z tych właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na powierzchni projektanta.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Fałsz|Określa przyjazną nazwę <xref:System.Activities.Statements.State> projektanta działań w nagłówku. Wartość domyślna to **State**. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku projektanta działań. Ta wartość <xref:System.Activities.Statements.State.DisplayName%2A> jest używana w nawigacyjnym nawigacji, który jest wyświetlany w górnej części projektanta przepływu pracy.<br /><br /> Chociaż <xref:System.Activities.Statements.State.DisplayName%2A> nie jest to ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.State.Entry%2A>|Fałsz|Określa akcję, która występuje, gdy ten stan jest przenoszony do. Tę wartość można ustawić, przeciągając działanie z **przybornika** i upuszczając je na <xref:System.Activities.Statements.State.Entry%2A> sekcję stanu.|

## <a name="see-also"></a>Zobacz też

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [Stan](../workflow-designer/state-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)