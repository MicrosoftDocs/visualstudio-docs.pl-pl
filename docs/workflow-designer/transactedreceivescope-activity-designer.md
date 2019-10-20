---
title: Projektant przepływu pracy — Projektant działań TransactedReceiveScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf5a52a6a806d72632bf31a7c73e41677e9ddaf9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654289"
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope, projektant działań

Projektant **TransactedReceiveScope** służy do tworzenia i konfigurowania działania <xref:System.ServiceModel.Activities.TransactedReceiveScope>.

## <a name="the-transactedreceivescope-activity"></a>Działanie TransactedReceiveScope

Działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> umożliwia przepływ transakcji do transakcji serwera utworzonych przez przepływ pracy lub dyspozytora.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Korzystanie z projektanta działań TransactedReceiveScope

Dostęp do projektanta działań **TransactedReceiveScope** w kategorii **Obsługa wiadomości** w **przyborniku**. Projektanta działań **TransactedReceiveScope** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam gdzie działania są zwykle umieszczane. Spowoduje to utworzenie działania <xref:System.ServiceModel.Activities.TransactedReceiveScope> z domyślną wartością **DisplayName** TransactedReceiveScope. @No__t_0 można edytować w nagłówku projektanta działań **TransactedReceiveScope** lub w polu **DisplayName** siatki właściwości.

Projektant **TransactedReceiveScope** zawiera pola **żądanie** i **treść** . Są one używane do konfigurowania właściwości <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>, która określa działanie <xref:System.ServiceModel.Activities.Receive> i Właściwość <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>, która określa inne <xref:System.Activities.Activity>. @No__t_0 tworzy transakcję. Transakcja jest następnie prowadzona dla zakresu <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> tak, aby wszystkie działania w ramach tego zakresu były wykonywane w ramach tej transakcji.

### <a name="the-transactedreceivescope-properties"></a>Właściwości TransactedReceiveScope

W poniższej tabeli przedstawiono właściwości <xref:System.ServiceModel.Activities.TransactedReceiveScope> i opisano sposób ich używania w projektancie. Te właściwości <xref:System.Activities.Activity.DisplayName%2A> można edytować w siatce właściwości lub na powierzchni Projektant przepływu pracy, ale inne muszą być edytowane na powierzchni projektowej.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalna przyjazna nazwa działania <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Wartość domyślna to TransactedReceiveScope.<br /><br /> Chociaż nazwa <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie nazwy wyświetlanej.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Oznacza|Odrzuca działanie <xref:System.ServiceModel.Activities.Receive> do bloku **żądania** na powierzchni projektanta aktywności.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Odrzuca <xref:System.Activities.Activity> w bloku **treści** na powierzchni projektanta aktywności.|

## <a name="see-also"></a>Zobacz także

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)