---
title: Jeśli Projektant działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6b35fe7f1b55dde25ec896f230f66cef00d24eed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659058"
---
# <a name="if-activity-designer"></a>If, projektant działań
<xref:System.Activities.Statements.If>Działanie ocenia warunek i wykonuje działanie w zależności od wyników tej oceny. To działanie jest najbardziej przydatne w przypadku korzystania z stylu modelowania proceduralnego programowania. <xref:System.Activities.Statements.If>Działanie może być na przykład zagnieżdżone w <xref:System.Activities.Statements.Sequence> działaniu lub <xref:System.Activities.Statements.Parallel> działaniu. W przypadku korzystania z <xref:System.Activities.Statements.Flowchart> działania należy rozważyć użycie <xref:System.Activities.Statements.FlowDecision> działania zamiast tego.

## <a name="if-properties-in-the-workflow-designer"></a>Jeśli właściwości w Projektant przepływu pracy
 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.If> właściwości działania i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.If.Condition%2A>|Prawda|Warunek określający działanie podrzędne, które ma zostać wykonane. Aby ustawić <xref:System.Activities.Statements.If.Condition%2A> , wpisz [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] wyrażenie w polu **warunek** w projektancie działania **if** lub w siatce właściwości.|
|<xref:System.Activities.Statements.If.Else%2A>|Fałsz|Działanie do wykonania, jeśli <xref:System.Activities.Statements.If.Condition%2A> ma **wartość false**. Aby dodać działanie, które jest wykonywane przez <xref:System.Activities.Statements.If.Else%2A> gałąź, upuść działanie z **przybornika** do pola **else** w projektancie działania **if** z wskazówką text "Drop Activity tutaj".|
|<xref:System.Activities.Statements.If.Then%2A>|Fałsz|Działanie do wykonania, jeśli <xref:System.Activities.Statements.If.Condition%2A> ma **wartość true**. Aby dodać działanie, które jest wykonywane przez <xref:System.Activities.Statements.If.Then%2A> gałąź, upuść działanie z **przybornika** do pola **then** w projektancie działania w **przypadku, gdy** tekst wskazówki "upuść działanie tutaj".|

## <a name="see-also"></a>Zobacz też
 [Sequence](../workflow-designer/sequence-activity-designer.md) [Równoległy](../workflow-designer/parallel-activity-designer.md) [przepływ sterowania](../workflow-designer/control-flow-activity-designers.md) sekwencji