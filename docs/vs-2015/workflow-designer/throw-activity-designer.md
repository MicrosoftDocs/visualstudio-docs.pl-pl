---
title: Zgłoś projektanta działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1855daa5016241fb6eb04f05d7218e02083fc0a8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655164"
---
# <a name="throw-activity-designer"></a>Throw, projektant działań
Projektant działań **throw** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.Throw>.

## <a name="the-throw-activity"></a>Działanie throw
 Działanie <xref:System.Activities.Statements.Throw> zgłasza wyjątek.

### <a name="using-the-throw-activity-designer"></a>Korzystanie z projektanta działań throw
 Projektant działań **throw** można znaleźć w kategorii **Obsługa błędów** w **przyborniku**, do którego uzyskuje się dostęp, klikając kartę **Przybornik** po lewej stronie [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie, wybierając pozycję **pasek narzędzi** z **widoku.** lub CTRL + ALT + X.)

 Projektant działań **throw** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.Throw> z domyślną **nazwą wyświetlaną** throw. Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań **throw** lub w polu **DisplayName** siatki właściwości. Właściwość <xref:System.Activities.Statements.Throw.Exception%2A> musi być edytowana w siatce właściwości.

### <a name="the-throw-properties"></a>Właściwości throw
 W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.Throw> i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalną przyjazną nazwę działania <xref:System.Activities.Statements.Throw>. Wartość domyślna to throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|Oznacza|Wyjątek do zgłoszenia. Ten wyjątek musi pochodzić od <xref:System.Exception>. Aby określić wyjątek, wpisz wyrażenie Visual Basic w siatce właściwości.|

## <a name="see-also"></a>Zobacz też
 [](../workflow-designer/collection-activity-designers.md) [](../workflow-designer/rethrow-activity-designer.md) [TryCatch](../workflow-designer/trycatch-activity-designer.md) — [Zgłoś ponownie projektanta działań](../workflow-designer/throw-activity-designer.md)