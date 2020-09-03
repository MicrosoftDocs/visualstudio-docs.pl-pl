---
title: Projektant szablonów ReceiveAndSendReply | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c00eed244867cfd38b20f6a8f065fc6da006801
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395392"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply, projektant szablonów
Szablon **ReceiveAndSendReply** służy do tworzenia pary wstępnie skonfigurowanych <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań w ramach <xref:System.Activities.Statements.Sequence> działania, które są skorelowane jako część wzorca wymiany komunikatów żądania/odpowiedzi na serwerze.

## <a name="the-receiveandsendreply-template"></a>Szablon ReceiveAndSendReply
 Dodanie szablonu **ReceiveAndSendReply** wykonuje trzy rzeczy oprócz tworzenia <xref:System.ServiceModel.Activities.Receive> działań i działania <xref:System.ServiceModel.Activities.SendReply> z <xref:System.Activities.Statements.Sequence> działaniem:

1. Konfiguruje <xref:System.ServiceModel.Activities.Receive.OperationName%2A> <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> właściwości <xref:System.ServiceModel.Activities.Receive> działania.

2. Wiąże <xref:System.ServiceModel.Activities.SendReply.Request%2A> Właściwość <xref:System.ServiceModel.Activities.Receive> działania z <xref:System.ServiceModel.Activities.Send> działaniem.

3. Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienną w działaniu nadrzędnym.

### <a name="using-the-receiveandsendreply-template-designer"></a>Korzystanie z projektanta szablonów ReceiveAndSendReply
 Projektanta działań **ReceiveAndSendReply** można znaleźć w kategorii **wiadomości** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** w [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz pozycję **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X).

 Projektanta działań **ReceiveAndSendReply** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, wszędzie tam gdzie działania są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Receive> działania, które można skonfigurować za pomocą projektanta działania **wysyłania** , a następnie skorelowane <xref:System.ServiceModel.Activities.SendReply> , które można skonfigurować za pomocą projektanta SendReplyToReceive.

 [!INCLUDE[crabout](../includes/crabout-md.md)]Aby skonfigurować **Receive** działanie za pomocą projektanta odbioru <xref:System.ServiceModel.Activities.Receive> , zobacz temat [odbieranie](../workflow-designer/receive-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] Aby skonfigurować działanie, użyj projektanta **SendReplyToReceive** w <xref:System.ServiceModel.Activities.SendReply> następującej sekcji.

### <a name="properties-of-sendreply"></a>Właściwości działania SendReply
 W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.SendReply> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre można edytować na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni projektanta.

|                               Nazwa właściwości                                | Wymagany |                                                                                                                                                                                                                                                                                                                                                      Użycie                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  Fałsz   |                                                                                                                                                                                            Opcjonalna przyjazna nazwa <xref:System.ServiceModel.Activities.SendReply> działania. Wartość domyślna to SendReplyToReceive.<br /><br /> Chociaż użycie wartości innej niż domyślna dla elementu friendly <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie takiej wartości.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   Prawda   | Odwołanie do <xref:System.ServiceModel.Activities.Receive> działania sparowanego z tym <xref:System.ServiceModel.Activities.SendReply> działaniem. Ta właściwość nie może mieć **wartości null**. <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działania są używane razem na serwerze do modelowania wzorca komunikatów żądania/odpowiedzi. Ta właściwość określa, które <xref:System.ServiceModel.Activities.Send> działanie jest sparowane. W projektancie nie można edytować tej właściwości, ponieważ jest ona automatycznie powiązana z <xref:System.ServiceModel.Activities.Send> działaniem, z którego zostało utworzone <xref:System.ServiceModel.Activities.SendReply> działanie. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  Fałsz   |                       Określa komunikat lub zawartość parametru do odebrania. Może to być <xref:System.ServiceModel.Activities.ReceiveMessageContent> działanie lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działanie. Edytuj tę właściwość, klikając przycisk wielokropka obok pola **zawartość** w siatce właściwości lub klikając polecenie **Definiuj...** obok etykiety **zawartość** na powierzchni projektanta działań **odbioru** . Wyświetla okno dialogowe **definicji zawartości** . [!INCLUDE[crabout](../includes/crabout-md.md)] Jak korzystać z tego pola, zobacz temat okno [dialogowe Definicja zawartości](../workflow-designer/content-definition-dialog-box.md) .                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  Fałsz   |            Określa kolekcję <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które inicjują wiele <xref:System.ServiceModel.Activities.CorrelationHandle> obiektów, które konfigurują to <xref:System.ServiceModel.Activities.Receive> działanie w ramach przepływu pracy. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> właściwości w siatce właściwości, aby otworzyć okno dialogowe **Dodawanie inicjatorów korelacji** . [!INCLUDE[crabout](../includes/crabout-md.md)] Korzystając z tego pola, zobacz okno [dialogowe Dodawanie CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) .            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  Fałsz   |                                                                                                                                                                                                                                              Określa nagłówek akcji wiadomości. Jeśli nie jest on jawnie ustawiony, jego wartość domyślna to:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  Fałsz   |                                                                                                                                                                                                                                                                                          Określa, czy wystąpienie przepływu pracy powinno być utrwalane przed wysłaniem komunikatu odpowiedzi. Wartość domyślna to **fałsz**.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Zobacz też
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [odbieranie](../workflow-designer/receive-activity-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)