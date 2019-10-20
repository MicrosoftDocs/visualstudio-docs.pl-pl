---
title: Działanie CompensableActivity — Projektant działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2bc28c4586912d7c253c9629c2af0eefd30e47e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656993"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity, projektant działań
Projektant działań **działanie CompensableActivity** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.CompensableActivity>.

## <a name="the-compensableactivity-activity"></a>Działanie działanie CompensableActivity
 @No__t_0 definiuje jednostkę pracy, którą można potwierdzić lub skompensować po pomyślnym zakończeniu.

### <a name="using-the-compensableactivity-activity-designer"></a>Korzystanie z projektanta działań działanie CompensableActivity
 Projektanta działań **działanie CompensableActivity** można znaleźć w kategorii **transakcji** **przybornika**, do którego uzyskuje się dostęp, klikając kartę **Przybornik** po lewej stronie [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie, wybierając pozycję **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X.)

 Projektanta działań **działanie CompensableActivity** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.CompensableActivity> przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> działanie CompensableActivity. Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań **działanie CompensableActivity** lub w polu **DisplayName** siatki właściwości.

### <a name="the-compensableactivity-properties"></a>Właściwości działanie CompensableActivity
 W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.CompensableActivity> i opisano sposób ich używania w projektancie. Właściwość <xref:System.Activities.Activity.DisplayName%2A> i <xref:System.Activities.Activity%601.Result%2A> można edytować w siatce właściwości, ale inne właściwości muszą być edytowane na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalna przyjazna nazwa działania <xref:System.Activities.Statements.CompensableActivity>. Wartość domyślna to działanie CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Określa wartość zwracaną <xref:System.Activities.Statements.CompensableActivity>. Ta właściwość musi być edytowana w siatce właściwości.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Oznacza|Określa działanie, dla którego podano wynagrodzenie, anulowanie i logikę potwierdzeń. Aby dodać działanie <xref:System.Activities.Statements.CompensableActivity.Body%2A>, Usuń działanie z **przybornika** do pola **treść** w projektancie działań **działanie CompensableActivity** ze wskazówkami tekst "upuść aktywność tutaj".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Określa działanie, które jest wykonywane w przypadku anulowania. Aby dodać działanie, usuń jego projektanta z **przybornika** do pola **CancellationHandler** w projektancie działań **działanie CompensableActivity** z wskazówką text "upuść aktywność tutaj".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Określa działanie, które ma zostać wykonane przy kompensowaniu działania <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Tę procedurę obsługi można jawnie wywołać przy użyciu działania <xref:System.Activities.Statements.Compensate>.<br /><br /> Aby dodać działanie, usuń jego projektanta działań z **przybornika** do pola **CompensationHandler** w projektancie działań **działanie CompensableActivity** z podpowiedzią text "upuść aktywność tutaj".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Określa działanie, które ma zostać wykonane przy potwierdzeniu działania <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Tę procedurę obsługi można jawnie wywołać przy użyciu działania <xref:System.Activities.Statements.Confirm>.<br /><br /> Aby dodać działanie, usuń jego projektanta działań z **przybornika** do pola **ConfirmationHandler** w projektancie działań **działanie CompensableActivity** z podpowiedzią text "upuść aktywność tutaj".|

## <a name="see-also"></a>Zobacz też
 Element [TransactionScope](../workflow-designer/transactionscope-activity-designer.md) [potwierdzenia](../workflow-designer/confirm-activity-designer.md) [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md) [transakcji](../workflow-designer/transaction-activity-designers.md) [kompensaty](../workflow-designer/compensate-activity-designer.md)