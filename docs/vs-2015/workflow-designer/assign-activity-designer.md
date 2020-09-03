---
title: Przypisywanie projektanta działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40ebe465d5eeb12a956d285a8313b0acdbcfb8d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659192"
---
# <a name="assign-activity-designer"></a>Assign, projektant działań
Projektant działań **Assign** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Assign> działania.

## <a name="the-assign-activity"></a>Działanie Assign
 <xref:System.Activities.Statements.Assign>Działanie przypisuje wartość do zmiennej lub argumentu.

### <a name="using-the-assign-activity-designer"></a>Korzystanie z projektanta akcji przypisania
 Projektanta działań **przypisanych** można znaleźć w kategorii elementy **pierwotne** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** (można również wybrać **Przybornik** z menu **Widok** lub CTRL + ALT + X).

 Projektant działań **przypisanych** może być przeciągany z **przybornika** i upuszczany na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchnię, w której są zwykle umieszczane działania, takie jak wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.Assign> działania z domyślną wartością **DisplayName** elementu Assign. <xref:System.Activities.Activity.DisplayName%2A>Można edytować w nagłówku projektanta działania **przypisania** lub w polu **DisplayName** siatki właściwości.

### <a name="the-assign-properties"></a>Właściwości przypisania
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Assign> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa <xref:System.Activities.Statements.Assign> działania. Wartość domyślna to Assign. Chociaż <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.Assign.To%2A>|Prawda|Zmienna lub argument, do którego <xref:System.Activities.Statements.Assign.Value%2A> jest przypisany. Musi to być prawidłowy identyfikator Visual Basic. Aby ustawić właściwość, wpisz wyrażenie Visual Basic w polu **do** w **projektancie działania lub** w siatce właściwości.|
|<xref:System.Activities.Statements.Assign.Value%2A>|Prawda|Wartość, która jest przypisana do zmiennej. Aby ustawić <xref:System.Activities.Statements.Assign.Value%2A> , wpisz wyrażenie Visual Basic w polu **wartość** w projektancie działania lub w **Assign** siatce właściwości.|

## <a name="see-also"></a>Zobacz też
 [Primitives](../workflow-designer/primitives-activity-designers.md) [Opóźnienie](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) metodyą [WriteLine](../workflow-designer/writeline-activity-designer.md)