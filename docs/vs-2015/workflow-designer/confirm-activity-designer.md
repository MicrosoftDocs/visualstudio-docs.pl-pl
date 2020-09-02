---
title: Potwierdź projektanta działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b3835c6cb537e7ac74862ac4a6794dd7b0bd5003
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656965"
---
# <a name="confirm-activity-designer"></a>Confirm, projektant działań
Aby utworzyć i skonfigurować działanie, należy użyć programu **confirming** Designer <xref:System.Activities.Statements.Confirm> .

## <a name="the-confirm-activity"></a>Potwierdzenie działania
 <xref:System.Activities.Statements.Confirm>Działanie jawnie wywołuje <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> działanie dla działania zawartego w <xref:System.Activities.Statements.CompensableActivity> . Jeśli <xref:System.Activities.Statements.Confirm> działanie nie jest używane w <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> , <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> , lub, należy <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> <xref:System.Activities.Statements.CompensableActivity> określić <xref:System.Activities.Statements.Confirm.Target%2A> Właściwość.

 <xref:System.Activities.Statements.CompensationToken>Określony przez <xref:System.Activities.Statements.Compensate.Target%2A> zawiera metodę, aby jawnie potwierdzić lub skompensować <xref:System.Activities.Statements.CompensableActivity> po <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> pomyślnym zakończeniu.

### <a name="using-the-confirm-activity-designer"></a>Korzystanie z programu Confirme Designer
 Można znaleźć **projektanta działań w** kategorii **transakcji** **przybornika**, do którego uzyskuje się dostęp, klikając kartę **Przybornik** po lewej stronie okna [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X).

 Można przeciągać **projektanta działań z** **przybornika** i znajdować się na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, wszędzie tam gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.Confirm> działania z domyślnym <xref:System.Activities.Activity.DisplayName%2A> potwierdzeniem. <xref:System.Activities.Activity.DisplayName%2A>Wartość można edytować w nagłówku programu **Confirmed** Activity Designer lub w polu **DisplayName** siatki właściwości.

### <a name="the-confirm-properties"></a>Potwierdzenie właściwości
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Confirm> właściwości i opisano sposób ich użycia w projektancie. <xref:System.Activities.Activity.DisplayName%2A>Właściwość można edytować w siatce właściwości lub na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, ale <xref:System.Activities.Statements.Confirm.Target%2A> Właściwość musi być edytowana w siatce właściwości.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa opcjonalną przyjazną nazwę <xref:System.Activities.Statements.CancellationScope> działania. Wartość domyślna to Confirm (Potwierdź).|
|<xref:System.Activities.Statements.Confirm.Target%2A>|Prawda|Określa <xref:System.Activities.InArgument%601> , który zawiera <xref:System.Activities.Statements.CompensationToken> dla tego <xref:System.Activities.Statements.Confirm> działania.|

## <a name="see-also"></a>Zobacz też
 [Transaction](../workflow-designer/transaction-activity-designers.md) [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md) [transakcji działanie CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [kompensowanie](../workflow-designer/compensate-activity-designer.md) elementu [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)