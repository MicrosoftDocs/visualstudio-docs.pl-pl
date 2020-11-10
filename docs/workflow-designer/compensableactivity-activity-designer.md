---
title: Projektant przepływu pracy — Projektant działań działanie CompensableActivity
description: Dowiedz się, jak za pomocą projektanta działań działanie CompensableActivity utworzyć i skonfigurować działanie działanie CompensableActivity.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e170bd47af7c84eb9ddb26a4946422c418365d2
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434340"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity, projektant działań

Projektant działań **działanie CompensableActivity** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.CompensableActivity> działania.

## <a name="the-compensableactivity-activity"></a>Działanie działanie CompensableActivity
 <xref:System.Activities.Statements.CompensableActivity>Definiuje jednostkę pracy, którą można potwierdzić lub skompensować po pomyślnym zakończeniu.

### <a name="using-the-compensableactivity-activity-designer"></a>Korzystanie z projektanta działań działanie CompensableActivity
 Projektanta działań **działanie CompensableActivity** można znaleźć w kategorii **transakcji** **przybornika**. Aby otworzyć **Przybornik** , wybierz kartę **Przybornik** po lewej stronie Projektant przepływu pracy. Alternatywnie możesz wybrać **Przybornik** z menu **Widok** lub nacisnąć **klawisze CTRL** + **Alt** + **X**.

 Projektanta działań **działanie CompensableActivity** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię. Można upuścić projektanta działań wewnątrz <xref:System.Activities.Statements.Sequence> . Porzucenie projektanta działań powoduje utworzenie <xref:System.Activities.Statements.CompensableActivity> działania z wartością domyślną <xref:System.Activities.Activity.DisplayName%2A> działanie CompensableActivity. Edytuj <xref:System.Activities.Activity.DisplayName%2A> wartość w nagłówku projektanta działań **działanie CompensableActivity** . Można go również edytować w polu **DisplayName** siatki właściwości.

### <a name="the-compensableactivity-properties"></a>Właściwości działanie CompensableActivity
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.CompensableActivity> właściwości i opisano sposób ich użycia w projektancie. <xref:System.Activities.Activity.DisplayName%2A>Właściwość i <xref:System.Activities.Activity%601.Result%2A> można edytować w siatce właściwości, ale inne właściwości muszą być edytowane na powierzchni Projektant przepływu pracy.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Opcjonalna przyjazna nazwa <xref:System.Activities.Statements.CompensableActivity> działania. Wartość domyślna to działanie CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|Fałsz|Określa wartość zwracaną przez <xref:System.Activities.Statements.CompensableActivity> . Ta właściwość musi być edytowana w siatce właściwości.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Prawda|Określa działanie, dla którego podano wynagrodzenie, anulowanie i logikę potwierdzeń. Aby dodać <xref:System.Activities.Statements.CompensableActivity.Body%2A> działanie, upuść działanie z **przybornika** do pola **treść** w projektancie działań **działanie CompensableActivity** . Dodaj tekst wskazówki "upuść działanie tutaj".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|Fałsz|Określa działanie, które jest wykonywane po anulowaniu. Aby dodać działanie, usuń jego projektanta z **przybornika** do pola **CancellationHandler** w projektancie działań **działanie CompensableActivity** . Dodaj tekst wskazówki "upuść działanie tutaj".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|Fałsz|Określa działanie, które ma zostać wykonane przy kompensowaniu dla <xref:System.Activities.Statements.CompensableActivity.Body%2A> działania. Tę procedurę obsługi można jawnie wywołać za pomocą <xref:System.Activities.Statements.Compensate> działania.<br /><br /> Aby dodać działanie, usuń jego projektanta działań z **przybornika** do pola **CompensationHandler** w projektancie działań **działanie CompensableActivity** . Dodaj tekst wskazówki "upuść działanie tutaj".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|Fałsz|Określa działanie, które ma zostać wykonane podczas potwierdzania <xref:System.Activities.Statements.CompensableActivity.Body%2A> działania. Tę procedurę obsługi można jawnie wywołać za pomocą <xref:System.Activities.Statements.Confirm> działania.<br /><br /> Aby dodać działanie, usuń jego projektanta działań z **przybornika** do pola **ConfirmationHandler** w projektancie działań **działanie CompensableActivity** . Dodaj tekst wskazówki "upuść działanie tutaj".|

## <a name="see-also"></a>Zobacz też

- [Transakcja](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
