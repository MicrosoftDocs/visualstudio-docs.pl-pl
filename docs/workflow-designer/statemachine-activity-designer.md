---
title: Projektant przepływu pracy — Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: e7a270780a953a6104adc7089a02ff6529106fdf
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593138"
---
# <a name="statemachine-activity-designer"></a>StateMachine, projektant działań

Działanie <xref:System.Activities.Statements.StateMachine> zawiera kolekcję przepływów pracy stanów i modeli przy użyciu modelu z znaną maszyną stanu.

## <a name="using-the-statemachine-activity-designer"></a>Korzystanie z projektanta działań StateMachine

Aby dodać działanie <xref:System.Activities.Statements.StateMachine>, przeciągnij projektanta działań **StateMachine** z sekcji **stan automatu** w **przyborniku** i upuść go na powierzchni Projektant przepływu pracy. Aby dodać stan podrzędny do tego działania <xref:System.Activities.Statements.StateMachine>, przeciągnij <xref:System.Activities.Statements.State> lub <xref:System.Activities.Core.Presentation.FinalState> z **przybornika** i upuść go na obiekt **StateMachine**.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Właściwości działania StateMachine w Projektant przepływu pracy

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.StateMachine>, które można ustawić za pomocą projektanta przepływów pracy, i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na powierzchni projektanta.

|Nazwa właściwości|Wymagane|Pomiar|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa przyjazną nazwę <xref:System.Activities.Statements.StateMachine> projektanta działań w nagłówku. Wartość domyślna to **StateMachine**. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku projektanta działań. <xref:System.Activities.Activity.DisplayName%2A> jest używana w nawigacyjnym nawigacji, który jest wyświetlany w górnej części projektanta przepływu pracy.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|

## <a name="see-also"></a>Zobacz także

- [Schemat blokowy](../workflow-designer/flowchart-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
