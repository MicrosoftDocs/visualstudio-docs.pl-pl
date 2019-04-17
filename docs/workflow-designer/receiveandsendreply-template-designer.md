---
title: Projektant przepływu pracy — ReceiveAndSendReply, Projektant szablonów
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f6f3f874d00dff8a171a169dca6fe2d94f14fe6
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59648760"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply, projektant szablonów

**ReceiveAndSendReply** szablon służy do tworzenia pary wstępnie skonfigurowane <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań. Działania są częścią <xref:System.Activities.Statements.Sequence> działania i są skorelowane w ramach wymiany komunikatów żądań/odpowiedzi na serwerze.

## <a name="the-receiveandsendreply-template"></a>Szablon ReceiveAndSendReply

Dodawanie **ReceiveAndSendReply** szablonu wykonuje trzy rzeczy, oprócz tworzenia <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań z <xref:System.Activities.Statements.Sequence> działania:

- Konfiguruje <xref:System.ServiceModel.Activities.Receive.OperationName%2A> i <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> właściwości <xref:System.ServiceModel.Activities.Receive> działania.

- Wiąże <xref:System.ServiceModel.Activities.SendReply.Request%2A> właściwość <xref:System.ServiceModel.Activities.Receive> działanie <xref:System.ServiceModel.Activities.Send> działania.

- Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienna w działanie nadrzędne.

### <a name="use-the-receiveandsendreply-template-designer"></a>Używany jest Projektant szablonów ReceiveAndSendReply

Dostęp do **ReceiveAndSendReply** projektanta działań w **komunikatów** kategorii **przybornika**. **ReceiveAndSendReply** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy wszędzie tam, gdzie działań są zazwyczaj umieszczone. Tworzy porzucenie Projektant działań <xref:System.ServiceModel.Activities.Receive> działania, które można skonfigurować za pomocą **wysyłania** projektanta działań i skorelowane <xref:System.ServiceModel.Activities.SendReply> , można skonfigurować za pomocą projektanta SendReplyToReceive.

Aby uzyskać więcej informacji o korzystaniu z **Receive** projektanta, aby skonfigurować <xref:System.ServiceModel.Activities.Receive> działania, zobacz [wyświetlony Projektant działań](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Właściwości SendReply

W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.SendReply> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich mogą być edytowane na powierzchni projektanta przepływów pracy.

| Nazwa właściwości | Wymagane | Użycie |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Opcjonalna nazwa przyjazna <xref:System.ServiceModel.Activities.SendReply> działania. Wartość domyślna to SendReplyToReceive.<br /><br /> Mimo że użycie wartości innych niż domyślne przyjazna <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, zaleca się używać tych wartości. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | Prawda | Odwołanie do <xref:System.ServiceModel.Activities.Receive> działania skojarzone z tym <xref:System.ServiceModel.Activities.SendReply> działania. Ta właściwość nie może być **null**. <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działania są używane wspólnie na serwerze do modelowania wzorzec przesyłania komunikatów żądań/odpowiedzi. Ta właściwość określa, która <xref:System.ServiceModel.Activities.Send> Europą działania. W projektancie nie można edytować tej właściwości, ponieważ jest on automatycznie powiązany z <xref:System.ServiceModel.Activities.Send> działań, z którego została utworzona <xref:System.ServiceModel.Activities.SendReply> działania. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Określa zawartość komunikatu lub parametr do odbierania. Może być albo <xref:System.ServiceModel.Activities.ReceiveMessageContent> działania lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działania. Edytuj tę właściwość, klikając przycisk wielokropka obok pozycji **zawartości** pola w siatce właściwości lub przez kliknięcie przycisku **Definiuj** przycisk Dalej, aby **zawartości** etykiety na  **Odbieranie** powierzchni projektanta działań. Wyświetl oba **definicji zawartości** okna dialogowego. Aby uzyskać więcej informacji na temat używania tego pola, zobacz [definicji zawartości, okno dialogowe](../workflow-designer/content-definition-dialog-box.md) tematu. |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Określa kolekcję elementów <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które zainicjować wielu <xref:System.ServiceModel.Activities.CorrelationHandle> obiektów, które to skonfigurować <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> właściwości siatki właściwości, aby otworzyć **Dodaj inicjatory korelacji** okno dialogowe. Aby uzyskać więcej informacji o korzystaniu z tego pola, zobacz [Dodawanie CorrelationInitializers, okno dialogowe](../workflow-designer/add-correlationinitializers-dialog-box.md) tematu. |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | Określa nagłówek akcji w wiadomości. Jeśli nie zostały jawnie jest ustawiona, jej wartość ustawiona wartość domyślna:<br /><br /> <strong>https://tempuri.org/{service kontrakt przestrzeni nazw} / {Nazwa kontraktu usługi} / {nazwa operacji}</strong> |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Określa, czy wystąpienie przepływu pracy powinny zostać utrwalone przed wysłaniem komunikat odpowiedzi. Wartość domyślna to **false**. |

## <a name="see-also"></a>Zobacz także

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)