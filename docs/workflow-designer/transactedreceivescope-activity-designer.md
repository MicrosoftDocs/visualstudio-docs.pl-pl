---
title: TransactedReceiveScope, Projektant działań
description: W Projektant przepływu pracy można dowiedzieć się, jak utworzyć i skonfigurować działanie TransactedReceiveScope przy użyciu projektanta TransactedReceiveScope.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eceb0776fd1cb5e850dab2b97ab6e7e56a684ebd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838025"
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope, projektant działań

Projektant **TransactedReceiveScope** służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.

## <a name="the-transactedreceivescope-activity"></a>Działanie TransactedReceiveScope

<xref:System.ServiceModel.Activities.TransactedReceiveScope>Działanie umożliwia przepływ transakcji do transakcji serwera utworzonych przez przepływ pracy lub dyspozytora.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Korzystanie z projektanta działań TransactedReceiveScope

Dostęp do projektanta działań **TransactedReceiveScope** w kategorii **Obsługa wiadomości** w **przyborniku**. Projektanta działań **TransactedReceiveScope** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam gdzie działania są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania z domyślną wartością **DisplayName** elementu TransactedReceiveScope. <xref:System.Activities.Activity.DisplayName%2A>Można edytować w nagłówku projektanta działań **TransactedReceiveScope** lub w polu **DisplayName** siatki właściwości.

Projektant **TransactedReceiveScope** zawiera pola **żądanie** i **treść** . Są one używane do konfigurowania <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> właściwości, która określa <xref:System.ServiceModel.Activities.Receive> działanie i <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> Właściwość, która określa inne <xref:System.Activities.Activity> . <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>Tworzy transakcję. Transakcja jest następnie prowadzona dla zakresu, <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> tak aby wszystkie działania w ramach tego zakresu były wykonywane w ramach tej transakcji.

### <a name="the-transactedreceivescope-properties"></a>Właściwości TransactedReceiveScope

W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.TransactedReceiveScope> właściwości i opisano sposób ich użycia w projektancie. Tę <xref:System.Activities.Activity.DisplayName%2A> Właściwość można edytować w siatce właściwości lub na Projektant przepływu pracy powierzchni, ale inne muszą być edytowane na powierzchni projektowej.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Opcjonalna przyjazna nazwa <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania. Wartość domyślna to TransactedReceiveScope.<br /><br /> Chociaż <xref:System.Activities.Activity.DisplayName%2A> nazwa nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie nazwy wyświetlanej.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Prawda|Odrzuca <xref:System.ServiceModel.Activities.Receive> działanie do bloku **żądania** na powierzchni projektanta aktywności.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|Fałsz|Opuszcza <xref:System.Activities.Activity> blok **treści** na powierzchni projektanta aktywności.|

## <a name="see-also"></a>Zobacz też

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Odbieranie](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Wysyłanie](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)