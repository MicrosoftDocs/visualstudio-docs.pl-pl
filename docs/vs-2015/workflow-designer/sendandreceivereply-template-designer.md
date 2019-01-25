---
title: SendAndReceiveReply, Projektant szablonów | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5c978c4be142283866ce140a1f0870cd654a06dd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804945"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply, projektant szablonów
**SendAndReceiveReply** szablon służy do tworzenia pary wstępnie skonfigurowane <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań w ramach <xref:System.Activities.Statements.Sequence> działanie, które są skorelowane w ramach wymiany komunikatów żądań/odpowiedzi wzorzec na komputerze klienckim.  

## <a name="the-sendandreceivereply-template"></a>Szablon SendAndReceiveReply  
 Dodawanie **SendAndReceiveReply** szablonu wykonuje trzy rzeczy, oprócz tworzenia <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań w ramach <xref:System.Activities.Statements.Sequence> działania:  

1.  Konfiguruje <xref:System.ServiceModel.Activities.Send.OperationName%2A>, <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> właściwości <xref:System.ServiceModel.Activities.Send> działania.  

2.  Wiąże <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> właściwość <xref:System.ServiceModel.Activities.ReceiveReply> działanie <xref:System.ServiceModel.Activities.Send> działania.  

3.  Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienna w działanie nadrzędne.  

### <a name="using-the-sendandreceivereply-template-designer"></a>Za pomocą SendAndReceiveReply, Projektant szablonów  
 **SendAndReceiveReply** projektanta działań można znaleźć w **komunikatów** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**  karcie [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać **narzędzi** z **widoku** menu lub klawiszy CTRL + ALT + X.)  

 **SendAndReceiveReply** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zazwyczaj umieszczone. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Send> działania, które można skonfigurować za pomocą **wysyłania** projektanta działań i skorelowane <xref:System.ServiceModel.Activities.ReceiveReply> mogą być skonfigurowane z **ReceiveReplyForSend** projektanta.  

 [!INCLUDE[crabout](../includes/crabout-md.md)] za pomocą **wysyłania** projektanta, aby skonfigurować <xref:System.ServiceModel.Activities.Send> działania, zobacz [wysyłania](../workflow-designer/send-activity-designer.md) tematu.  

 [!INCLUDE[crabout](../includes/crabout-md.md)] za pomocą **ReceiveReplyForSend** projektanta, aby skonfigurować <xref:System.ServiceModel.Activities.ReceiveReply> działania, zobacz następującą sekcję.  

### <a name="properties-of-receivereply"></a>Właściwości ReceiveReply  
 W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.ReceiveReply> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości i niektóre mogą być edytowane [!INCLUDE[wfd2](../includes/wfd2-md.md)]powierzchni projektowej.  


|                                 Nazwa właściwości                                 | Wymagane |                                                                                                                                                                                                                                                                                                                                                        Użycie                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            Opcjonalna nazwa przyjazna <xref:System.ServiceModel.Activities.ReceiveReply> działania. Wartość domyślna to ReceiveReplyForSend.<br /><br /> Mimo że użycie wartości innych niż domyślne przyjazna <xref:System.Activities.Activity.DisplayName%2A> nie jest bezwzględnie konieczne jest najlepszym rozwiązaniem jest użycie tych wartości.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   Prawda   | Odwołanie do <xref:System.ServiceModel.Activities.Send> działania skojarzone z tym <xref:System.ServiceModel.Activities.ReceiveReply> działania. Ta właściwość nie może być **null**. <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działania są używane razem na kliencie do modelowania wzorzec przesyłania komunikatów żądań/odpowiedzi. Ta właściwość określa, która <xref:System.ServiceModel.Activities.Send> Europą działania. W projektancie nie można edytować tej właściwości, ponieważ jest on automatycznie powiązany z <xref:System.ServiceModel.Activities.Send> działań, z którego została utworzona <xref:System.ServiceModel.Activities.ReceiveReply> działania. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        Określa zawartość komunikatu lub parametr do odbierania. Może być albo <xref:System.ServiceModel.Activities.ReceiveMessageContent> działania lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działania. Edytuj tę właściwość, klikając przycisk wielokropka obok **zawartości** w siatce właściwości lub klikając **Definiuj...** przycisk obok **zawartości** etykiety na **Receive** powierzchni projektanta działań. Wyświetl oba **definicji zawartości** okna dialogowego. [!INCLUDE[crabout](../includes/crabout-md.md)] Użyj tego pola, zobacz [definicji zawartości, okno dialogowe](../workflow-designer/content-definition-dialog-box.md) tematu.                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              Określa kolekcję elementów <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które zainicjować wielu <xref:System.ServiceModel.Activities.CorrelationHandle> obiektów, które to skonfigurować <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> właściwości siatki właściwości, aby otworzyć **Dodaj inicjatory korelacji** okno dialogowe. [!INCLUDE[crabout](../includes/crabout-md.md)] za pomocą tego pola, zobacz [Dodawanie CorrelationInitializers, okno dialogowe](../workflow-designer/add-correlationinitializers-dialog-box.md) tematu.               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               Określa nagłówek akcji w wiadomości. Jeśli nie jest jawnie ustawiona wartość ustawiona wartość domyślna:<br /><br /> <strong>https://tempuri.org/{service kontrakt przestrzeni nazw} / {Nazwa kontraktu usługi} / {nazwa operacji}.</strong>                                                                                                                                                                                                                                               |

## <a name="see-also"></a>Zobacz też  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Odbieranie](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Wyślij](../workflow-designer/send-activity-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)