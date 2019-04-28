---
title: Projektant przepływu pracy — Compensate, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c55ecd8e3402d927b11cc00d18d6d134a5b25681
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949841"
---
# <a name="compensate-activity-designer"></a>Compensate, projektant działań

**Compensate** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Compensate> działania.

## <a name="the-compensate-activity"></a>Kompensacji działania

<xref:System.Activities.Statements.Compensate> Działania jawnie wywołuje <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> dla działania zawarte w <xref:System.Activities.Statements.CompensableActivity>. Jeśli <xref:System.Activities.Statements.Compensate> działanie nie jest używane w ramach <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, lub <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> z <xref:System.Activities.Statements.CompensableActivity>, a następnie należy określić <xref:System.Activities.Statements.Compensate.Target%2A> właściwości.

<xref:System.Activities.Statements.CompensationToken> Określony przez <xref:System.Activities.Statements.Compensate.Target%2A> udostępnia środki do jawnie potwierdzić, lub kompensacji <xref:System.Activities.Statements.CompensableActivity> po <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> została ukończona pomyślnie.

### <a name="using-the-compensate-activity-designer"></a>Za pomocą Compensate, Projektant działań

**Compensate** projektanta działań można znaleźć w **transakcji** kategorii **przybornika**. Aby otworzyć **przybornika**, wybierz opcję **przybornika** karty w lewej części projektanta przepływów pracy. Można także wybrać **przybornika** z **widoku** menu lub naciśnij klawisz **Ctrl**+**Alt** + **X**.

**Compensate** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy wszędzie tam, gdzie działań są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Projektant działań porzucenie tworzy <xref:System.Activities.Statements.Compensate> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> z Compensate. <xref:System.Activities.Activity.DisplayName%2A> Wartość może być edytowana w nagłówku **Compensate** projektanta działań lub **DisplayName** pola siatki właściwości.

### <a name="the-compensate-properties"></a>Kompensacji właściwości

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.CancellationScope> właściwości i w tym artykule opisano, jak są używane w projektancie. <xref:System.Activities.Activity.DisplayName%2A> Właściwości można edytować w siatce właściwości lub na powierzchni projektanta przepływów pracy. Edytuj <xref:System.Activities.Statements.Compensate.Target%2A> właściwość w siatce właściwości.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalny przyjazna nazwa <xref:System.Activities.Statements.Compensate> działania. Wartość domyślna to Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|Prawda|Określa <xref:System.Activities.InArgument%601> zawierający <xref:System.Activities.Statements.CompensationToken> tego <xref:System.Activities.Statements.Compensate> działania.|

## <a name="see-also"></a>Zobacz także

- [Transakcja](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate, projektant działań](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)