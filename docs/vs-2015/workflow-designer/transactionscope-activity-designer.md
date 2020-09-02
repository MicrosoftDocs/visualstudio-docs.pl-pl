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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670176"
---
# <a name="transactionscope-activity-designer"></a>TransactionScope, projektant działań
Projektant działań elementu **TransactionScope** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.TransactionScope> działania.

## <a name="the-transactionscope-activity"></a>Działanie TransactionScope
 <xref:System.Activities.Statements.TransactionScope>Działanie wykonuje zawarte działanie w ramach pojedynczej transakcji. Transakcja zatwierdza, gdy <xref:System.Activities.Statements.TransactionScope.Body%2A> działanie i wszyscy inni uczestnicy transakcji zostały zakończone pomyślnie.

### <a name="using-the-transactionscope-activity-designer"></a>Korzystanie z projektanta działań elementu TransactionScope
 Projektanta działań elementu **TransactionScope** można znaleźć w kategorii **transakcji** **przybornika**, do którego uzyskuje się dostęp, klikając kartę **przybornika** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierając pozycję **pasek narzędzi** w menu **Widok** lub CTRL + ALT + X).

 Projektanta działań elementu **TransactionScope** można przeciągać z **przybornika** i znajdować się na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.TransactionScope> działania z domyślną wartością <xref:System.Activities.Activity.DisplayName%2A> elementu TransactionScope. <xref:System.Activities.Activity.DisplayName%2A>Wartość można edytować w nagłówku projektanta działań elementu **TransactionScope** lub w polu **DisplayName** siatki właściwości.

### <a name="the-transactionscope-properties"></a>Właściwości elementu TransactionScope
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.TransactionScope> właściwości i opisano sposób ich użycia w projektancie. <xref:System.Activities.Activity.DisplayName%2A>Właściwości i <xref:System.Activities.Statements.TransactionScope.Body%2A> można edytować na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni. Natomiast inne właściwości muszą być edytowane w siatce właściwości.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Opcjonalna przyjazna nazwa <xref:System.Activities.Statements.TransactionScope> działania. Wartość domyślna to TransactionScope. Chociaż <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|Prawda|Określa działanie, które ma zostać wykonane w ramach jednej transakcji. Aby dodać <xref:System.Activities.Statements.TransactionScope.Body%2A> działanie, upuść działanie z **przybornika** do pola **treść** w projektancie działań elementu **TransactionScope** ze wskazówką text "upuść działanie tutaj".|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Prawda|Określa <xref:System.Transactions.IsolationLevel> dla tego elementu <xref:System.Activities.Statements.TransactionScope> .|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|Fałsz|Określa przedział czasu (sformatowany jako 00:00:00, który wskazuje godziny: minuty: sekundy), aby transakcja była ukończona. Wartość domyślna to 1 minuta (00:01:00).|
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure?qualifyHint=False&autoUpgrade=True>|Prawda|Określa wartość wskazującą, czy przepływ pracy powinien być przerwany w przypadku przerwania transakcji.|

## <a name="see-also"></a>Zobacz też
 [Potwierdzenie](../workflow-designer/confirm-activity-designer.md) [kompensaty](../workflow-designer/compensate-activity-designer.md) w usłudze [Transaction](../workflow-designer/transaction-activity-designers.md) [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md) [działanie CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)