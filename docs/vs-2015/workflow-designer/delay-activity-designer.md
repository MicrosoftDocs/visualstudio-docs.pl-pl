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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656798"
---
# <a name="delay-activity-designer"></a>Delay, projektant działań
Projektant działań **opóźnionych** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.Delay>.

## <a name="the-delay-activity"></a>Działanie Opóźnij
 Działanie <xref:System.Activities.Statements.Delay> opóźnia wykonywanie przepływu pracy przez określoną ilość czasu.

### <a name="using-the-delay-activity-designer"></a>Korzystanie z projektanta działań opóźnionych
 Projektanta aktywności **opóźnienia** można znaleźć w kategorii elementy **pierwotne** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** w [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz pozycję **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X.)

 Projektanta aktywności **opóźnienia** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.Delay> z domyślnym <xref:System.Activities.Activity.DisplayName%2A> opóźnieniem. @No__t_0 można edytować w nagłówku projektanta działań **opóźnionych** lub w polu **DisplayName** siatki właściwości.

### <a name="the-delay-properties"></a>Właściwości opóźnienia
 W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.Delay> i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości i z nich niektóre można edytować na [!INCLUDE[wfd2](../includes/wfd2-md.md)]designer powierzchni.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa działania <xref:System.Activities.Statements.Delay>. Wartość domyślna to opóźnienie. Mimo że wartość <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Oznacza|Czas opóźnienia przepływu pracy. Ta właściwość jest ustawiana w siatce właściwości. Wpisz literał <xref:System.TimeSpan> w formacie 00:00:00 lub Visual Basic wyrażenie, aby określić ilość czasu.|

## <a name="see-also"></a>Zobacz też
 Elementy [pierwotne](../workflow-designer/primitives-activity-designers.md) [przypisują](../workflow-designer/assign-activity-designer.md) [opóźnienie WriteLine projektanta działań](../workflow-designer/delay-activity-designer.md) [](../workflow-designer/invokemethod-activity-designer.md) [](../workflow-designer/writeline-activity-designer.md)