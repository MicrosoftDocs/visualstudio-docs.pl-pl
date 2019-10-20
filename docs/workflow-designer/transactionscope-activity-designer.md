---
title: Projektant przepływu pracy — Projektant działań TransactionScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5d557fb91c52c33022a161bada169d4332bac6b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649832"
---
# <a name="transactionscope-activity-designer"></a>TransactionScope, projektant działań

Projektant działań elementu **TransactionScope** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.TransactionScope>.

## <a name="the-transactionscope-activity"></a>Działanie TransactionScope

Działanie <xref:System.Activities.Statements.TransactionScope> wykonuje zawarte działanie w jednej transakcji. Transakcja zatwierdza, gdy działanie <xref:System.Activities.Statements.TransactionScope.Body%2A> i wszystkich innych uczestników transakcji zakończyło się pomyślnie.

### <a name="using-the-transactionscope-activity-designer"></a>Korzystanie z projektanta działań elementu TransactionScope

Dostęp do projektanta działań elementu **TransactionScope** w kategorii **transakcji** **przybornika**. Projektanta działań elementu **TransactionScope** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.TransactionScope> z domyślnym <xref:System.Activities.Activity.DisplayName%2A> elementu TransactionScope. Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań elementu **TransactionScope** lub w polu **DisplayName** siatki właściwości.

### <a name="the-transactionscope-properties"></a>Właściwości elementu TransactionScope

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.TransactionScope> i opisano sposób ich używania w projektancie. Właściwości <xref:System.Activities.Activity.DisplayName%2A> i <xref:System.Activities.Statements.TransactionScope.Body%2A> można edytować na Projektant przepływu pracy powierzchni. Natomiast inne właściwości muszą być edytowane w siatce właściwości.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalna przyjazna nazwa działania <xref:System.Activities.Statements.TransactionScope>. Wartość domyślna to TransactionScope. Mimo że wartość <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|Oznacza|Określa działanie, które ma zostać wykonane w ramach jednej transakcji. Aby dodać działanie <xref:System.Activities.Statements.TransactionScope.Body%2A>, upuść działanie z **przybornika** do pola **treść** w projektancie działań elementu **TransactionScope** ze wskazówką text "upuść aktywność tutaj".|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Oznacza|Określa <xref:System.Transactions.IsolationLevel> dla tego <xref:System.Activities.Statements.TransactionScope>.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Określa przedział czasu (sformatowany jako 00:00:00, który wskazuje godziny: minuty: sekundy), aby transakcja była ukończona. Wartość domyślna to 1 minuta (00:01:00).|
|[System. Activities. Statements. TransactionScope. AbortInstanceOnTransactionFailure](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|Oznacza|Określa wartość wskazującą, czy przepływ pracy powinien być przerwany w przypadku przerwania transakcji.|

## <a name="see-also"></a>Zobacz także

- [Transakcja](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)