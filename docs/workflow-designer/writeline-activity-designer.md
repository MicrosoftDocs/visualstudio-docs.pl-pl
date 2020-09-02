---
title: Projektant przepływu pracy — Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e3b4da69a2d9154f36e42d3b20657e204767872
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593027"
---
# <a name="writeline-activity-designer"></a>WriteLine, projektant działań

Projektant działań **WriteLine** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.WriteLine> działania.

## <a name="the-writeline-activity"></a>Działanie WriteLine

<xref:System.Activities.Statements.WriteLine>Działanie zapisuje tekst do określonego <xref:System.IO.TextWriter> obiektu. Jeśli nie <xref:System.IO.TextWriter> jest określony, program <xref:System.Activities.Statements.WriteLine> zapisuje tekst w konsoli programu.

### <a name="using-the-writeline-activity-designer"></a>Korzystanie z projektanta działań WriteLine

Dostęp do projektanta działań **WriteLine** w kategorii elementy **pierwotne** w **przyborniku**. Projektant działań **WriteLine** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.WriteLine> działania z domyślną wartością <xref:System.Activities.Activity.DisplayName%2A> WriteLine. <xref:System.Activities.Activity.DisplayName%2A>Można edytować w nagłówku projektanta działania **WriteLine** lub w polu **DisplayName** siatki właściwości.

### <a name="the-writeline-properties"></a>Właściwości WriteLine

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.WriteLine> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na Projektant przepływu pracy powierzchni.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa <xref:System.Activities.Statements.WriteLine> działania. Wartość domyślna to WriteLine. Chociaż <xref:System.Activities.Activity.DisplayName%2A> nie jest to ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|Fałsz|Tekst do zapisania. Aby ustawić właściwość, wpisz wyrażenie Visual Basic w polu **tekstowym** w projektancie aktywności **WriteLine** lub w siatce właściwości.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|Fałsz|<xref:System.IO.TextWriter>Do którego <xref:System.Activities.Statements.WriteLine> zapisu <xref:System.Activities.Statements.WriteLine.Text%2A> . Wartością domyślną jest konsola programu.|

## <a name="see-also"></a>Zobacz też

- [Typy pierwotne](../workflow-designer/primitives-activity-designers.md)
- [Ponownie](../workflow-designer/assign-activity-designer.md)
- [Opóźnienie](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
