---
title: SendAndReceiveReply Projektant szablonów | Dokumenty firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1bfe43f410709a924b0ebdb0cf6afbb8d30a8fcf
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395345"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply, projektant szablonów
**SendAndReceiveReply** szablon jest używany do tworzenia pary <xref:System.ServiceModel.Activities.Send> wstępnie <xref:System.ServiceModel.Activities.ReceiveReply> skonfigurowane <xref:System.Activities.Statements.Sequence> i działania w ramach działania, które są skorelowane jako część wzorca wymiany komunikatów żądanie/odpowiedź na kliencie.

## <a name="the-sendandreceivereply-template"></a>Szablon SendAndReceiveReply
 Dodawanie **SendAndReceiveReply** szablon robi trzy <xref:System.ServiceModel.Activities.Send> rzeczy <xref:System.ServiceModel.Activities.ReceiveReply> oprócz tworzenia <xref:System.Activities.Statements.Sequence> i działań w ramach działania:

1. Konfiguruje <xref:System.ServiceModel.Activities.Send.OperationName%2A> <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> właściwości <xref:System.ServiceModel.Activities.Send> działania.

2. Wiąże <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> właściwość <xref:System.ServiceModel.Activities.ReceiveReply> działania z <xref:System.ServiceModel.Activities.Send> działaniem.

3. Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienną w działaniu nadrzędnym.

### <a name="using-the-sendandreceivereply-template-designer"></a>Korzystanie z SendAndReceiveReply Projektant szablonów
 Projektant działań **SendAndReceiveReply** można znaleźć w kategorii **Wiadomości** **przybornika**, do której uzyskuje [!INCLUDE[wfd2](../includes/wfd2-md.md)] się dostęp, klikając kartę **Przybornik** (Alternatywnie wybierz **pasek narzędzi** z menu **Widok** lub CTRL+ALT+X).

 **SendAndReceiveReply** projektanta działań mogą być przeciągane z [!INCLUDE[wfd2](../includes/wfd2-md.md)] **przybornika** i upuszczone na powierzchni, gdzie zwykle są umieszczane działania. Spowoduje to <xref:System.ServiceModel.Activities.Send> utworzenie działania, które można skonfigurować za pomocą <xref:System.ServiceModel.Activities.ReceiveReply> projektanta działania **Wyślij** i skorelowane, które mogą być konfigurowane za pomocą projektanta **ReceiveReplyForSend.**

 [!INCLUDE[crabout](../includes/crabout-md.md)]za **Send** pomocą projektanta Wyślij <xref:System.ServiceModel.Activities.Send> skonfigurować działanie, zobacz [Wyślij](../workflow-designer/send-activity-designer.md) tematu.

 [!INCLUDE[crabout](../includes/crabout-md.md)]za pomocą **ReceiveReplyForSend projektanta,** aby skonfigurować <xref:System.ServiceModel.Activities.ReceiveReply> działanie, zobacz następującą sekcję.

### <a name="properties-of-receivereply"></a>Właściwości ReceiveReply
 W poniższej <xref:System.ServiceModel.Activities.ReceiveReply> tabeli przedstawiono właściwości i opisano, jak są one używane w projektancie. Te właściwości mogą być edytowane w siatce [!INCLUDE[wfd2](../includes/wfd2-md.md)]właściwości, a niektóre mogą być edytowane na powierzchni projektanta.

|                                 Nazwa właściwości                                 | Wymagany |                                                                                                                                                                                                                                                                                                                                                        Sposób użycia                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            Opcjonalna przyjazna <xref:System.ServiceModel.Activities.ReceiveReply> nazwa działania. Wartość domyślna to ReceiveReplyForSend.<br /><br /> Chociaż użycie wartości nie domyślnej dla <xref:System.Activities.Activity.DisplayName%2A> przyjaznego nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie takiej wartości.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   True   | Odwołanie do <xref:System.ServiceModel.Activities.Send> działania w <xref:System.ServiceModel.Activities.ReceiveReply> połączeniu z tym działaniem. Ta właściwość nie może mieć **wartości null**. <xref:System.ServiceModel.Activities.Send>i <xref:System.ServiceModel.Activities.ReceiveReply> działania są używane razem na kliencie do modelowania wzorca wiadomości żądania/odpowiedzi. Ta właściwość <xref:System.ServiceModel.Activities.Send> określa, które działanie jest sparowane. W projektancie nie można edytować tej właściwości, <xref:System.ServiceModel.Activities.Send> ponieważ jest ona <xref:System.ServiceModel.Activities.ReceiveReply> automatycznie powiązana z działaniem, z którego utworzono działanie. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        Określa zawartość wiadomości lub parametrów do odebrania. Może to być <xref:System.ServiceModel.Activities.ReceiveMessageContent> działanie lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działanie. Edytuj tę właściwość, klikając przycisk elipsy obok pola **Zawartość** w siatce właściwości lub klikając przycisk **Definiuj...** obok etykiety **Zawartość** na powierzchni projektanta **działań Odbierania.** Oba wyświetlają okno dialogowe **Definicja zawartości.** [!INCLUDE[crabout](../includes/crabout-md.md)]jak korzystać z tego pola, zobacz temat [okna dialogowego Definicja zawartości.](../workflow-designer/content-definition-dialog-box.md)                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              Określa kolekcję <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które <xref:System.ServiceModel.Activities.CorrelationHandle> inicjują <xref:System.ServiceModel.Activities.Receive> wiele obiektów, które konfigurują to działanie w przepływie pracy. Kliknij przycisk wielokropka <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> obok właściwości w siatce właściwości, aby otworzyć okno dialogowe **Dodawanie inicjatorów korelacji.** [!INCLUDE[crabout](../includes/crabout-md.md)]korzystając z tego pola, zobacz temat [Okno dialogowe Dodawanie correlationInitializers.](../workflow-designer/add-correlationinitializers-dialog-box.md)               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               Określa nagłówek akcji wiadomości. Jeśli nie jest jawnie ustawiona, jego wartość domyślnie wynosi:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`.                                                                                                                                                                                                                                              |

## <a name="see-also"></a>Zobacz też
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)