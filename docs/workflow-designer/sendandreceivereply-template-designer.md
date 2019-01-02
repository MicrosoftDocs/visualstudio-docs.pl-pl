---
title: Projektant przepływu pracy — SendAndReceiveReply, Projektant szablonów
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e1bd37924a818fce26e3f3263aec691be66aee29
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53960488"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply, projektant szablonów

**SendAndReceiveReply** szablon służy do tworzenia pary wstępnie skonfigurowane <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań. Działania są częścią <xref:System.Activities.Statements.Sequence> działania i są skorelowane w ramach wymiany komunikatów żądań/odpowiedzi na komputerze klienckim.

## <a name="the-sendandreceivereply-template"></a>Szablon SendAndReceiveReply

Dodawanie **SendAndReceiveReply** szablonu wykonuje trzy rzeczy, oprócz tworzenia <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań w ramach <xref:System.Activities.Statements.Sequence> działania:

- Konfiguruje <xref:System.ServiceModel.Activities.Send.OperationName%2A> i <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> właściwości <xref:System.ServiceModel.Activities.Send> działania.

- Wiąże <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> właściwość <xref:System.ServiceModel.Activities.ReceiveReply> działanie <xref:System.ServiceModel.Activities.Send> działania.

- Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienna w działanie nadrzędne.

### <a name="use-the-sendandreceivereply-template-designer"></a>Użyj SendAndReceiveReply, Projektant szablonów

Dostęp do **SendAndReceiveReply** projektanta działań w **komunikatów** kategorii **przybornika**. **SendAndReceiveReply** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy wszędzie tam, gdzie działań są zazwyczaj umieszczone. Tworzy porzucenie Projektant działań <xref:System.ServiceModel.Activities.Send> działania, które można skonfigurować za pomocą **wysyłania** projektanta działań i skorelowane <xref:System.ServiceModel.Activities.ReceiveReply> mogą być skonfigurowane z **ReceiveReplyForSend** projektanta.

Aby uzyskać więcej informacji o korzystaniu z **wysyłania** projektanta, aby skonfigurować <xref:System.ServiceModel.Activities.Send> działania, zobacz [wysyłania](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Właściwości ReceiveReply

W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.ReceiveReply> właściwości oraz opisano sposoby ich używania w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich mogą być edytowane na powierzchni projektanta przepływów pracy.


| Nazwa właściwości | Wymagane | Użycie |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Opcjonalna nazwa przyjazna <xref:System.ServiceModel.Activities.ReceiveReply> działania. Wartość domyślna to ReceiveReplyForSend.<br /><br /> Mimo że użycie wartości innych niż domyślne przyjazna <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, zaleca się używać tych wartości. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | Prawda | Odwołanie do <xref:System.ServiceModel.Activities.Send> działania skojarzone z tym <xref:System.ServiceModel.Activities.ReceiveReply> działania. Ta właściwość nie może być **null**. <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działania są używane razem na kliencie do modelowania wzorzec przesyłania komunikatów żądań/odpowiedzi. Ta właściwość określa, która <xref:System.ServiceModel.Activities.Send> Europą działania. W projektancie nie można edytować tej właściwości, ponieważ jest on automatycznie powiązany z <xref:System.ServiceModel.Activities.Send> działań, z którego została utworzona <xref:System.ServiceModel.Activities.ReceiveReply> działania. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Określa zawartość komunikatu lub parametr do odbierania. Może być albo <xref:System.ServiceModel.Activities.ReceiveMessageContent> działania lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działania. Edytuj tę właściwość, klikając przycisk wielokropka obok **zawartości** pola w siatce właściwości lub przez kliknięcie przycisku **Definiuj** przycisk Dalej, aby **zawartości** etykiety na **Receive** powierzchni projektanta działań. Wyświetl oba **definicji zawartości** okna dialogowego. Aby uzyskać więcej informacji na temat używania tego pola, zobacz [definicji zawartości, okno dialogowe](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Określa kolekcję elementów <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które zainicjować wielu <xref:System.ServiceModel.Activities.CorrelationHandle> obiektów, które to skonfigurować <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> właściwości siatki właściwości, aby otworzyć **Dodaj inicjatory korelacji** okno dialogowe. Aby uzyskać więcej informacji o korzystaniu z tego pola, zobacz [Dodawanie CorrelationInitializers, okno dialogowe](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Określa nagłówek akcji w wiadomości. Jeśli nie zostały jawnie jest ustawiona, jej wartość ustawiona wartość domyślna:<br /><br /> <strong>https://tempuri.org/{service kontrakt przestrzeni nazw} / {Nazwa kontraktu usługi} / {nazwa operacji}.</strong> |

## <a name="see-also"></a>Zobacz także

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)