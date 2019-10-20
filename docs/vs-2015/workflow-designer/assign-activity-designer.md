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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659192"
---
# <a name="assign-activity-designer"></a>Assign, projektant działań
Projektant działania **Assign** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.Assign>.

## <a name="the-assign-activity"></a>Działanie Assign
 Działanie <xref:System.Activities.Statements.Assign> przypisuje wartość do zmiennej lub argumentu.

### <a name="using-the-assign-activity-designer"></a>Korzystanie z projektanta akcji przypisania
 Projektanta działań **przypisanych** można znaleźć w kategorii elementy **pierwotne** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** (można również wybrać **Przybornik** z menu **Widok** lub CTRL + ALT + X).

 Projektant działań **przypisanych** może być przeciągany z **przybornika** i upuszczany na [!INCLUDE[wfd2](../includes/wfd2-md.md)]ą powierzchnię, w której kiedykolwiek są zwykle umieszczane działania, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.Assign> z domyślną wartością **DisplayName** elementu Assign. @No__t_0 można edytować w nagłówku projektanta działań **przypisanych** lub w polu **DisplayName** siatki właściwości.

### <a name="the-assign-properties"></a>Właściwości przypisania
 W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.Assign> i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa działania <xref:System.Activities.Statements.Assign>. Wartość domyślna to Assign. Mimo że wartość <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.Assign.To%2A>|Oznacza|Zmienna lub argument, do którego przypisano <xref:System.Activities.Statements.Assign.Value%2A>. Musi to być prawidłowy identyfikator Visual Basic. Aby ustawić właściwość, wpisz wyrażenie Visual Basic w polu **do** w **projektancie działania lub** w siatce właściwości.|
|<xref:System.Activities.Statements.Assign.Value%2A>|Oznacza|Wartość, która jest przypisana do zmiennej. Aby ustawić <xref:System.Activities.Statements.Assign.Value%2A>, wpisz wyrażenie Visual Basic w polu **wartość** w **projektancie działania lub** w siatce właściwości.|

## <a name="see-also"></a>Zobacz też
 [](../workflow-designer/primitives-activity-designers.md) [Opóźnienie](../workflow-designer/delay-activity-designer.md) [](../workflow-designer/invokemethod-activity-designer.md) metodyą [WriteLine](../workflow-designer/writeline-activity-designer.md)