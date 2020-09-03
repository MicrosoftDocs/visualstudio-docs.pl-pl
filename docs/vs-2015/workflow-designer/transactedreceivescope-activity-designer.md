---
title: TransactedReceiveScope — Projektant działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c4230e4b598553f5fefbc3b97663fd42320ee1e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72607017"
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope, projektant działań
Projektant **TransactedReceiveScope** służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.

## <a name="the-transactedreceivescope-activity"></a>Działanie TransactedReceiveScope
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>Działanie umożliwia przepływ transakcji do transakcji serwera utworzonych przez przepływ pracy lub dyspozytora.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Korzystanie z projektanta działań TransactedReceiveScope
 Projektanta działań **TransactedReceiveScope** można znaleźć w kategorii **wiadomości** w **przyborniku**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz pozycję **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X).

 Projektanta działań **TransactedReceiveScope** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, wszędzie tam gdzie działania są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania z domyślną wartością **DisplayName** elementu TransactedReceiveScope. <xref:System.Activities.Activity.DisplayName%2A>Można edytować w nagłówku projektanta działań **TransactedReceiveScope** lub w polu **DisplayName** siatki właściwości.

 Projektant **TransactedReceiveScope** zawiera pola **żądanie** i **treść** . Są one używane do konfigurowania <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> właściwości, która określa <xref:System.ServiceModel.Activities.Receive> działanie i <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> Właściwość, która określa inne <xref:System.Activities.Activity> . <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>Tworzy transakcję. Transakcja jest następnie prowadzona dla zakresu, <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> tak aby wszystkie działania w ramach tego zakresu były wykonywane w ramach tej transakcji.

### <a name="the-transactedreceivescope-properties"></a>Właściwości TransactedReceiveScope
 W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.TransactedReceiveScope> właściwości i opisano sposób ich użycia w projektancie. Tę <xref:System.Activities.Activity.DisplayName%2A> Właściwość można edytować w siatce właściwości lub na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, ale inne muszą być edytowane na powierzchni projektowej.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Opcjonalna przyjazna nazwa <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania. Wartość domyślna to TransactedReceiveScope.<br /><br /> Chociaż <xref:System.Activities.Activity.DisplayName%2A> nazwa nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie nazwy wyświetlanej.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Prawda|Odrzuca <xref:System.ServiceModel.Activities.Receive> działanie do bloku **żądania** na powierzchni projektanta aktywności.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|Fałsz|Opuszcza <xref:System.Activities.Activity> blok **treści** na powierzchni projektanta aktywności.|

## <a name="see-also"></a>Zobacz też
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [odbieranie](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)