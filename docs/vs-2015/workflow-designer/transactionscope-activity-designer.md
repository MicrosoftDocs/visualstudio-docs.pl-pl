---
title: Projektant działań TransactionScope | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b5a1d38ea37896cedcd2166c42f37ce037a1c4cd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670176"
---
# <a name="transactionscope-activity-designer"></a>TransactionScope, projektant działań
Projektant działań elementu **TransactionScope** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.TransactionScope>.

## <a name="the-transactionscope-activity"></a>Działanie TransactionScope
 Działanie <xref:System.Activities.Statements.TransactionScope> wykonuje zawarte działanie w jednej transakcji. Transakcja zatwierdza, gdy działanie <xref:System.Activities.Statements.TransactionScope.Body%2A> i wszystkich innych uczestników transakcji zakończyło się pomyślnie.

### <a name="using-the-transactionscope-activity-designer"></a>Korzystanie z projektanta działań elementu TransactionScope
 Projektanta działań elementu **TransactionScope** można znaleźć w kategorii **transakcji** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** w [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz pozycję **pasek narzędzi** z **widoku).** menu lub CTRL + ALT + X.)

 Projektanta działań elementu **TransactionScope** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.TransactionScope> z domyślnym <xref:System.Activities.Activity.DisplayName%2A> elementu TransactionScope. Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań elementu **TransactionScope** lub w polu **DisplayName** siatki właściwości.

### <a name="the-transactionscope-properties"></a>Właściwości elementu TransactionScope
 W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.TransactionScope> i opisano sposób ich używania w projektancie. Właściwości <xref:System.Activities.Activity.DisplayName%2A> i <xref:System.Activities.Statements.TransactionScope.Body%2A> można edytować na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni. Natomiast inne właściwości muszą być edytowane w siatce właściwości.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalna przyjazna nazwa działania <xref:System.Activities.Statements.TransactionScope>. Wartość domyślna to TransactionScope. Mimo że wartość <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|Oznacza|Określa działanie, które ma zostać wykonane w ramach jednej transakcji. Aby dodać działanie <xref:System.Activities.Statements.TransactionScope.Body%2A>, upuść działanie z **przybornika** do pola **treść** w projektancie działań elementu **TransactionScope** ze wskazówką text "upuść aktywność tutaj".|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Oznacza|Określa <xref:System.Transactions.IsolationLevel> dla tego <xref:System.Activities.Statements.TransactionScope>.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Określa przedział czasu (sformatowany jako 00:00:00, który wskazuje godziny: minuty: sekundy), aby transakcja była ukończona. Wartość domyślna to 1 minuta (00:01:00).|
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure?qualifyHint=False&autoUpgrade=True>|Oznacza|Określa wartość wskazującą, czy przepływ pracy powinien być przerwany w przypadku przerwania transakcji.|

## <a name="see-also"></a>Zobacz też
 [Potwierdzenie](../workflow-designer/confirm-activity-designer.md) [kompensaty](../workflow-designer/compensate-activity-designer.md) w usłudze [Transaction](../workflow-designer/transaction-activity-designers.md) [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md) [działanie CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)