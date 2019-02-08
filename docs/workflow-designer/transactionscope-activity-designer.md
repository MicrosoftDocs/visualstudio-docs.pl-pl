---
title: Projektant przepływu pracy — TransactionScope, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e84312518c19ef2a041091c5e2439dd7fb312c69
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55948891"
---
# <a name="transactionscope-activity-designer"></a>TransactionScope, projektant działań

**TransactionScope** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.TransactionScope> działania.

## <a name="the-transactionscope-activity"></a>Działanie elementu TransactionScope

<xref:System.Activities.Statements.TransactionScope> Działanie wykonuje zawarte działanie w ramach jednej transakcji. Zatwierdzenia transakcji, gdy <xref:System.Activities.Statements.TransactionScope.Body%2A> działanie i innych uczestników transakcji zostały ukończone pomyślnie.

### <a name="using-the-transactionscope-activity-designer"></a>Za pomocą TransactionScope, Projektant działań

Dostęp do **TransactionScope** projektanta działań w **transakcji** kategorii **przybornika**. **TransactionScope** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy wszędzie tam, gdzie działań są zazwyczaj umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.TransactionScope> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> elementu TransactionScope. <xref:System.Activities.Activity.DisplayName%2A> Wartość może być edytowana w nagłówku **TransactionScope** projektanta działań lub **DisplayName** pola siatki właściwości.

### <a name="the-transactionscope-properties"></a>Właściwości elementu TransactionScope

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.TransactionScope> właściwości i w tym artykule opisano, jak są używane w projektancie. <xref:System.Activities.Activity.DisplayName%2A> i <xref:System.Activities.Statements.TransactionScope.Body%2A> właściwości można edytować na powierzchni projektanta przepływów pracy. Ale inne właściwości, należy edytować w siatce właściwości.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalna nazwa przyjazna <xref:System.Activities.Statements.TransactionScope> działania. Wartość domyślna to TransactionScope. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest bezwzględnie konieczne, jest najlepszym rozwiązaniem, aby użyć jednego.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|Prawda|Określa działanie do wykonania w ramach jednej transakcji. Można dodać <xref:System.Activities.Statements.TransactionScope.Body%2A> działania, listy działanie z **przybornika** do **treści** polu na **TransactionScope** projektanta działań z tekst wskazówki "listy działanie w tym miejscu".|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Prawda|Określa <xref:System.Transactions.IsolationLevel> tego <xref:System.Activities.Statements.TransactionScope>.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Określa przedział czasu (w formacie 00:00:00, co oznacza godziny: minuty: sekundy) zawierającej transakcji zakończyć. Wartość domyślna to 1 minuta (00: 01:00).|
|[System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|Prawda|Określa wartość, która wskazuje, czy przepływ pracy powinien przerwane w przypadku transakcji przerywa.|

## <a name="see-also"></a>Zobacz także

- [Transakcja](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)