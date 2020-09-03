---
title: Projektant działań StateMachine | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
caps.latest.revision: 5
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fc9d34e06ca443b39a1a57aa88fee1155f47a8c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660116"
---
# <a name="statemachine-activity-designer"></a>StateMachine, projektant działań
<xref:System.Activities.Statements.StateMachine>Działanie zawiera kolekcję przepływów pracy stanów i modeli przy użyciu modelu znanego komputera o stanie.

## <a name="using-the-statemachine-activity-designer"></a>Korzystanie z projektanta działań StateMachine
 Aby dodać <xref:System.Activities.Statements.StateMachine> działanie, przeciągnij projektanta działań **StateMachine** z sekcji **stan automatu** w **przyborniku** i upuść go na [!INCLUDE[wfd1](../includes/wfd1-md.md)] powierzchnię. Aby dodać stan podrzędny do tego <xref:System.Activities.Statements.StateMachine> działania, przeciągnij <xref:System.Activities.Statements.State> lub <xref:System.Activities.Core.Presentation.FinalState> z **przybornika** i upuść go na obiekt **StateMachine**.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Właściwości działania StateMachine w Projektant przepływu pracy
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.StateMachine> właściwości, które można ustawić za pomocą projektanta przepływów pracy, i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na powierzchni projektanta.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa przyjazną nazwę <xref:System.Activities.Statements.StateMachine> projektanta działań w nagłówku. Wartość domyślna to **StateMachine**. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku projektanta działań. Ta wartość <xref:System.Activities.Activity.DisplayName%2A> jest używana w nawigacyjnym nawigacji, który jest wyświetlany w górnej części projektanta przepływu pracy.<br /><br /> Chociaż <xref:System.Activities.Activity.DisplayName%2A> nie jest to ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|

## <a name="see-also"></a>Zobacz też
 [Flowchart](../workflow-designer/flowchart-activity-designer.md) [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md) Flowchart