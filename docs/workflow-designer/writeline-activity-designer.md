---
title: Projektant przepływu pracy — Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 475755fed96f8341c45b8260b414658967b3284c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649754"
---
# <a name="writeline-activity-designer"></a>WriteLine, projektant działań

Projektant działań **WriteLine** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.WriteLine>.

## <a name="the-writeline-activity"></a>Działanie WriteLine

Działanie <xref:System.Activities.Statements.WriteLine> zapisuje tekst do określonego <xref:System.IO.TextWriter> obiektu. Jeśli nie <xref:System.IO.TextWriter> jest określony, <xref:System.Activities.Statements.WriteLine> zapisuje tekst w konsoli programu.

### <a name="using-the-writeline-activity-designer"></a>Korzystanie z projektanta działań WriteLine

Dostęp do projektanta działań **WriteLine** w kategorii elementy **pierwotne** w **przyborniku**. Projektant działań **WriteLine** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.WriteLine> z domyślną <xref:System.Activities.Activity.DisplayName%2A> WriteLine. @No__t_0 można edytować w nagłówku projektanta działań **WriteLine** lub w polu **DisplayName** siatki właściwości.

### <a name="the-writeline-properties"></a>Właściwości WriteLine

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.WriteLine> i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na Projektant przepływu pracy powierzchni.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa działania <xref:System.Activities.Statements.WriteLine>. Wartość domyślna to WriteLine. Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Tekst do zapisania. Aby ustawić właściwość, wpisz wyrażenie Visual Basic w polu **tekstowym** w projektancie aktywności **WriteLine** lub w siatce właściwości.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|@No__t_0, do której <xref:System.Activities.Statements.WriteLine> zapisuje <xref:System.Activities.Statements.WriteLine.Text%2A>. Wartością domyślną jest konsola programu.|

## <a name="see-also"></a>Zobacz także

- [Typy pierwotne](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)