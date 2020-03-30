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
ms.openlocfilehash: 042032efe745a9cb38bbf4e362cb5ad8440129ba
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395301"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply, projektant szablonów

**Szablon ReceiveAndSendReply** służy do tworzenia pary wstępnie <xref:System.ServiceModel.Activities.Receive> skonfigurowanych i <xref:System.ServiceModel.Activities.SendReply> działań. Działania są częścią <xref:System.Activities.Statements.Sequence> działania i są skorelowane jako część wzorca wymiany komunikatów żądania/odpowiedzi na serwerze.

## <a name="the-receiveandsendreply-template"></a>Szablon ReceiveAndSendReply

Dodawanie **ReceiveAndSendReply** szablonu robi trzy <xref:System.ServiceModel.Activities.Receive> rzeczy <xref:System.ServiceModel.Activities.SendReply> oprócz tworzenia <xref:System.Activities.Statements.Sequence> i działań z działaniem:

- Konfiguruje <xref:System.ServiceModel.Activities.Receive.OperationName%2A> <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> i właściwości <xref:System.ServiceModel.Activities.Receive> działania.

- Wiąże <xref:System.ServiceModel.Activities.SendReply.Request%2A> właściwość <xref:System.ServiceModel.Activities.Receive> działania z <xref:System.ServiceModel.Activities.Send> działaniem.

- Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienną w działaniu nadrzędnym.

### <a name="use-the-receiveandsendreply-template-designer"></a>Użyj projektanta szablonów ReceiveAndSendReply

Dostęp do **receiveandsendReply** projektanta działań w **kategorii Wiadomości** **przybornika**. **ReceiveAndSendReply** projektanta działań mogą być przeciągane z **przybornika** i upuszczone na powierzchni Projektanta przepływu pracy, gdzie zwykle są umieszczane działania. Porzucenie projektanta <xref:System.ServiceModel.Activities.Receive> działań tworzy działanie, które można skonfigurować za <xref:System.ServiceModel.Activities.SendReply> pomocą **projektanta** działania Wyślij i skorelowane, które mogą być skonfigurowane za pomocą SendReplyToReceive projektanta.

Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Activities.Receive> konfigurowania działania za pomocą projektanta **Odbierania,** zobacz [Odbieranie Projektanta działań](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Właściwości SendReply

W poniższej <xref:System.ServiceModel.Activities.SendReply> tabeli przedstawiono właściwości i opisano, jak są one używane w projektancie. Te właściwości mogą być edytowane w siatce właściwości, a niektóre mogą być edytowane na powierzchni Projektanta przepływu pracy.

| Nazwa właściwości | Wymagany | Sposób użycia |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Opcjonalna przyjazna <xref:System.ServiceModel.Activities.SendReply> nazwa działania. Wartość domyślna to SendReplyToReceive.<br /><br /> Chociaż użycie wartości nieobejmowej <xref:System.Activities.Activity.DisplayName%2A> dla przyjaznego nie jest ściśle wymagane, najlepiej użyć takiej wartości. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | Odwołanie do <xref:System.ServiceModel.Activities.Receive> działania w <xref:System.ServiceModel.Activities.SendReply> połączeniu z tym działaniem. Ta właściwość nie może mieć **wartości null**. <xref:System.ServiceModel.Activities.Receive>i <xref:System.ServiceModel.Activities.SendReply> działania są używane razem na serwerze do modelowania wzorca wiadomości żądania/odpowiedzi. Ta właściwość <xref:System.ServiceModel.Activities.Send> określa, które działanie jest sparowane. W projektancie nie można edytować tej właściwości, ponieważ jest <xref:System.ServiceModel.Activities.Send> ona automatycznie powiązana z działaniem, z którego utworzono <xref:System.ServiceModel.Activities.SendReply> działanie. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Określa zawartość wiadomości lub parametrów do odebrania. Może to być <xref:System.ServiceModel.Activities.ReceiveMessageContent> działanie lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działanie. Edytuj tę właściwość, klikając przycisk wielokropka obok pola **Zawartość** w siatce właściwości lub klikając przycisk **Definiuj** obok etykiety **Zawartość** na powierzchni projektanta działań **Odbierania.** Oba wyświetlają okno dialogowe **Definicja zawartości.** Aby uzyskać więcej informacji na temat używania tego pola, zobacz temat [okna dialogowego Definicja zawartości.](../workflow-designer/content-definition-dialog-box.md) |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Określa kolekcję <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które <xref:System.ServiceModel.Activities.CorrelationHandle> inicjują <xref:System.ServiceModel.Activities.Receive> wiele obiektów, które konfigurują to działanie w przepływie pracy. Kliknij przycisk wielokropka <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> obok właściwości w siatce właściwości, aby otworzyć okno dialogowe **Dodawanie inicjatorów korelacji.** Aby uzyskać więcej informacji na temat korzystania z tego pola, zobacz [temat Okno dialogowe Dodawanie correlationInitializers.](../workflow-designer/add-correlationinitializers-dialog-box.md) |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | Określa nagłówek akcji wiadomości. Jeśli nie jest jawnie ustawiona, jego wartość domyślnie wynosi:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Określa, czy wystąpienie przepływu pracy ma być zachowywane przed wysłaniem wiadomości odpowiedzi. Wartość domyślna to **fałsz**. |

## <a name="see-also"></a>Zobacz też

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Odbieranie](../workflow-designer/receive-activity-designer.md)
- [Wysyłanie](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)