---
title: Opóźnij projektanta działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a47279bc68503ba645fea3ef23a04ce9d5ef4c41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656798"
---
# <a name="delay-activity-designer"></a>Delay, projektant działań
Projektant działań **opóźnionych** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Delay> działania.

## <a name="the-delay-activity"></a>Działanie Opóźnij
 <xref:System.Activities.Statements.Delay>Działanie opóźnia wykonywanie przepływu pracy przez określoną ilość czasu.

### <a name="using-the-delay-activity-designer"></a>Korzystanie z projektanta działań opóźnionych
 Projektanta aktywności **opóźnienia** można znaleźć w kategorii elementy **pierwotne** **przybornika**, do którego uzyskuje się dostęp, klikając kartę **przybornika** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X).

 Projektanta aktywności **opóźnienia** można przeciągać z **przybornika** i znajdować się na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.Delay> działania z domyślnym <xref:System.Activities.Activity.DisplayName%2A> opóźnieniem. <xref:System.Activities.Activity.DisplayName%2A>Można edytować w nagłówku projektanta działań **opóźnionych** lub w polu **DisplayName** siatki właściwości.

### <a name="the-delay-properties"></a>Właściwości opóźnienia
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Delay> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości i z nich niektóre można edytować na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni projektanta.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa <xref:System.Activities.Statements.Delay> działania. Wartość domyślna to opóźnienie. Chociaż <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Prawda|Czas opóźnienia przepływu pracy. Ta właściwość jest ustawiana w siatce właściwości. Wpisz w postaci literału w <xref:System.TimeSpan> formacie 00:00:00 lub Visual Basic wyrażenie, aby określić ilość czasu.|

## <a name="see-also"></a>Zobacz też
 Elementy [pierwotne](../workflow-designer/primitives-activity-designers.md) [przypisują](../workflow-designer/assign-activity-designer.md) [opóźnienie WriteLine projektanta działań](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)