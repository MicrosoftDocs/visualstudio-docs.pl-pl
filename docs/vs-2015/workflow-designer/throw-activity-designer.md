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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655164"
---
# <a name="throw-activity-designer"></a>Throw, projektant działań
Projektant działań **throw** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Throw> działania.

## <a name="the-throw-activity"></a>Działanie throw
 <xref:System.Activities.Statements.Throw>Działanie zgłasza wyjątek.

### <a name="using-the-throw-activity-designer"></a>Korzystanie z projektanta działań throw
 Projektant działań **throw** można znaleźć w kategorii **Obsługa błędów** w **przyborniku**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** w lewej części okna [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X).

 Można przeciągać **projektanta działań z** **przybornika** i znajdować się na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, wszędzie tam gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.Throw> działania z domyślną wartością **DisplayName** elementu throw. <xref:System.Activities.Activity.DisplayName%2A>Wartość można edytować w nagłówku projektanta działań **throw** lub w polu **DisplayName** siatki właściwości. <xref:System.Activities.Statements.Throw.Exception%2A>Właściwość musi być edytowana w siatce właściwości.

### <a name="the-throw-properties"></a>Właściwości throw
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Throw> właściwości i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa opcjonalną przyjazną nazwę <xref:System.Activities.Statements.Throw> działania. Wartość domyślna to throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|Prawda|Wyjątek do zgłoszenia. Ten wyjątek musi pochodzić od <xref:System.Exception> . Aby określić wyjątek, wpisz wyrażenie Visual Basic w siatce właściwości.|

## <a name="see-also"></a>Zobacz też
 [Collection](../workflow-designer/collection-activity-designers.md) [Rethrow](../workflow-designer/rethrow-activity-designer.md) [TryCatch](../workflow-designer/trycatch-activity-designer.md) — [Zgłoś ponownie projektanta działań](../workflow-designer/throw-activity-designer.md)