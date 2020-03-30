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
ms.openlocfilehash: 2067ee92883d0c4ad3003f23032a88f5da3fa710
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395248"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply, projektant szablonów

**SendAndReceiveReply** szablon jest używany do tworzenia pary <xref:System.ServiceModel.Activities.Send> wstępnie <xref:System.ServiceModel.Activities.ReceiveReply> skonfigurowane i działania. Działania są częścią <xref:System.Activities.Statements.Sequence> działania i są skorelowane jako część wzorca wymiany komunikatów żądania/odpowiedzi na kliencie.

## <a name="the-sendandreceivereply-template"></a>Szablon SendAndReceiveReply

Dodawanie **SendAndReceiveReply** szablonu robi trzy <xref:System.ServiceModel.Activities.Send> rzeczy <xref:System.ServiceModel.Activities.ReceiveReply> oprócz tworzenia <xref:System.Activities.Statements.Sequence> i działań w ramach działania:

- Konfiguruje <xref:System.ServiceModel.Activities.Send.OperationName%2A> <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> i właściwości <xref:System.ServiceModel.Activities.Send> działania.

- Wiąże <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> właściwość <xref:System.ServiceModel.Activities.ReceiveReply> działania z <xref:System.ServiceModel.Activities.Send> działaniem.

- Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienną w działaniu nadrzędnym.

### <a name="use-the-sendandreceivereply-template-designer"></a>Użyj projektanta szablonów SendAndReceiveReply

Dostęp do **sendandreceiveReply** projektanta działań w kategorii **Wiadomości** **przybornika**. **SendAndReceiveReply** projektanta działań mogą być przeciągane z **przybornika** i upuszczone na powierzchni Projektanta przepływu pracy, gdzie zwykle są umieszczane działania. Porzucenie projektanta <xref:System.ServiceModel.Activities.Send> działań tworzy działanie, które można skonfigurować za <xref:System.ServiceModel.Activities.ReceiveReply> pomocą **projektanta** działania Wyślij i skorelowane, które można skonfigurować za pomocą projektanta **ReceiveReplyForSend.**

Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Activities.Send> konfigurowania działania za pomocą projektanta **Wyślij,** zobacz [Wysyłanie](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Właściwości ReceiveReply

W poniższej <xref:System.ServiceModel.Activities.ReceiveReply> tabeli przedstawiono właściwości i opisano, jak są one używane w projektancie. Te właściwości mogą być edytowane w siatce właściwości, a niektóre mogą być edytowane na powierzchni Projektanta przepływu pracy.

| Nazwa właściwości | Wymagany | Sposób użycia |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Opcjonalna przyjazna <xref:System.ServiceModel.Activities.ReceiveReply> nazwa działania. Wartość domyślna to ReceiveReplyForSend.<br /><br /> Chociaż użycie wartości nieobejmowej <xref:System.Activities.Activity.DisplayName%2A> dla przyjaznego nie jest ściśle wymagane, najlepiej użyć takiej wartości. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Odwołanie do <xref:System.ServiceModel.Activities.Send> działania w <xref:System.ServiceModel.Activities.ReceiveReply> połączeniu z tym działaniem. Ta właściwość nie może mieć **wartości null**. <xref:System.ServiceModel.Activities.Send>i <xref:System.ServiceModel.Activities.ReceiveReply> działania są używane razem na kliencie do modelowania wzorca wiadomości żądania/odpowiedzi. Ta właściwość <xref:System.ServiceModel.Activities.Send> określa, które działanie jest sparowane. W projektancie nie można edytować tej właściwości, ponieważ jest <xref:System.ServiceModel.Activities.Send> ona automatycznie powiązana z działaniem, z którego utworzono <xref:System.ServiceModel.Activities.ReceiveReply> działanie. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Określa zawartość wiadomości lub parametrów do odebrania. Może to być <xref:System.ServiceModel.Activities.ReceiveMessageContent> działanie lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działanie. Edytuj tę właściwość, klikając przycisk wielokropka obok pola **Zawartość** w siatce właściwości lub klikając przycisk **Definiuj** obok etykiety **Zawartość** na powierzchni projektanta **działań Odbierania.** Oba wyświetlają okno dialogowe **Definicja zawartości.** Aby uzyskać więcej informacji na temat korzystania z tego pola, zobacz [Okno dialogowe Definicja zawartości](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Określa kolekcję <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które <xref:System.ServiceModel.Activities.CorrelationHandle> inicjują <xref:System.ServiceModel.Activities.Receive> wiele obiektów, które konfigurują to działanie w przepływie pracy. Kliknij przycisk wielokropka <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> obok właściwości w siatce właściwości, aby otworzyć okno dialogowe **Dodawanie inicjatorów korelacji.** Aby uzyskać więcej informacji na temat korzystania z tego pola, zobacz [Okno dialogowe Dodawanie correlationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Określa nagłówek akcji wiadomości. Jeśli nie jest jawnie ustawiona, jego wartość domyślnie wynosi:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Zobacz też

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Odbieranie](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Wysyłanie](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)