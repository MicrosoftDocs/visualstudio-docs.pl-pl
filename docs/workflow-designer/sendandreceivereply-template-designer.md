---
title: SendAndReceiveReply, projektant szablonów
description: Dowiedz się, w jaki sposób można użyć szablonu SendAndReceiveReply w Projektant przepływu pracy, aby utworzyć parę wstępnie skonfigurowanych działań wysyłania i ReceiveReply.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91885371f72c5756ddc026111404f091a2cccf08
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993266"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply, projektant szablonów

Szablon **SendAndReceiveReply** służy do tworzenia pary wstępnie skonfigurowanych <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań. Działania są częścią <xref:System.Activities.Statements.Sequence> działania i są skorelowane jako część wzorca wymiany komunikatów żądania/odpowiedzi na kliencie.

## <a name="the-sendandreceivereply-template"></a>Szablon SendAndReceiveReply

Dodanie szablonu **SendAndReceiveReply** powoduje trzy rzeczy oprócz tworzenia <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> działań i w ramach <xref:System.Activities.Statements.Sequence> działania:

- Konfiguruje <xref:System.ServiceModel.Activities.Send.OperationName%2A> <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> właściwości i <xref:System.ServiceModel.Activities.Send> działania.

- Wiąże <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> Właściwość <xref:System.ServiceModel.Activities.ReceiveReply> działania z <xref:System.ServiceModel.Activities.Send> działaniem.

- Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienną w działaniu nadrzędnym.

### <a name="use-the-sendandreceivereply-template-designer"></a>Korzystanie z projektanta szablonów SendAndReceiveReply

Dostęp do projektanta działań **SendAndReceiveReply** w kategorii **Obsługa wiadomości** w **przyborniku**. Projektanta działań **SendAndReceiveReply** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam gdzie działania są zwykle umieszczane. Porzucenie projektanta działań powoduje utworzenie <xref:System.ServiceModel.Activities.Send> działania, które można skonfigurować za pomocą projektanta działania **wysyłania** , a także skorelowane <xref:System.ServiceModel.Activities.ReceiveReply> , które można skonfigurować za pomocą projektanta **ReceiveReplyForSend** .

Aby uzyskać więcej informacji o używaniu projektanta **wysyłania** do konfigurowania <xref:System.ServiceModel.Activities.Send> działania, zobacz [send](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Właściwości ReceiveReply

W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.ReceiveReply> właściwości i opisano, jak są one używane w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre można edytować na powierzchni Projektant przepływu pracy.

| Nazwa właściwości | Wymagany | Użycie |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Fałsz | Opcjonalna przyjazna nazwa <xref:System.ServiceModel.Activities.ReceiveReply> działania. Wartość domyślna to ReceiveReplyForSend.<br /><br /> Chociaż użycie wartości innej niż domyślna dla elementu friendly <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie takiej wartości. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | Prawda | Odwołanie do <xref:System.ServiceModel.Activities.Send> działania sparowanego z tym <xref:System.ServiceModel.Activities.ReceiveReply> działaniem. Ta właściwość nie może mieć **wartości null**. <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działania są używane razem z klientem w celu modelowania wzorca komunikatów żądania/odpowiedzi. Ta właściwość określa, które <xref:System.ServiceModel.Activities.Send> działanie jest sparowane. W projektancie nie można edytować tej właściwości, ponieważ jest ona automatycznie powiązana z <xref:System.ServiceModel.Activities.Send> działaniem, z którego zostało utworzone <xref:System.ServiceModel.Activities.ReceiveReply> działanie. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | Fałsz | Określa komunikat lub zawartość parametru do odebrania. Może to być <xref:System.ServiceModel.Activities.ReceiveMessageContent> działanie lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działanie. Edytuj tę właściwość, klikając przycisk wielokropka obok pola **zawartość** w siatce właściwości lub klikając przycisk **Definiuj** obok etykiety **zawartość** na powierzchni **projektanta działań.** Wyświetla okno dialogowe **definicji zawartości** . Aby uzyskać więcej informacji na temat korzystania z tego pola, zobacz [okno dialogowe Definicja zawartości](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | Fałsz | Określa kolekcję <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które inicjują wiele <xref:System.ServiceModel.Activities.CorrelationHandle> obiektów, które konfigurują to <xref:System.ServiceModel.Activities.Receive> działanie w ramach przepływu pracy. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> właściwości w siatce właściwości, aby otworzyć okno dialogowe **Dodawanie inicjatorów korelacji** . Aby uzyskać więcej informacji na temat korzystania z tego pola, zobacz [Dodawanie CorrelationInitializers dialogowego](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | Fałsz | Określa nagłówek akcji wiadomości. Jeśli nie jest on jawnie ustawiony, jego wartość domyślna to:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Zobacz też

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Odbieranie](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Wysyłanie](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)