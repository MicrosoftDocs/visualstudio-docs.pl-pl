---
title: Projektant przepływu pracy — Projektant szablonów ReceiveAndSendReply
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a816013f4eceb390a16e76a06814043aa0adaeb8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650021"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply, projektant szablonów

Szablon **ReceiveAndSendReply** służy do tworzenia pary wstępnie skonfigurowanych działań <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply>. Działania są częścią działania <xref:System.Activities.Statements.Sequence> i są skorelowane jako część wzorca wymiany komunikatów żądania/odpowiedzi na serwerze.

## <a name="the-receiveandsendreply-template"></a>Szablon ReceiveAndSendReply

Dodanie szablonu **ReceiveAndSendReply** powoduje trzy rzeczy oprócz tworzenia działań <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> z działaniami <xref:System.Activities.Statements.Sequence>:

- Konfiguruje <xref:System.ServiceModel.Activities.Receive.OperationName%2A> i <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> właściwości działania <xref:System.ServiceModel.Activities.Receive>.

- Wiąże Właściwość <xref:System.ServiceModel.Activities.SendReply.Request%2A> działania <xref:System.ServiceModel.Activities.Receive> z działaniem <xref:System.ServiceModel.Activities.Send>.

- Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienną w działaniu nadrzędnym.

### <a name="use-the-receiveandsendreply-template-designer"></a>Korzystanie z projektanta szablonów ReceiveAndSendReply

Dostęp do projektanta działań **ReceiveAndSendReply** w kategorii **Obsługa wiadomości** w **przyborniku**. Projektanta działań **ReceiveAndSendReply** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam gdzie działania są zwykle umieszczane. Porzucenie projektanta działań powoduje utworzenie działania <xref:System.ServiceModel.Activities.Receive>, które można skonfigurować za pomocą projektanta działania **wysyłania** i skorelowane <xref:System.ServiceModel.Activities.SendReply>, które można skonfigurować za pomocą projektanta SendReplyToReceive.

Aby uzyskać więcej informacji o korzystaniu z projektanta **odbioru** w celu skonfigurowania działania <xref:System.ServiceModel.Activities.Receive>, zobacz [odbieranie działania projektanta](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Właściwości działania SendReply

W poniższej tabeli przedstawiono właściwości <xref:System.ServiceModel.Activities.SendReply> i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre można edytować na powierzchni Projektant przepływu pracy.

| Nazwa właściwości | Wymagane | Użycie |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Opcjonalna przyjazna nazwa działania <xref:System.ServiceModel.Activities.SendReply>. Wartość domyślna to SendReplyToReceive.<br /><br /> Chociaż użycie wartości innej niż domyślna dla przyjaznej <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepiej użyć takiej wartości. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | Oznacza | Odwołanie do działania <xref:System.ServiceModel.Activities.Receive> sparowane z tym działaniem <xref:System.ServiceModel.Activities.SendReply>. Ta właściwość nie może mieć **wartości null**. działania <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> są używane razem na serwerze do modelowania wzorca komunikatów żądania/odpowiedzi. Ta właściwość określa, które <xref:System.ServiceModel.Activities.Send> działania są sparowane. W projektancie nie można edytować tej właściwości, ponieważ jest ona automatycznie powiązana z działaniem <xref:System.ServiceModel.Activities.Send>, z którego zostało utworzone działanie <xref:System.ServiceModel.Activities.SendReply>. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Określa komunikat lub zawartość parametru do odebrania. Może to być działanie <xref:System.ServiceModel.Activities.ReceiveMessageContent> lub <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Edytuj tę właściwość, klikając przycisk wielokropka obok pola **zawartość** w siatce właściwości lub klikając przycisk **Definiuj** obok etykiety **zawartość** na powierzchni **projektanta działań.** Wyświetla okno dialogowe **definicji zawartości** . Aby uzyskać więcej informacji na temat korzystania z tego pola, zobacz [okno dialogowe Definicja zawartości](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Określa kolekcję obiektów <xref:System.ServiceModel.Activities.CorrelationInitializer>, które inicjują wiele obiektów <xref:System.ServiceModel.Activities.CorrelationHandle>, które konfigurują to działanie <xref:System.ServiceModel.Activities.Receive> w ramach przepływu pracy. Kliknij przycisk wielokropka obok właściwości <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> w siatce właściwości, aby otworzyć okno dialogowe **Dodawanie inicjatorów korelacji** . Aby uzyskać więcej informacji na temat korzystania z tego pola, zobacz [okno dialogowe Dodawanie CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | Określa nagłówek akcji wiadomości. Jeśli nie jest on jawnie ustawiony, jego wartość domyślna to:<br /><br /> <strong>Przestrzeń nazw kontraktu https://tempuri.org/{service }/{Service Nazwa kontraktu}/{Operation nazwa}</strong> |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Określa, czy wystąpienie przepływu pracy powinno być utrwalane przed wysłaniem komunikatu odpowiedzi. Wartość domyślna to **false**. |

## <a name="see-also"></a>Zobacz także

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)