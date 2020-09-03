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
ms.openlocfilehash: 1bfe43f410709a924b0ebdb0cf6afbb8d30a8fcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395345"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply, projektant szablonów
Szablon **SendAndReceiveReply** służy do tworzenia pary wstępnie skonfigurowanych <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań w ramach <xref:System.Activities.Statements.Sequence> działania, które są skorelowane jako część wzorca wymiany komunikatów żądania/odpowiedzi na komputerze klienckim.

## <a name="the-sendandreceivereply-template"></a>Szablon SendAndReceiveReply
 Dodanie szablonu **SendAndReceiveReply** wykonuje trzy rzeczy oprócz tworzenia <xref:System.ServiceModel.Activities.Send> działań i <xref:System.ServiceModel.Activities.ReceiveReply> w ramach <xref:System.Activities.Statements.Sequence> działania:

1. Konfiguruje <xref:System.ServiceModel.Activities.Send.OperationName%2A> <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> właściwości <xref:System.ServiceModel.Activities.Send> działania.

2. Wiąże <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> Właściwość <xref:System.ServiceModel.Activities.ReceiveReply> działania z <xref:System.ServiceModel.Activities.Send> działaniem.

3. Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienną w działaniu nadrzędnym.

### <a name="using-the-sendandreceivereply-template-designer"></a>Korzystanie z projektanta szablonów SendAndReceiveReply
 Projektanta działań **SendAndReceiveReply** można znaleźć w kategorii **wiadomości** w **przyborniku**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz pozycję **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X).

 Projektanta działań **SendAndReceiveReply** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, wszędzie tam gdzie działania są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Send> działania, które można skonfigurować za pomocą projektanta działania **wysyłania** , a następnie skorelowane <xref:System.ServiceModel.Activities.ReceiveReply> , które można skonfigurować za pomocą projektanta **ReceiveReplyForSend** .

 [!INCLUDE[crabout](../includes/crabout-md.md)] Korzystanie z projektanta **wysyłania** do konfigurowania <xref:System.ServiceModel.Activities.Send> działania, patrz temat [wysyłanie](../workflow-designer/send-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] Aby skonfigurować działanie, użyj projektanta **ReceiveReplyForSend** w <xref:System.ServiceModel.Activities.ReceiveReply> następującej sekcji.

### <a name="properties-of-receivereply"></a>Właściwości ReceiveReply
 W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.ReceiveReply> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre można edytować na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni projektanta.

|                                 Nazwa właściwości                                 | Wymagany |                                                                                                                                                                                                                                                                                                                                                        Użycie                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  Fałsz   |                                                                                                                                                                                            Opcjonalna przyjazna nazwa <xref:System.ServiceModel.Activities.ReceiveReply> działania. Wartość domyślna to ReceiveReplyForSend.<br /><br /> Chociaż użycie wartości innej niż domyślna dla elementu friendly <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie takiej wartości.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   Prawda   | Odwołanie do <xref:System.ServiceModel.Activities.Send> działania sparowanego z tym <xref:System.ServiceModel.Activities.ReceiveReply> działaniem. Ta właściwość nie może mieć **wartości null**. <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działania są używane razem z klientem w celu modelowania wzorca komunikatów żądania/odpowiedzi. Ta właściwość określa, które <xref:System.ServiceModel.Activities.Send> działanie jest sparowane. W projektancie nie można edytować tej właściwości, ponieważ jest ona automatycznie powiązana z <xref:System.ServiceModel.Activities.Send> działaniem, z którego zostało utworzone <xref:System.ServiceModel.Activities.ReceiveReply> działanie. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  Fałsz   |                        Określa komunikat lub zawartość parametru do odebrania. Może to być <xref:System.ServiceModel.Activities.ReceiveMessageContent> działanie lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działanie. Edytuj tę właściwość, klikając przycisk wielokropka obok pola **zawartość** w siatce właściwości lub klikając polecenie **Definiuj...** obok etykiety **zawartość** na powierzchni projektanta działań **odbioru** . Wyświetla okno dialogowe **definicji zawartości** . [!INCLUDE[crabout](../includes/crabout-md.md)] Jak korzystać z tego pola, zobacz temat okno [dialogowe Definicja zawartości](../workflow-designer/content-definition-dialog-box.md) .                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  Fałsz   |              Określa kolekcję <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które inicjują wiele <xref:System.ServiceModel.Activities.CorrelationHandle> obiektów, które konfigurują to <xref:System.ServiceModel.Activities.Receive> działanie w ramach przepływu pracy. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> właściwości w siatce właściwości, aby otworzyć okno dialogowe **Dodawanie inicjatorów korelacji** . [!INCLUDE[crabout](../includes/crabout-md.md)] Korzystając z tego pola, zobacz okno [dialogowe Dodawanie CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) .               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  Fałsz   |                                                                                                                                                                                                                                               Określa nagłówek akcji wiadomości. Jeśli nie jest on jawnie ustawiony, jego wartość domyślna to:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`.                                                                                                                                                                                                                                              |

## <a name="see-also"></a>Zobacz też
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [odbieranie](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)