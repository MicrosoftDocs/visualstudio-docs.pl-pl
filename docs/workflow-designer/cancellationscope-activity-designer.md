---
title: Projektant przepływu pracy — Projektant działań CancellationScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a2fd36d81f774ca48cca170b8a4a256d73cf1f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650701"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope, projektant działań

Projektant działań **CancellationScope** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.CancellationScope>.

## <a name="the-cancellationscope-activity"></a>Działanie CancellationScope

Działanie <xref:System.Activities.Statements.CancellationScope> pozwala określić działanie dla logiki wykonywania i anulowania dla tego działania.

### <a name="using-the-cancellationscope-activity-designer"></a>Korzystanie z projektanta działań CancellationScope

Projektanta działań **CancellationScope** można znaleźć w kategorii **transakcji** **przybornika**. Aby otworzyć **Przybornik**, wybierz kartę **przybornika** Projektant przepływu pracy. Alternatywnie wybierz pozycję **Przybornik** z menu **Widok** lub naciśnij **klawisze CTRL** +**Alt** +**X**.

Projektanta działań **CancellationScope** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence>. Porzucenie projektanta działań **CancellationScope** tworzy działanie <xref:System.Activities.Statements.CancellationScope> z domyślnym <xref:System.Activities.Activity.DisplayName%2A>em CancellationScope. Edytuj wartość <xref:System.Activities.Activity.DisplayName%2A> w nagłówku projektanta działań **CancellationScope** . Można go również edytować w polu **DisplayName** siatki właściwości.

### <a name="the-cancellationscope-properties"></a>Właściwości CancellationScope

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.CancellationScope> i opisano sposób ich używania w projektancie. Właściwość <xref:System.Activities.Activity.DisplayName%2A> można edytować w siatce właściwości, ale inne właściwości muszą być edytowane na Projektant przepływu pracy powierzchni.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalna przyjazna nazwa działania <xref:System.Activities.Statements.CancellationScope>. Wartość domyślna to CancellationScope. Mimo że wartość <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Oznacza|Określa działanie, dla którego podano logikę anulowania. Aby dodać działanie <xref:System.Activities.Statements.CancellationScope.Body%2A>, Usuń działanie z **przybornika** do pola **treść** w projektancie działań **CancellationScope** . Dodaj tekst wskazówki "upuść działanie tutaj".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Oznacza|Określa działanie, które jest wykonywane w przypadku anulowania. Aby dodać działanie <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, upuść działanie z **przybornika** do pola **CancellationHandler** w projektancie działań **CancellationScope** . Dodaj tekst wskazówki "upuść działanie tutaj".|

## <a name="see-also"></a>Zobacz także

- [Transakcja](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)