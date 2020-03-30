---
title: ReceiveAndSendReply Projektant szablonów | Dokumenty firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c00eed244867cfd38b20f6a8f065fc6da006801
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395392"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply, projektant szablonów
**Szablon ReceiveAndSendReply** służy do tworzenia pary wstępnie <xref:System.ServiceModel.Activities.Receive> skonfigurowanych i <xref:System.ServiceModel.Activities.SendReply> <xref:System.Activities.Statements.Sequence> działań w ramach działania, które są skorelowane jako część wzorca wymiany komunikatów żądania/odpowiedzi na serwerze.

## <a name="the-receiveandsendreply-template"></a>Szablon ReceiveAndSendReply
 Dodawanie **ReceiveAndSendReply** szablon robi trzy <xref:System.ServiceModel.Activities.Receive> rzeczy <xref:System.ServiceModel.Activities.SendReply> oprócz tworzenia <xref:System.Activities.Statements.Sequence> i działań z działania:

1. Konfiguruje <xref:System.ServiceModel.Activities.Receive.OperationName%2A> <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> właściwości <xref:System.ServiceModel.Activities.Receive> działania.

2. Wiąże <xref:System.ServiceModel.Activities.SendReply.Request%2A> właściwość <xref:System.ServiceModel.Activities.Receive> działania z <xref:System.ServiceModel.Activities.Send> działaniem.

3. Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienną w działaniu nadrzędnym.

### <a name="using-the-receiveandsendreply-template-designer"></a>Korzystanie z ReceiveAndSendReply Projektant szablonów
 Projektant działań **ReceiveAndSendReply** można znaleźć w kategorii **Wiadomości** **przybornika**, do której uzyskuje [!INCLUDE[wfd2](../includes/wfd2-md.md)] się dostęp, klikając kartę **Przybornik** (alternatywnie, wybierz pasek **narzędzi** z menu **Widok** lub CTRL+ALT+X).

 **ReceiveAndSendReply** projektanta działań mogą być przeciągane z [!INCLUDE[wfd2](../includes/wfd2-md.md)] **przybornika** i upuszczone na powierzchni, gdzie zwykle są umieszczane działania. Spowoduje to <xref:System.ServiceModel.Activities.Receive> utworzenie działania, które można skonfigurować za pomocą <xref:System.ServiceModel.Activities.SendReply> projektanta działania **Wyślij** i skorelowane, które mogą być konfigurowane za pomocą SendReplyToReceive projektanta.

 [!INCLUDE[crabout](../includes/crabout-md.md)]za pomocą **Projektanta** Receive <xref:System.ServiceModel.Activities.Receive> skonfigurować działanie, zobacz [Receive](../workflow-designer/receive-activity-designer.md) tematu.

 [!INCLUDE[crabout](../includes/crabout-md.md)]za pomocą **SendReplyToReceive projektanta,** aby skonfigurować <xref:System.ServiceModel.Activities.SendReply> działanie, zobacz następującą sekcję.

### <a name="properties-of-sendreply"></a>Właściwości SendReply
 W poniższej <xref:System.ServiceModel.Activities.SendReply> tabeli przedstawiono właściwości i opisano, jak są one używane w projektancie. Te właściwości mogą być edytowane w siatce [!INCLUDE[wfd2](../includes/wfd2-md.md)] właściwości, a niektóre mogą być edytowane na powierzchni projektanta.

|                               Nazwa właściwości                                | Wymagany |                                                                                                                                                                                                                                                                                                                                                      Sposób użycia                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  False   |                                                                                                                                                                                            Opcjonalna przyjazna <xref:System.ServiceModel.Activities.SendReply> nazwa działania. Wartość domyślna to SendReplyToReceive.<br /><br /> Chociaż użycie wartości nie domyślnej dla <xref:System.Activities.Activity.DisplayName%2A> przyjaznego nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie takiej wartości.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   True   | Odwołanie do <xref:System.ServiceModel.Activities.Receive> działania w <xref:System.ServiceModel.Activities.SendReply> połączeniu z tym działaniem. Ta właściwość nie może mieć **wartości null**. <xref:System.ServiceModel.Activities.Receive>i <xref:System.ServiceModel.Activities.SendReply> działania są używane razem na serwerze do modelowania wzorca wiadomości żądania/odpowiedzi. Ta właściwość <xref:System.ServiceModel.Activities.Send> określa, które działanie jest sparowane. W projektancie nie można edytować tej właściwości, <xref:System.ServiceModel.Activities.Send> ponieważ jest ona <xref:System.ServiceModel.Activities.SendReply> automatycznie powiązana z działaniem, z którego utworzono działanie. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  False   |                       Określa zawartość wiadomości lub parametrów do odebrania. Może to być <xref:System.ServiceModel.Activities.ReceiveMessageContent> działanie lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działanie. Edytuj tę właściwość, klikając przycisk elipsy obok pola **Zawartość** w siatce właściwości lub klikając przycisk **Definiuj...** obok etykiety **Zawartość** na powierzchni projektanta **działań Odbierania.** Oba wyświetlają okno dialogowe **Definicja zawartości.** [!INCLUDE[crabout](../includes/crabout-md.md)]jak korzystać z tego pola, zobacz temat [okna dialogowego Definicja zawartości.](../workflow-designer/content-definition-dialog-box.md)                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  False   |            Określa kolekcję <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które <xref:System.ServiceModel.Activities.CorrelationHandle> inicjują <xref:System.ServiceModel.Activities.Receive> wiele obiektów, które konfigurują to działanie w przepływie pracy. Kliknij przycisk wielokropka <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> obok właściwości w siatce właściwości, aby otworzyć okno dialogowe **Dodawanie inicjatorów korelacji.** [!INCLUDE[crabout](../includes/crabout-md.md)]korzystając z tego pola, zobacz temat [Okno dialogowe Dodawanie correlationInitializers.](../workflow-designer/add-correlationinitializers-dialog-box.md)            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  False   |                                                                                                                                                                                                                                              Określa nagłówek akcji wiadomości. Jeśli nie jest jawnie ustawiona, jego wartość domyślnie wynosi:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  False   |                                                                                                                                                                                                                                                                                          Określa, czy wystąpienie przepływu pracy ma być zachowywane przed wysłaniem wiadomości odpowiedzi. Wartość domyślna to **fałsz**.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Zobacz też
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Odbieranie](../workflow-designer/receive-activity-designer.md) [Wyślij](../workflow-designer/send-activity-designer.md) [Wyślij I Receply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)