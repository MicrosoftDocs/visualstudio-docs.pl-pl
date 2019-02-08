---
title: Projektant przepływu pracy — Jeśli Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 762199906bbb84701c044b5fa9f3f3b8c6fdfdae
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55916976"
---
# <a name="if-activity-designer"></a>If, projektant działań

<xref:System.Activities.Statements.If> Działanie sprawdza warunek i wykonuje działanie w zależności od wyników tej oceny. To działanie jest najbardziej użyteczna, korzystając z procedur, modelowanie stylu programowania. <xref:System.Activities.Statements.If> Działania mogą być zagnieżdżone wewnątrz <xref:System.Activities.Statements.Sequence> działania lub <xref:System.Activities.Statements.Parallel> działania, na przykład. Jeśli używasz <xref:System.Activities.Statements.Flowchart> działanie, należy rozważyć użycie <xref:System.Activities.Statements.FlowDecision> działania zamiast tego.

## <a name="if-properties-in-the-workflow-designer"></a>Jeśli właściwości w Projektancie przepływu pracy

W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.If> właściwości działań i informacje dotyczące używania ich w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|Prawda|Warunek, który określa, które działania podrzędnego do wykonania. Aby ustawić <xref:System.Activities.Statements.If.Condition%2A>, wpisz wyrażenie języka Visual Basic w **warunek** polu na **Jeśli** działanie projektanta lub w siatce właściwości.|
|<xref:System.Activities.Statements.If.Else%2A>|False|Działanie do wykonania, jeśli <xref:System.Activities.Statements.If.Condition%2A> jest **false**. Można dodać działania wykonywane przez <xref:System.Activities.Statements.If.Else%2A> gałęzi, Porzuć działania z **przybornika** do **Else** polu na **Jeśli** projektanta działań z tekst wskazówki " Upuść działanie tutaj".|
|<xref:System.Activities.Statements.If.Then%2A>|False|Działanie do wykonania, jeśli <xref:System.Activities.Statements.If.Condition%2A> jest **true**. Można dodać działania wykonywane przez <xref:System.Activities.Statements.If.Then%2A> gałęzi, Porzuć działania z **przybornika** do **następnie** polu na **Jeśli** projektanta działań z tekst wskazówki " Upuść działanie tutaj".|

## <a name="see-also"></a>Zobacz także

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)