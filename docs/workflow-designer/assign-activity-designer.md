---
title: Projektant przepływu pracy — Przypisz projektanta działań
description: Dowiedz się, w jaki sposób można użyć projektanta działań do tworzenia i konfigurowania działania przypisania oraz jak działanie Assign przypisuje wartość do zmiennej lub argumentu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d8601951cfaba3f246e8488ab23c9b6ccad0d01
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438194"
---
# <a name="assign-activity-designer"></a>Assign, projektant działań

Projektant działań **Assign** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Assign> działania.

## <a name="the-assign-activity"></a>Działanie Assign

<xref:System.Activities.Statements.Assign>Działanie przypisuje wartość do zmiennej lub argumentu.

### <a name="using-the-assign-activity-designer"></a>Korzystanie z projektanta akcji przypisania

Projektanta działań **przypisanych** można znaleźć w kategorii elementy **pierwotne** **przybornika** , do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** (można również wybrać **Przybornik** z menu **Widok** lub CTRL + ALT + X).

Projektanta działania **przypisanego** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracyą powierzchnię, w której zostaną umieszczone kiedykolwiek wykonane działania, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Porzucenie projektanta **przypisywania** działań powoduje utworzenie <xref:System.Activities.Statements.Assign> działania z domyślną wartością **DisplayName** elementu Assign. <xref:System.Activities.Activity.DisplayName%2A>Można edytować w nagłówku projektanta działania **przypisania** lub w polu **DisplayName** siatki właściwości.

### <a name="the-assign-properties"></a>Właściwości przypisania

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Assign> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na Projektant przepływu pracy powierzchni.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa <xref:System.Activities.Statements.Assign> działania. Wartość domyślna to Assign. Chociaż <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.Assign.To%2A>|Prawda|Zmienna lub argument, do którego <xref:System.Activities.Statements.Assign.Value%2A> jest przypisany. Wartość musi być prawidłowym identyfikatorem Visual Basic. Aby ustawić właściwość, wpisz wyrażenie Visual Basic w polu **do** w **projektancie działania lub** w siatce właściwości.|
|<xref:System.Activities.Statements.Assign.Value%2A>|Prawda|Wartość, która jest przypisana do zmiennej. Aby ustawić <xref:System.Activities.Statements.Assign.Value%2A> , wpisz wyrażenie Visual Basic w polu **wartość** w projektancie działania lub w **Assign** siatce właściwości.|

## <a name="see-also"></a>Zobacz też

- [Typy pierwotne](../workflow-designer/primitives-activity-designers.md)
- [Opóźnienie](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)