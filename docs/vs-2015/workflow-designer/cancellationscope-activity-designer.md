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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659179"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope, projektant działań
Projektant działań **CancellationScope** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.CancellationScope>.

## <a name="the-cancellationscope-activity"></a>Działanie CancellationScope
 Działanie <xref:System.Activities.Statements.CancellationScope> pozwala określić działanie dla logiki wykonywania i anulowania dla tego działania.

### <a name="using-the-cancellationscope-activity-designer"></a>Korzystanie z projektanta działań CancellationScope
 Projektanta działań **CancellationScope** można znaleźć w kategorii **transakcji** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** w [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz pozycję **pasek narzędzi** z widoku) **.** lub CTRL + ALT + X.)

 Projektanta działań **CancellationScope** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.CancellationScope> przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> CancellationScope. Wartość <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań **CancellationScope** lub w polu **DisplayName** siatki właściwości.

### <a name="the-cancellationscope-properties"></a>Właściwości CancellationScope
 W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.CancellationScope> i opisano sposób ich używania w projektancie. Właściwość <xref:System.Activities.Activity.DisplayName%2A> można edytować w siatce właściwości, ale inne właściwości muszą być edytowane na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalna przyjazna nazwa działania <xref:System.Activities.Statements.CancellationScope>. Wartość domyślna to CancellationScope. Mimo że wartość <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Oznacza|Określa działanie, dla którego podano logikę anulowania. Aby dodać działanie <xref:System.Activities.Statements.CancellationScope.Body%2A>, Usuń działanie z **przybornika** do pola **treść** w projektancie działań **CancellationScope** ze wskazówkami tekst "upuść aktywność tutaj".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Oznacza|Określa działanie, które jest wykonywane w przypadku anulowania. Aby dodać działanie <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, upuść działanie z **przybornika** do pola **CancellationHandler** w projektancie działań **CancellationScope** z tekstem wskazówki "upuść działanie tutaj".|

## <a name="see-also"></a>Zobacz też
 Element [TransactionScope](../workflow-designer/transactionscope-activity-designer.md) [potwierdzenia](../workflow-designer/confirm-activity-designer.md) [działanie CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [transakcji](../workflow-designer/transaction-activity-designers.md) [kompensaty](../workflow-designer/compensate-activity-designer.md)