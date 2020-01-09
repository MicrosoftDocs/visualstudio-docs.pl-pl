---
title: Projektant przepływu pracy — Projektant działań działanie CompensableActivity
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
ms.openlocfilehash: 7ec70c22ae195dc6dd58aa2cfa893cee35fe6ca8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597103"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity, projektant działań

Projektant działań **działanie CompensableActivity** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.CompensableActivity>.

## <a name="the-compensableactivity-activity"></a>Działanie działanie CompensableActivity
 <xref:System.Activities.Statements.CompensableActivity> definiuje jednostkę pracy, którą można potwierdzić lub skompensować po pomyślnym zakończeniu.

### <a name="using-the-compensableactivity-activity-designer"></a>Korzystanie z projektanta działań działanie CompensableActivity
 Projektanta działań **działanie CompensableActivity** można znaleźć w kategorii **transakcji** **przybornika**. Aby otworzyć **Przybornik**, wybierz kartę **Przybornik** po lewej stronie Projektant przepływu pracy. Alternatywnie wybierz pozycję **Przybornik** z menu **Widok** lub naciśnij **klawisze CTRL**+**Alt**+**X**.

 Projektanta działań **działanie CompensableActivity** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię. Można upuścić projektanta działań wewnątrz <xref:System.Activities.Statements.Sequence>. Porzucenie projektanta działań powoduje utworzenie działania <xref:System.Activities.Statements.CompensableActivity> przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> działanie CompensableActivity. Edytuj wartość <xref:System.Activities.Activity.DisplayName%2A> w nagłówku projektanta działań **działanie CompensableActivity** . Można go również edytować w polu **DisplayName** siatki właściwości.

### <a name="the-compensableactivity-properties"></a>Właściwości działanie CompensableActivity
 W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.CompensableActivity> i opisano sposób ich używania w projektancie. Właściwość <xref:System.Activities.Activity.DisplayName%2A> i <xref:System.Activities.Activity%601.Result%2A> można edytować w siatce właściwości, ale inne właściwości muszą być edytowane na Projektant przepływu pracy powierzchni.

|Nazwa właściwości|Wymagane|Pomiar|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Opcjonalna przyjazna nazwa działania <xref:System.Activities.Statements.CompensableActivity>. Wartość domyślna to działanie CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|Fałsz|Określa wartość zwracaną <xref:System.Activities.Statements.CompensableActivity>. Ta właściwość musi być edytowana w siatce właściwości.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Prawda|Określa działanie, dla którego podano wynagrodzenie, anulowanie i logikę potwierdzeń. Aby dodać działanie <xref:System.Activities.Statements.CompensableActivity.Body%2A>, Usuń działanie z **przybornika** do pola **treść** w projektancie działań **działanie CompensableActivity** . Dodaj tekst wskazówki "upuść działanie tutaj".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|Fałsz|Określa działanie, które jest wykonywane po anulowaniu. Aby dodać działanie, usuń jego projektanta z **przybornika** do pola **CancellationHandler** w projektancie działań **działanie CompensableActivity** . Dodaj tekst wskazówki "upuść działanie tutaj".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|Fałsz|Określa działanie, które ma zostać wykonane przy kompensowaniu działania <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Tę procedurę obsługi można jawnie wywołać przy użyciu działania <xref:System.Activities.Statements.Compensate>.<br /><br /> Aby dodać działanie, usuń jego projektanta działań z **przybornika** do pola **CompensationHandler** w projektancie działań **działanie CompensableActivity** . Dodaj tekst wskazówki "upuść działanie tutaj".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|Fałsz|Określa działanie, które ma zostać wykonane przy potwierdzeniu działania <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Tę procedurę obsługi można jawnie wywołać przy użyciu działania <xref:System.Activities.Statements.Confirm>.<br /><br /> Aby dodać działanie, usuń jego projektanta działań z **przybornika** do pola **ConfirmationHandler** w projektancie działań **działanie CompensableActivity** . Dodaj tekst wskazówki "upuść działanie tutaj".|

## <a name="see-also"></a>Zobacz także

- [Transakcja](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
