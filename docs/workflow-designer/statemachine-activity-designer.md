---
title: Projektant przepływu pracy — Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 2e79e1db2cc6c46361afa7412cdeb493418c0365
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649912"
---
# <a name="statemachine-activity-designer"></a>StateMachine, projektant działań

Działanie <xref:System.Activities.Statements.StateMachine> zawiera kolekcję przepływów pracy stanów i modeli przy użyciu modelu z znaną maszyną stanu.

## <a name="using-the-statemachine-activity-designer"></a>Korzystanie z projektanta działań StateMachine

Aby dodać działanie <xref:System.Activities.Statements.StateMachine>, przeciągnij projektanta działań **StateMachine** z sekcji **stan automatu** w **przyborniku** i upuść go na powierzchni Projektant przepływu pracy. Aby dodać stan podrzędny do tego działania <xref:System.Activities.Statements.StateMachine>, przeciągnij <xref:System.Activities.Statements.State> lub <xref:System.Activities.Core.Presentation.FinalState> z **przybornika** i upuść go na obiekt **StateMachine**.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Właściwości działania StateMachine w Projektant przepływu pracy

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.StateMachine>, które można ustawić za pomocą projektanta przepływów pracy, i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na powierzchni projektanta.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.StateMachine> projektanta działań w nagłówku. Wartość domyślna to **StateMachine**. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku projektanta działań. @No__t_0 jest używana w nawigacyjnym nawigacji, który jest wyświetlany w górnej części projektanta przepływu pracy.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|

## <a name="see-also"></a>Zobacz także

- [Schemat blokowy](../workflow-designer/flowchart-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)