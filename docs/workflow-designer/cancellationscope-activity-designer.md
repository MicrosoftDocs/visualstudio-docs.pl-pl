---
title: Projektant przepływu pracy — Projektant działań CancellationScope
description: Dowiedz się, jak za pomocą projektanta działań CancellationScope utworzyć i skonfigurować działanie CancellationScope.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 746ed70d0a1a8ae4de2207ea1fdf15280bd44de9
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434444"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope, projektant działań

Projektant działań **CancellationScope** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.CancellationScope> działania.

## <a name="the-cancellationscope-activity"></a>Działanie CancellationScope

<xref:System.Activities.Statements.CancellationScope>Działanie pozwala określić działanie dla logiki wykonywania i anulowania dla tego działania.

### <a name="using-the-cancellationscope-activity-designer"></a>Korzystanie z projektanta działań CancellationScope

Projektanta działań **CancellationScope** można znaleźć w kategorii **transakcji** **przybornika**. Aby otworzyć **Przybornik** , wybierz kartę **przybornika** Projektant przepływu pracy. Alternatywnie możesz wybrać **Przybornik** z menu **Widok** lub nacisnąć **klawisze CTRL** + **Alt** + **X**.

Projektanta działań **CancellationScope** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Porzucenie projektanta działań **CancellationScope** tworzy <xref:System.Activities.Statements.CancellationScope> działanie z domyślną wartością <xref:System.Activities.Activity.DisplayName%2A> CancellationScope. Edytuj <xref:System.Activities.Activity.DisplayName%2A> wartość w nagłówku projektanta działań **CancellationScope** . Można go również edytować w polu **DisplayName** siatki właściwości.

### <a name="the-cancellationscope-properties"></a>Właściwości CancellationScope

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.CancellationScope> właściwości i opisano sposób ich użycia w projektancie. <xref:System.Activities.Activity.DisplayName%2A>Właściwość można edytować w siatce właściwości, ale inne właściwości muszą być edytowane na Projektant przepływu pracy powierzchni.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Opcjonalna przyjazna nazwa <xref:System.Activities.Statements.CancellationScope> działania. Wartość domyślna to CancellationScope. Chociaż <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Prawda|Określa działanie, dla którego podano logikę anulowania. Aby dodać <xref:System.Activities.Statements.CancellationScope.Body%2A> działanie, upuść działanie z **przybornika** do pola **treść** w projektancie działań **CancellationScope** . Dodaj tekst wskazówki "upuść działanie tutaj".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Prawda|Określa działanie, które jest wykonywane w przypadku anulowania. Aby dodać <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> działanie, upuść działanie z **przybornika** do pola **CancellationHandler** w projektancie działań **CancellationScope** . Dodaj tekst wskazówki "upuść działanie tutaj".|

## <a name="see-also"></a>Zobacz też

- [Transakcja](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
