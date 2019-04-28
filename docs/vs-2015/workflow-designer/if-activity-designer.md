---
title: Jeśli Projektant działań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3ab8c9a7f49302b2308f97855c022d8e8d5126e0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62956888"
---
# <a name="if-activity-designer"></a>If, projektant działań
<xref:System.Activities.Statements.If> Działanie sprawdza warunek i wykonuje działanie w zależności od wyników tej oceny. To działanie jest najbardziej użyteczna, korzystając z procedur, modelowanie stylu programowania. <xref:System.Activities.Statements.If> Działania mogą być zagnieżdżone wewnątrz <xref:System.Activities.Statements.Sequence> działania lub <xref:System.Activities.Statements.Parallel> działania, na przykład. Jeśli używasz <xref:System.Activities.Statements.Flowchart> działanie, należy rozważyć użycie <xref:System.Activities.Statements.FlowDecision> działania zamiast tego.  
  
## <a name="if-properties-in-the-workflow-designer"></a>Jeśli właściwości w Projektancie przepływu pracy  
 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.If> właściwości działań i informacje dotyczące używania ich w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.If.Condition%2A>|Prawda|Warunek, który określa, które działania podrzędnego do wykonania. Aby ustawić <xref:System.Activities.Statements.If.Condition%2A>, wpisz [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] wyrażenia w **warunek** polu na **Jeśli** działanie projektanta lub w siatce właściwości.|  
|<xref:System.Activities.Statements.If.Else%2A>|False|Działanie do wykonania, jeśli <xref:System.Activities.Statements.If.Condition%2A> jest **false**. Można dodać działania wykonywane przez <xref:System.Activities.Statements.If.Else%2A> gałęzi, Porzuć działania z **przybornika** do **Else** polu na **Jeśli** projektanta działań z tekst wskazówki " Upuść działanie tutaj".|  
|<xref:System.Activities.Statements.If.Then%2A>|False|Działanie do wykonania, jeśli <xref:System.Activities.Statements.If.Condition%2A> jest **true**. Można dodać działania wykonywane przez <xref:System.Activities.Statements.If.Then%2A> gałęzi, Porzuć działania z **przybornika** do **następnie** polu na **Jeśli** projektanta działań z tekst wskazówki " Upuść działanie tutaj".|  
  
## <a name="see-also"></a>Zobacz też  
 [Sekwencja](../workflow-designer/sequence-activity-designer.md)   
 [równoległe](../workflow-designer/parallel-activity-designer.md)   
 [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)