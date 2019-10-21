---
title: Projektant przepływu pracy — Jeśli Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e0c08d655393a953e1abae9d33086d43e281500
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650237"
---
# <a name="if-activity-designer"></a>If, projektant działań

Działanie <xref:System.Activities.Statements.If> ocenia warunek i wykonuje działanie w zależności od wyników tej oceny. To działanie jest najbardziej przydatne w przypadku korzystania z stylu modelowania proceduralnego programowania. Działanie <xref:System.Activities.Statements.If> może być zagnieżdżone w działaniu <xref:System.Activities.Statements.Sequence> lub działaniu <xref:System.Activities.Statements.Parallel>, na przykład. Jeśli używasz działania <xref:System.Activities.Statements.Flowchart>, rozważ użycie <xref:System.Activities.Statements.FlowDecision> działania.

## <a name="if-properties-in-the-workflow-designer"></a>Jeśli właściwości w Projektant przepływu pracy

W poniższej tabeli przedstawiono najbardziej przydatne właściwości działania <xref:System.Activities.Statements.If> i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|Oznacza|Warunek określający działanie podrzędne, które ma zostać wykonane. Aby ustawić <xref:System.Activities.Statements.If.Condition%2A>, wpisz wyrażenie Visual Basic w polu **warunek** w projektancie działania **if** lub w siatce właściwości.|
|<xref:System.Activities.Statements.If.Else%2A>|False|Działanie do wykonania, jeśli <xref:System.Activities.Statements.If.Condition%2A> ma **wartość false**. Aby dodać działanie, które jest wykonywane przez gałąź <xref:System.Activities.Statements.If.Else%2A>, upuść działanie z **przybornika** do pola **else** w projektancie działania **if** z wskazówką text "upuść aktywność tutaj".|
|<xref:System.Activities.Statements.If.Then%2A>|False|Działanie do wykonania, jeśli <xref:System.Activities.Statements.If.Condition%2A> ma **wartość true**. Aby dodać działanie, które jest wykonywane przez gałąź <xref:System.Activities.Statements.If.Then%2A>, upuść działanie z **przybornika** do pola **then** w projektancie aktywności, z wskazówką text " **upuść aktywność tutaj** ".|

## <a name="see-also"></a>Zobacz także

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)