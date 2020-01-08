---
title: Projektant przepływu pracy — Projektant działań stanu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: f1a95808ec19edba01b266ccd280603bcc4321dc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593151"
---
# <a name="state-activity-designer"></a>State, projektant działań

<xref:System.Activities.Statements.State> reprezentuje stan, w którym może znajdować się komputer stanu.

## <a name="using-the-state-activity-designer"></a>Korzystanie z programu Projektant działań stanu

Aby dodać <xref:System.Activities.Statements.State> do przepływu pracy, przeciągnij projektanta działań **stanu** z sekcji **stan komputera** **przybornika** i upuść go na działanie <xref:System.Activities.Statements.StateMachine> na Projektant przepływu pracy powierzchni. Działanie <xref:System.Activities.Statements.State> można porzucić do <xref:System.Activities.Statements.StateMachine> i przejść dodanych później; lub można utworzyć przejście, gdy działanie <xref:System.Activities.Statements.State> zostanie porzucone. Aby dodać działanie <xref:System.Activities.Statements.State> i utworzyć przejście w jednym kroku, przeciągnij działanie **stanu** z sekcji **stan automatu** **przybornika** i umieść je w innym stanie w Projektancie przepływu pracy. Gdy przeciągany <xref:System.Activities.Statements.State> jest nad innym <xref:System.Activities.Statements.State>, cztery Trójkąty będą widoczne wokół innych <xref:System.Activities.Statements.State>. Jeśli <xref:System.Activities.Statements.State> zostanie porzucone do jednego z czterech trójkątów, zostanie dodany do komputera stanu i zostanie utworzone przejście z <xref:System.Activities.Statements.State> źródłowej do usuniętej <xref:System.Activities.Statements.State>docelowej. Aby uzyskać więcej informacji, zobacz [Przechodzenie](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Właściwości działania stanu w Projektant przepływu pracy

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.State>, które można ustawić za pomocą projektanta przepływów pracy, i opisano sposób ich użycia w projektancie. Niektóre z tych właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na powierzchni projektanta.

|Nazwa właściwości|Wymagane|Pomiar|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Fałsz|Określa przyjazną nazwę <xref:System.Activities.Statements.State> projektanta działań w nagłówku. Wartość domyślna to **State**. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku projektanta działań. <xref:System.Activities.Statements.State.DisplayName%2A> jest używana w nawigacyjnym nawigacji, który jest wyświetlany w górnej części projektanta przepływu pracy.<br /><br /> Mimo że <xref:System.Activities.Statements.State.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.State.Entry%2A>|Fałsz|Określa akcję, która występuje, gdy ten stan jest przenoszony do. Po rozwinięciu działania <xref:System.Activities.Statements.State> tę wartość można ustawić, przeciągając działanie z **przybornika** i upuszczając je w sekcji **wpis** stanu.|
|<xref:System.Activities.Statements.State.Exit%2A>|Fałsz|Określa akcję, która występuje, gdy ten stan zostanie przeniesiony z. Po rozwinięciu działania <xref:System.Activities.Statements.State> tę wartość można ustawić, przeciągając działanie z **przybornika** i upuszczając je w sekcji **wyjście** stanu.|
|<xref:System.Activities.Statements.State.Transitions%2A>|Fałsz|Wyświetla listę możliwych przejść, które pochodzą z <xref:System.Activities.Statements.State>. Każdy element na liście ma link do skojarzonego <xref:System.Activities.Statements.Transition> i <xref:System.Activities.Statements.State>docelowej. Kliknięcie linku spowoduje przełączenie projektanta do rozwiniętego widoku <xref:System.Activities.Statements.Transition> lub <xref:System.Activities.Statements.State>.|

## <a name="see-also"></a>Zobacz także

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)
