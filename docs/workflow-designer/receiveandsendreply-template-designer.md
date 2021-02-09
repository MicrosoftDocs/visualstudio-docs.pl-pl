---
title: ReceiveAndSendReply, projektant szablonów
description: Dowiedz się, jak używać szablonu ReceiveAndSendReply w Projektant przepływu pracy, aby utworzyć parę wstępnie skonfigurowanych działań dotyczących odbierania i działania SendReply.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6bc86aed1e135f369d771a9ac47513c4eb28ce25
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926537"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply, projektant szablonów

Szablon **ReceiveAndSendReply** służy do tworzenia pary wstępnie skonfigurowanych <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań. Działania są częścią <xref:System.Activities.Statements.Sequence> działania i są skorelowane jako część wzorca wymiany komunikatów żądania/odpowiedzi na serwerze.

## <a name="the-receiveandsendreply-template"></a>Szablon ReceiveAndSendReply

Dodanie szablonu **ReceiveAndSendReply** powoduje trzy rzeczy oprócz tworzenia <xref:System.ServiceModel.Activities.Receive> działań i działania <xref:System.ServiceModel.Activities.SendReply> z <xref:System.Activities.Statements.Sequence> działaniem:

- Konfiguruje <xref:System.ServiceModel.Activities.Receive.OperationName%2A> <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> właściwości i <xref:System.ServiceModel.Activities.Receive> działania.

- Wiąże <xref:System.ServiceModel.Activities.SendReply.Request%2A> Właściwość <xref:System.ServiceModel.Activities.Receive> działania z <xref:System.ServiceModel.Activities.Send> działaniem.

- Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienną w działaniu nadrzędnym.

### <a name="use-the-receiveandsendreply-template-designer"></a>Korzystanie z projektanta szablonów ReceiveAndSendReply

Dostęp do projektanta działań **ReceiveAndSendReply** w kategorii **Obsługa wiadomości** w **przyborniku**. Projektanta działań **ReceiveAndSendReply** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam gdzie działania są zwykle umieszczane. Porzucenie projektanta działań powoduje utworzenie <xref:System.ServiceModel.Activities.Receive> działania, które można skonfigurować za pomocą projektanta działania **wysyłania** , a także skorelowane <xref:System.ServiceModel.Activities.SendReply> , które można skonfigurować za pomocą projektanta SendReplyToReceive.

Aby uzyskać więcej informacji o korzystaniu z projektanta **odbioru** w celu skonfigurowania <xref:System.ServiceModel.Activities.Receive> działania, zobacz [odbieranie programu Activity Designer](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Właściwości działania SendReply

W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.SendReply> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre można edytować na powierzchni Projektant przepływu pracy.

| Nazwa właściwości | Wymagany | Użycie |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Fałsz | Opcjonalna przyjazna nazwa <xref:System.ServiceModel.Activities.SendReply> działania. Wartość domyślna to SendReplyToReceive.<br /><br /> Chociaż użycie wartości innej niż domyślna dla elementu friendly <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie takiej wartości. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | Prawda | Odwołanie do <xref:System.ServiceModel.Activities.Receive> działania sparowanego z tym <xref:System.ServiceModel.Activities.SendReply> działaniem. Ta właściwość nie może mieć **wartości null**. <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działania są używane razem na serwerze do modelowania wzorca komunikatów żądania/odpowiedzi. Ta właściwość określa, które <xref:System.ServiceModel.Activities.Send> działanie jest sparowane. W projektancie nie można edytować tej właściwości, ponieważ jest ona automatycznie powiązana z <xref:System.ServiceModel.Activities.Send> działaniem, z którego zostało utworzone <xref:System.ServiceModel.Activities.SendReply> działanie. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | Fałsz | Określa komunikat lub zawartość parametru do odebrania. Może to być <xref:System.ServiceModel.Activities.ReceiveMessageContent> działanie lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działanie. Edytuj tę właściwość, klikając przycisk wielokropka obok pola **zawartość** w siatce właściwości lub klikając przycisk **Definiuj** obok etykiety **zawartość** na powierzchni **projektanta działań.** Wyświetla okno dialogowe **definicji zawartości** . Aby uzyskać więcej informacji na temat korzystania z tego pola, zobacz [okno dialogowe Definicja zawartości](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | Fałsz | Określa kolekcję <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które inicjują wiele <xref:System.ServiceModel.Activities.CorrelationHandle> obiektów, które konfigurują to <xref:System.ServiceModel.Activities.Receive> działanie w ramach przepływu pracy. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> właściwości w siatce właściwości, aby otworzyć okno dialogowe **Dodawanie inicjatorów korelacji** . Aby uzyskać więcej informacji na temat korzystania z tego pola, zobacz [okno dialogowe Dodawanie CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | Fałsz | Określa nagłówek akcji wiadomości. Jeśli nie jest on jawnie ustawiony, jego wartość domyślna to:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | Fałsz | Określa, czy wystąpienie przepływu pracy powinno być utrwalane przed wysłaniem komunikatu odpowiedzi. Wartość domyślna to **fałsz**. |

## <a name="see-also"></a>Zobacz też

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Odbieranie](../workflow-designer/receive-activity-designer.md)
- [Wysyłanie](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)