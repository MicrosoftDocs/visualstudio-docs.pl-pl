---
title: Kompensacja działań — Projektant | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 706cd446e931d6a3a065a3e8abfb58b5a90e9152
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656975"
---
# <a name="compensate-activity-designer"></a>Compensate, projektant działań
Projektant działań **kompensacyjnych** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Compensate> działania.

## <a name="the-compensate-activity"></a>Działanie kompensacja
 <xref:System.Activities.Statements.Compensate>Działanie jawnie wywołuje <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> działanie dla działania zawartego w <xref:System.Activities.Statements.CompensableActivity> . Jeśli <xref:System.Activities.Statements.Compensate> działanie nie jest używane w <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> , <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> , lub, należy <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> <xref:System.Activities.Statements.CompensableActivity> określić <xref:System.Activities.Statements.Compensate.Target%2A> Właściwość.

 <xref:System.Activities.Statements.CompensationToken>Określony przez <xref:System.Activities.Statements.Compensate.Target%2A> zawiera metodę, aby jawnie potwierdzić lub skompensować <xref:System.Activities.Statements.CompensableActivity> po <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> pomyślnym zakończeniu.

### <a name="using-the-compensate-activity-designer"></a>Korzystanie z projektanta działań kompensacyjnych
 Projektant działań **kompensacyjnych** można znaleźć w kategorii **transakcji** **przybornika**, do którego uzyskuje się dostęp, klikając kartę **Przybornik** po lewej stronie okna [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X).

 Można przeciągać **projektanta działań z** **przybornika** i znajdować się na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, wszędzie tam gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.Compensate> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> kompensacją. <xref:System.Activities.Activity.DisplayName%2A>Wartość można edytować w nagłówku projektanta działań lub w **Compensate** polu **DisplayName** siatki właściwości.

### <a name="the-compensate-properties"></a>Właściwości kompensacji
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.CancellationScope> właściwości i opisano sposób ich użycia w projektancie. <xref:System.Activities.Activity.DisplayName%2A>Właściwość można edytować w siatce właściwości lub na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, ale <xref:System.Activities.Statements.Compensate.Target%2A> Właściwość musi być edytowana w siatce właściwości.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa opcjonalną przyjazną nazwę <xref:System.Activities.Statements.Compensate> działania. Wartość domyślna to kompensacja.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|Prawda|Określa <xref:System.Activities.InArgument%601> , który zawiera <xref:System.Activities.Statements.CompensationToken> dla tego <xref:System.Activities.Statements.Compensate> działania.|

## <a name="see-also"></a>Zobacz też
 [Transaction](../workflow-designer/transaction-activity-designers.md) [Działanie CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [transakcji Wynagradzaj projektanta działań](../workflow-designer/compensate-activity-designer.md) , aby [potwierdzić](../workflow-designer/confirm-activity-designer.md) element [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)