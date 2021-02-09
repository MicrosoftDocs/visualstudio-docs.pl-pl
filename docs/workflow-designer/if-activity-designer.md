---
title: Projektant przepływu pracy — Jeśli Projektant działań
description: Dowiedz się, jak działanie if ocenia warunek i wykonuje działanie w zależności od wyników tej oceny.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 93f36a3c2b587718fe6889688baa50224f663c1c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881363"
---
# <a name="if-activity-designer"></a>If, projektant działań

<xref:System.Activities.Statements.If>Działanie ocenia warunek i wykonuje działanie w zależności od wyników tej oceny. To działanie jest najbardziej przydatne w przypadku korzystania z stylu modelowania proceduralnego programowania. <xref:System.Activities.Statements.If>Działanie może być na przykład zagnieżdżone w <xref:System.Activities.Statements.Sequence> działaniu lub <xref:System.Activities.Statements.Parallel> działaniu. W przypadku korzystania z <xref:System.Activities.Statements.Flowchart> działania należy rozważyć użycie <xref:System.Activities.Statements.FlowDecision> działania zamiast tego.

## <a name="if-properties-in-the-workflow-designer"></a>Jeśli właściwości w Projektant przepływu pracy

W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.If> właściwości działania i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|Prawda|Warunek określający działanie podrzędne, które ma zostać wykonane. Aby ustawić <xref:System.Activities.Statements.If.Condition%2A> , wpisz wyrażenie Visual Basic w polu **warunek** w projektancie działania **if** lub w siatce właściwości.|
|<xref:System.Activities.Statements.If.Else%2A>|Fałsz|Działanie do wykonania, jeśli <xref:System.Activities.Statements.If.Condition%2A> ma **wartość false**. Aby dodać działanie, które jest wykonywane przez <xref:System.Activities.Statements.If.Else%2A> gałąź, upuść działanie z **przybornika** do pola **else** w projektancie działania **if** z wskazówką text "Drop Activity tutaj".|
|<xref:System.Activities.Statements.If.Then%2A>|Fałsz|Działanie do wykonania, jeśli <xref:System.Activities.Statements.If.Condition%2A> ma **wartość true**. Aby dodać działanie, które jest wykonywane przez <xref:System.Activities.Statements.If.Then%2A> gałąź, upuść działanie z **przybornika** do pola **then** w projektancie działania w **przypadku, gdy** tekst wskazówki "upuść działanie tutaj".|

## <a name="see-also"></a>Zobacz też

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Równoległ](../workflow-designer/parallel-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
