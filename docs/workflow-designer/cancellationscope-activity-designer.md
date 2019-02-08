---
title: Projektant przepływu pracy — CancellationScope, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43a818be208c7e07ef74a8f35923f3042bb8fad5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938166"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope, projektant działań

**CancellationScope** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.CancellationScope> działania.

## <a name="the-cancellationscope-activity"></a>Działania CancellationScope

<xref:System.Activities.Statements.CancellationScope> Działanie umożliwia określenie działania wykonywania i anulowania logiki dla tego działania.

### <a name="using-the-cancellationscope-activity-designer"></a>Za pomocą CancellationScope, Projektant działań

**CancellationScope** projektanta działań można znaleźć w **transakcji** kategorii **przybornika**. Aby otworzyć **przybornika**, wybierz opcję **przybornika** kartę projektanta przepływów pracy. Można także wybrać **przybornika** z **widoku** menu lub naciśnij klawisz **Ctrl**+**Alt** + **X**.

**CancellationScope** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy wszędzie tam, gdzie działań są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Upuszczanie **CancellationScope** tworzy projektanta działań <xref:System.Activities.Statements.CancellationScope> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> z CancellationScope. Edytuj <xref:System.Activities.Activity.DisplayName%2A> wartością w nagłówku **CancellationScope** projektanta działań. Można również edytować go w **DisplayName** pola siatki właściwości.

### <a name="the-cancellationscope-properties"></a>Właściwości działania CancellationScope

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.CancellationScope> właściwości i w tym artykule opisano, jak są używane w projektancie. <xref:System.Activities.Activity.DisplayName%2A> Właściwości można edytować w siatce właściwości, ale inne właściwości, należy edytować na powierzchni projektanta przepływów pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalna nazwa przyjazna <xref:System.Activities.Statements.CancellationScope> działania. Wartość domyślna to CancellationScope. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest bezwzględnie konieczne, jest najlepszym rozwiązaniem, aby użyć jednego.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Prawda|Określa działanie anulowania, który znajduje się logiki. Aby dodać <xref:System.Activities.Statements.CancellationScope.Body%2A> działania, listy działanie z **przybornika** do **treści** polu na **CancellationScope** Projektant działań. Dodaj tekst wskazówki "Upuść działanie tutaj".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Prawda|Określa działania, który jest wykonywany w przypadku anulowania. Aby dodać <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> działania, listy działanie z **przybornika** do **CancellationHandler** polu na **CancellationScope** Projektant działań. Dodaj tekst wskazówki "Upuść działanie tutaj".|

## <a name="see-also"></a>Zobacz także

- [Transakcja](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)