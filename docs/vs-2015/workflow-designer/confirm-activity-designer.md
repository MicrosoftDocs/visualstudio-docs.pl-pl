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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656965"
---
# <a name="confirm-activity-designer"></a>Confirm, projektant działań
Aby utworzyć i skonfigurować działanie <xref:System.Activities.Statements.Confirm>, można użyć programu **confirming** Designer.

## <a name="the-confirm-activity"></a>Potwierdzenie działania
 Działanie <xref:System.Activities.Statements.Confirm> jawnie wywołuje <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> dla działania zawartego w <xref:System.Activities.Statements.CompensableActivity>. Jeśli działanie <xref:System.Activities.Statements.Confirm> nie jest używane w <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> lub <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> <xref:System.Activities.Statements.CompensableActivity>, należy określić właściwość <xref:System.Activities.Statements.Confirm.Target%2A>.

 @No__t_0 określony przez <xref:System.Activities.Statements.Compensate.Target%2A> zapewnia metodę jawnego potwierdzenia lub zrekompensowania <xref:System.Activities.Statements.CompensableActivity> po pomyślnym zakończeniu <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity>.

### <a name="using-the-confirm-activity-designer"></a>Korzystanie z programu Confirme Designer
 Program **confirming** Designer można znaleźć w kategorii **transakcji** **przybornika**, do którego uzyskuje się dostęp, klikając kartę **Przybornik** po lewej stronie [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie, wybierając pozycję **pasek narzędzi** z **widoku.** menu lub CTRL + ALT + X.)

 Można przeciągnąć **projektanta działań z** **przybornika** i porzucony na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład w <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.Confirm> przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> potwierdzenia. Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku programu **Confirme** Activity Designer lub w polu **DisplayName** siatki właściwości.

### <a name="the-confirm-properties"></a>Potwierdzenie właściwości
 W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.Confirm> i opisano sposób ich używania w projektancie. Właściwość <xref:System.Activities.Activity.DisplayName%2A> można edytować w siatce właściwości lub na powierzchni [!INCLUDE[wfd2](../includes/wfd2-md.md)], ale Właściwość <xref:System.Activities.Statements.Confirm.Target%2A> musi być edytowana w siatce właściwości.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalną przyjazną nazwę działania <xref:System.Activities.Statements.CancellationScope>. Wartość domyślna to Confirm (Potwierdź).|
|<xref:System.Activities.Statements.Confirm.Target%2A>|Oznacza|Określa <xref:System.Activities.InArgument%601>, który zawiera <xref:System.Activities.Statements.CompensationToken> dla tego działania <xref:System.Activities.Statements.Confirm>.|

## <a name="see-also"></a>Zobacz też
 [](../workflow-designer/transaction-activity-designers.md) [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md) [transakcji działanie CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [kompensowanie](../workflow-designer/compensate-activity-designer.md) elementu [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)