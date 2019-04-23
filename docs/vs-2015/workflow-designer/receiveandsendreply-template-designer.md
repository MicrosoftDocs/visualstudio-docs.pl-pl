---
title: ReceiveAndSendReply, Projektant szablonów | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9de3e8446250829d431dcbf33b14effd607ab545
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60075775"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply, projektant szablonów
**ReceiveAndSendReply** szablon służy do tworzenia pary wstępnie skonfigurowane <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań w ramach <xref:System.Activities.Statements.Sequence> działanie, które są skorelowane w ramach wymiany komunikatów żądań/odpowiedzi wzorzec na serwerze.  

## <a name="the-receiveandsendreply-template"></a>Szablon ReceiveAndSendReply  
 Dodawanie **ReceiveAndSendReply** szablonu wykonuje trzy rzeczy, oprócz tworzenia <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań z <xref:System.Activities.Statements.Sequence> działania:  

1. Konfiguruje <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> właściwości <xref:System.ServiceModel.Activities.Receive> działania.  

2. Wiąże <xref:System.ServiceModel.Activities.SendReply.Request%2A> właściwość <xref:System.ServiceModel.Activities.Receive> działanie <xref:System.ServiceModel.Activities.Send> działania.  

3. Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienna w działanie nadrzędne.  

### <a name="using-the-receiveandsendreply-template-designer"></a>Za pomocą ReceiveAndSendReply, Projektant szablonów  
 **ReceiveAndSendReply** projektanta działań można znaleźć w **komunikatów** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**  karcie [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać **narzędzi** z **widoku** menu lub klawiszy CTRL + ALT + X.)  

 **ReceiveAndSendReply** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zazwyczaj umieszczone. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Receive> działania, które można skonfigurować za pomocą **wysyłania** projektanta działań i skorelowane <xref:System.ServiceModel.Activities.SendReply> , można skonfigurować za pomocą projektanta SendReplyToReceive.  

 [!INCLUDE[crabout](../includes/crabout-md.md)] za pomocą **Receive** projektanta, aby skonfigurować <xref:System.ServiceModel.Activities.Receive> działania, zobacz [Receive](../workflow-designer/receive-activity-designer.md) tematu.  

 [!INCLUDE[crabout](../includes/crabout-md.md)] za pomocą **SendReplyToReceive** projektanta, aby skonfigurować <xref:System.ServiceModel.Activities.SendReply> działania, zobacz następującą sekcję.  

### <a name="properties-of-sendreply"></a>Właściwości SendReply  
 W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.SendReply> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości i niektóre mogą być edytowane [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni projektowej.  

|                               Nazwa właściwości                                | Wymagane |                                                                                                                                                                                                                                                                                                                                                      Użycie                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  False   |                                                                                                                                                                                            Opcjonalna nazwa przyjazna <xref:System.ServiceModel.Activities.SendReply> działania. Wartość domyślna to SendReplyToReceive.<br /><br /> Mimo że użycie wartości innych niż domyślne przyjazna <xref:System.Activities.Activity.DisplayName%2A> nie jest bezwzględnie konieczne jest najlepszym rozwiązaniem jest użycie tych wartości.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   Prawda   | Odwołanie do <xref:System.ServiceModel.Activities.Receive> działania skojarzone z tym <xref:System.ServiceModel.Activities.SendReply> działania. Ta właściwość nie może być **null**. <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działania są używane wspólnie na serwerze do modelowania wzorzec przesyłania komunikatów żądań/odpowiedzi. Ta właściwość określa, która <xref:System.ServiceModel.Activities.Send> Europą działania. W projektancie nie można edytować tej właściwości, ponieważ jest on automatycznie powiązany z <xref:System.ServiceModel.Activities.Send> działań, z którego została utworzona <xref:System.ServiceModel.Activities.SendReply> działania. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  False   |                       Określa zawartość komunikatu lub parametr do odbierania. Może być albo <xref:System.ServiceModel.Activities.ReceiveMessageContent> działania lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działania. Edytuj tę właściwość, klikając przycisk wielokropka obok **zawartości** w siatce właściwości lub klikając **Definiuj...** przycisk obok **zawartości** etykiety na **Receive** powierzchni projektanta działań. Wyświetl oba **definicji zawartości** okna dialogowego. [!INCLUDE[crabout](../includes/crabout-md.md)] Użyj tego pola, zobacz [definicji zawartości, okno dialogowe](../workflow-designer/content-definition-dialog-box.md) tematu.                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  False   |            Określa kolekcję elementów <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które zainicjować wielu <xref:System.ServiceModel.Activities.CorrelationHandle> obiektów, które to skonfigurować <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> właściwości siatki właściwości, aby otworzyć **Dodaj inicjatory korelacji** okno dialogowe. [!INCLUDE[crabout](../includes/crabout-md.md)] za pomocą tego pola, zobacz [Dodawanie CorrelationInitializers, okno dialogowe](../workflow-designer/add-correlationinitializers-dialog-box.md) tematu.            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  False   |                                                                                                                                                                                                                                              Określa nagłówek akcji w wiadomości. Jeśli nie jest jawnie ustawiona wartość ustawiona wartość domyślna:<br /><br /> <strong>https://tempuri.org/{service kontrakt przestrzeni nazw} / {Nazwa kontraktu usługi} / {nazwa operacji}</strong>                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  False   |                                                                                                                                                                                                                                                                                          Określa, czy wystąpienie przepływu pracy powinny zostać utrwalone przed wysłaniem komunikat odpowiedzi. Wartość domyślna to **false**.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Zobacz też  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Odbieranie](../workflow-designer/receive-activity-designer.md)   
 [Wyślij](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)