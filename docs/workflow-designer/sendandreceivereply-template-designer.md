---
title: Projektant przepływu pracy — Projektant szablonów SendAndReceiveReply
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7c552e8bb94ed9035f25bdd40b7944458e61a11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649955"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply, projektant szablonów

Szablon **SendAndReceiveReply** służy do tworzenia pary wstępnie skonfigurowanych działań <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply>. Działania są częścią działania <xref:System.Activities.Statements.Sequence> i są skorelowane jako część wzorca wymiany komunikatów żądania/odpowiedzi na kliencie.

## <a name="the-sendandreceivereply-template"></a>Szablon SendAndReceiveReply

Dodanie szablonu **SendAndReceiveReply** powoduje trzy rzeczy oprócz tworzenia <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań w ramach <xref:System.Activities.Statements.Sequence> działania:

- Konfiguruje <xref:System.ServiceModel.Activities.Send.OperationName%2A> i <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> właściwości działania <xref:System.ServiceModel.Activities.Send>.

- Wiąże Właściwość <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> działania <xref:System.ServiceModel.Activities.ReceiveReply> z działaniem <xref:System.ServiceModel.Activities.Send>.

- Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienną w działaniu nadrzędnym.

### <a name="use-the-sendandreceivereply-template-designer"></a>Korzystanie z projektanta szablonów SendAndReceiveReply

Dostęp do projektanta działań **SendAndReceiveReply** w kategorii **Obsługa wiadomości** w **przyborniku**. Projektanta działań **SendAndReceiveReply** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam gdzie działania są zwykle umieszczane. Porzucenie projektanta działań powoduje utworzenie działania <xref:System.ServiceModel.Activities.Send>, które można skonfigurować za pomocą projektanta działania **wysyłania** i skorelowane <xref:System.ServiceModel.Activities.ReceiveReply>, które można skonfigurować za pomocą projektanta **ReceiveReplyForSend** .

Aby uzyskać więcej informacji o używaniu projektanta **wysyłania** do konfigurowania działania <xref:System.ServiceModel.Activities.Send>, zobacz [send](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Właściwości ReceiveReply

W poniższej tabeli przedstawiono właściwości <xref:System.ServiceModel.Activities.ReceiveReply> i opisano, jak są one używane w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre można edytować na powierzchni Projektant przepływu pracy.

| Nazwa właściwości | Wymagane | Użycie |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Opcjonalna przyjazna nazwa działania <xref:System.ServiceModel.Activities.ReceiveReply>. Wartość domyślna to ReceiveReplyForSend.<br /><br /> Chociaż użycie wartości innej niż domyślna dla przyjaznej <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepiej użyć takiej wartości. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | Oznacza | Odwołanie do działania <xref:System.ServiceModel.Activities.Send> sparowane z tym działaniem <xref:System.ServiceModel.Activities.ReceiveReply>. Ta właściwość nie może mieć **wartości null**. działania <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> są używane razem z klientem w celu modelowania wzorca komunikatów żądania/odpowiedzi. Ta właściwość określa, które <xref:System.ServiceModel.Activities.Send> działania są sparowane. W projektancie nie można edytować tej właściwości, ponieważ jest ona automatycznie powiązana z działaniem <xref:System.ServiceModel.Activities.Send>, z którego zostało utworzone działanie <xref:System.ServiceModel.Activities.ReceiveReply>. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Określa komunikat lub zawartość parametru do odebrania. Może to być działanie <xref:System.ServiceModel.Activities.ReceiveMessageContent> lub <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Edytuj tę właściwość, klikając przycisk wielokropka obok pola **zawartość** w siatce właściwości lub klikając przycisk **Definiuj** obok etykiety **zawartość** na powierzchni **projektanta działań.** Wyświetla okno dialogowe **definicji zawartości** . Aby uzyskać więcej informacji na temat korzystania z tego pola, zobacz [okno dialogowe Definicja zawartości](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Określa kolekcję obiektów <xref:System.ServiceModel.Activities.CorrelationInitializer>, które inicjują wiele obiektów <xref:System.ServiceModel.Activities.CorrelationHandle>, które konfigurują to działanie <xref:System.ServiceModel.Activities.Receive> w ramach przepływu pracy. Kliknij przycisk wielokropka obok właściwości <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> w siatce właściwości, aby otworzyć okno dialogowe **Dodawanie inicjatorów korelacji** . Aby uzyskać więcej informacji na temat korzystania z tego pola, zobacz [Dodawanie CorrelationInitializers dialogowego](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Określa nagłówek akcji wiadomości. Jeśli nie jest on jawnie ustawiony, jego wartość domyślna to:<br /><br /> <strong>https://tempuri.org/{service obszar nazw kontraktu} Nazwa kontraktu/{Service}/{Operation nazwa}.</strong> |

## <a name="see-also"></a>Zobacz także

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)