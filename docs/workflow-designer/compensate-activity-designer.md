---
title: Projektant przepływu pracy — kompensowanie działań
description: Dowiedz się więcej na temat projektanta działań kompensacyjnych i sposobu użycia projektanta działań kompensowania do tworzenia i konfigurowania działań kompensacyjnych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 36ab20854adb952d098f71904cdd3cb092e27ac9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955687"
---
# <a name="compensate-activity-designer"></a>Compensate, projektant działań

Projektant działań **kompensacyjnych** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Compensate> działania.

## <a name="the-compensate-activity"></a>Działanie kompensacja

<xref:System.Activities.Statements.Compensate>Działanie jawnie wywołuje <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> działanie dla działania zawartego w <xref:System.Activities.Statements.CompensableActivity> . Jeśli <xref:System.Activities.Statements.Compensate> działanie nie jest używane w <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> , <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> , lub, należy <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> <xref:System.Activities.Statements.CompensableActivity> określić <xref:System.Activities.Statements.Compensate.Target%2A> Właściwość.

<xref:System.Activities.Statements.CompensationToken>Określony przez <xref:System.Activities.Statements.Compensate.Target%2A> zawiera metodę, aby jawnie potwierdzić lub skompensować <xref:System.Activities.Statements.CompensableActivity> po <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> pomyślnym zakończeniu.

### <a name="using-the-compensate-activity-designer"></a>Korzystanie z projektanta działań kompensacyjnych

Projektanta działań **kompensowania** aktywności można znaleźć w kategorii **transakcji** w **przyborniku**. Aby otworzyć **Przybornik**, wybierz kartę **Przybornik** po lewej stronie Projektant przepływu pracy. Alternatywnie możesz wybrać **Przybornik** z menu **Widok** lub nacisnąć **klawisze CTRL** + **Alt** + **X**.

Projektant działań **kompensacyjnych** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Porzucenie projektanta działań powoduje utworzenie <xref:System.Activities.Statements.Compensate> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> kompensacją. <xref:System.Activities.Activity.DisplayName%2A>Wartość można edytować w nagłówku projektanta działań lub w  polu **DisplayName** siatki właściwości.

### <a name="the-compensate-properties"></a>Właściwości kompensacji

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.CancellationScope> właściwości i opisano sposób ich użycia w projektancie. <xref:System.Activities.Activity.DisplayName%2A>Właściwość można edytować w siatce właściwości lub na Projektant przepływu pracy powierzchni. Edytuj <xref:System.Activities.Statements.Compensate.Target%2A> Właściwość w siatce właściwości.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa opcjonalną przyjazną nazwę <xref:System.Activities.Statements.Compensate> działania. Wartość domyślna to kompensacja.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|Prawda|Określa <xref:System.Activities.InArgument%601> , który zawiera <xref:System.Activities.Statements.CompensationToken> dla tego <xref:System.Activities.Statements.Compensate> działania.|

## <a name="see-also"></a>Zobacz też

- [Transakcja](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate, projektant działań](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)