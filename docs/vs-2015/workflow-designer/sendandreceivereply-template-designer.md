---
title: Projektant szablonów SendAndReceiveReply | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4ecb0e201c4351a8a117d1e35aca97866b2beb89
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663268"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply, projektant szablonów
Szablon **SendAndReceiveReply** służy do tworzenia pary wstępnie skonfigurowanych działań <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> w ramach działania <xref:System.Activities.Statements.Sequence>, które są skorelowane jako część wzorca wymiany komunikatów żądania/odpowiedzi na kliencie.

## <a name="the-sendandreceivereply-template"></a>Szablon SendAndReceiveReply
 Dodanie szablonu **SendAndReceiveReply** wykonuje trzy rzeczy oprócz tworzenia <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań w ramach <xref:System.Activities.Statements.Sequence> działania:

1. Konfiguruje <xref:System.ServiceModel.Activities.Send.OperationName%2A>, <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> właściwości działania <xref:System.ServiceModel.Activities.Send>.

2. Wiąże Właściwość <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> działania <xref:System.ServiceModel.Activities.ReceiveReply> z działaniem <xref:System.ServiceModel.Activities.Send>.

3. Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienną w działaniu nadrzędnym.

### <a name="using-the-sendandreceivereply-template-designer"></a>Korzystanie z projektanta szablonów SendAndReceiveReply
 Projektanta działań **SendAndReceiveReply** można znaleźć w kategorii **wiadomości** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** w [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz pozycję **pasek narzędzi** z **widoku).** lub CTRL + ALT + X.)

 Projektanta działań **SendAndReceiveReply** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchnię, wszędzie tam gdzie działania są zwykle umieszczane. Spowoduje to utworzenie działania <xref:System.ServiceModel.Activities.Send>, które można skonfigurować za pomocą projektanta działania **wysyłania** i skorelowane <xref:System.ServiceModel.Activities.ReceiveReply>, które można skonfigurować za pomocą projektanta **ReceiveReplyForSend** .

 [!INCLUDE[crabout](../includes/crabout-md.md)] przy użyciu projektanta **wysyłania** do konfigurowania działania <xref:System.ServiceModel.Activities.Send>, zobacz temat [wysyłanie](../workflow-designer/send-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] pomocą projektanta **ReceiveReplyForSend** do skonfigurowania działania <xref:System.ServiceModel.Activities.ReceiveReply>, zobacz następującą sekcję.

### <a name="properties-of-receivereply"></a>Właściwości ReceiveReply
 W poniższej tabeli przedstawiono właściwości <xref:System.ServiceModel.Activities.ReceiveReply> i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na [!INCLUDE[wfd2](../includes/wfd2-md.md)]designer powierzchni.

|                                 Nazwa właściwości                                 | Wymagane |                                                                                                                                                                                                                                                                                                                                                        Użycie                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            Opcjonalna przyjazna nazwa działania <xref:System.ServiceModel.Activities.ReceiveReply>. Wartość domyślna to ReceiveReplyForSend.<br /><br /> Chociaż użycie wartości innej niż domyślna dla przyjaznej <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie takiej wartości.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   Oznacza   | Odwołanie do działania <xref:System.ServiceModel.Activities.Send> sparowane z tym działaniem <xref:System.ServiceModel.Activities.ReceiveReply>. Ta właściwość nie może mieć **wartości null**. działania <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> są używane razem z klientem w celu modelowania wzorca komunikatów żądania/odpowiedzi. Ta właściwość określa, które <xref:System.ServiceModel.Activities.Send> działania są sparowane. W projektancie nie można edytować tej właściwości, ponieważ jest ona automatycznie powiązana z działaniem <xref:System.ServiceModel.Activities.Send>, z którego zostało utworzone działanie <xref:System.ServiceModel.Activities.ReceiveReply>. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        Określa komunikat lub zawartość parametru do odebrania. Może to być działanie <xref:System.ServiceModel.Activities.ReceiveMessageContent> lub <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Edytuj tę właściwość, klikając przycisk wielokropka obok pola **zawartość** w siatce właściwości lub klikając polecenie **Definiuj...** obok etykiety **zawartość** na powierzchni projektanta działań **odbioru** . Wyświetla okno dialogowe **definicji zawartości** . [!INCLUDE[crabout](../includes/crabout-md.md)] korzystania z tego pola, zobacz temat okno [dialogowe Definicja zawartości](../workflow-designer/content-definition-dialog-box.md) .                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              Określa kolekcję obiektów <xref:System.ServiceModel.Activities.CorrelationInitializer>, które inicjują wiele obiektów <xref:System.ServiceModel.Activities.CorrelationHandle>, które konfigurują to działanie <xref:System.ServiceModel.Activities.Receive> w ramach przepływu pracy. Kliknij przycisk wielokropka obok właściwości <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> w siatce właściwości, aby otworzyć okno dialogowe **Dodawanie inicjatorów korelacji** . [!INCLUDE[crabout](../includes/crabout-md.md)] przy użyciu tego pola, zobacz okno [dialogowe Dodawanie CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) .               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               Określa nagłówek akcji wiadomości. Jeśli nie jest on jawnie ustawiony, jego wartość domyślna to:<br /><br /> <strong>https://tempuri.org/{service obszar nazw kontraktu} Nazwa kontraktu/{Service}/{Operation nazwa}.</strong>                                                                                                                                                                                                                                               |

## <a name="see-also"></a>Zobacz też
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [odbieranie](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)