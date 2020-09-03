---
title: CancellationScope — Projektant działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa41d63fa4f67037a8e98e72abc3e338ad894f70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659179"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope, projektant działań
Projektant działań **CancellationScope** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.CancellationScope> działania.

## <a name="the-cancellationscope-activity"></a>Działanie CancellationScope
 <xref:System.Activities.Statements.CancellationScope>Działanie pozwala określić działanie dla logiki wykonywania i anulowania dla tego działania.

### <a name="using-the-cancellationscope-activity-designer"></a>Korzystanie z projektanta działań CancellationScope
 Projektanta działań **CancellationScope** można znaleźć w kategorii **transakcji** **przybornika**, do którego uzyskuje się dostęp, klikając kartę **przybornika** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X).

 Projektanta działań **CancellationScope** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.CancellationScope> działania z wartością domyślną <xref:System.Activities.Activity.DisplayName%2A> CancellationScope. <xref:System.Activities.Activity.DisplayName%2A>Wartość można edytować w nagłówku projektanta działań **CancellationScope** lub w polu **DisplayName** siatki właściwości.

### <a name="the-cancellationscope-properties"></a>Właściwości CancellationScope
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.CancellationScope> właściwości i opisano sposób ich użycia w projektancie. <xref:System.Activities.Activity.DisplayName%2A>Właściwość można edytować w siatce właściwości, ale inne właściwości muszą być edytowane na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Opcjonalna przyjazna nazwa <xref:System.Activities.Statements.CancellationScope> działania. Wartość domyślna to CancellationScope. Chociaż <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Prawda|Określa działanie, dla którego podano logikę anulowania. Aby dodać <xref:System.Activities.Statements.CancellationScope.Body%2A> działanie, Usuń działanie z **przybornika** do pola **treść** w projektancie działań **CancellationScope** z podpowiedzią tekst "upuść działanie tutaj".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Prawda|Określa działanie, które jest wykonywane w przypadku anulowania. Aby dodać <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> działanie, upuść działanie z **przybornika** do pola **CancellationHandler** w projektancie działań **CancellationScope** z podpowiedzią text "upuść aktywność tutaj".|

## <a name="see-also"></a>Zobacz też
 Element [TransactionScope](../workflow-designer/transactionscope-activity-designer.md) [potwierdzenia](../workflow-designer/confirm-activity-designer.md) [działanie CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [transakcji](../workflow-designer/transaction-activity-designers.md) [kompensaty](../workflow-designer/compensate-activity-designer.md)