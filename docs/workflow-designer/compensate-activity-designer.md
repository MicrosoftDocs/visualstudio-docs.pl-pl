---
title: Projektant przepływu pracy — kompensowanie działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65203663214e6bc82a4a7b20af9caa25bfd98ee4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650652"
---
# <a name="compensate-activity-designer"></a>Compensate, projektant działań

Projektant działań **kompensacyjnych** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.Compensate>.

## <a name="the-compensate-activity"></a>Działanie kompensacja

Działanie <xref:System.Activities.Statements.Compensate> jawnie wywołuje <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> dla działania zawartego w <xref:System.Activities.Statements.CompensableActivity>. Jeśli działanie <xref:System.Activities.Statements.Compensate> nie jest używane w <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> lub <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> <xref:System.Activities.Statements.CompensableActivity>, należy określić właściwość <xref:System.Activities.Statements.Compensate.Target%2A>.

@No__t_0 określony przez <xref:System.Activities.Statements.Compensate.Target%2A> zapewnia metodę jawnego potwierdzenia lub zrekompensowania <xref:System.Activities.Statements.CompensableActivity> po pomyślnym zakończeniu <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity>.

### <a name="using-the-compensate-activity-designer"></a>Korzystanie z projektanta działań kompensacyjnych

Projektanta działań **kompensowania** aktywności można znaleźć w kategorii **transakcji** w **przyborniku**. Aby otworzyć **Przybornik**, wybierz kartę **Przybornik** po lewej stronie Projektant przepływu pracy. Alternatywnie wybierz pozycję **Przybornik** z menu **Widok** lub naciśnij **klawisze CTRL** +**Alt** +**X**.

Projektant działań **kompensacyjnych** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence>. Porzucenie projektanta działań powoduje utworzenie <xref:System.Activities.Statements.Compensate> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> kompensaty. Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań **kompensacyjnych** lub w polu **DisplayName** siatki właściwości.

### <a name="the-compensate-properties"></a>Właściwości kompensacji

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.CancellationScope> i opisano sposób ich używania w projektancie. Właściwość <xref:System.Activities.Activity.DisplayName%2A> można edytować w siatce właściwości lub na Projektant przepływu pracy powierzchni. Edytuj Właściwość <xref:System.Activities.Statements.Compensate.Target%2A> w siatce właściwości.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalną przyjazną nazwę działania <xref:System.Activities.Statements.Compensate>. Wartość domyślna to kompensacja.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|Oznacza|Określa <xref:System.Activities.InArgument%601>, który zawiera <xref:System.Activities.Statements.CompensationToken> dla tego działania <xref:System.Activities.Statements.Compensate>.|

## <a name="see-also"></a>Zobacz także

- [Transakcja](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate, projektant działań](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)