---
title: CorrelationScope — Projektant działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6ffcfd63d60ab6f085b5cb2a793e8bf17a50d8e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656915"
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope, projektant działań
Projektant działań **CorrelationScope** służy do tworzenia i konfigurowania działania <xref:System.ServiceModel.Activities.CorrelationScope>, które zapewnia niejawne zarządzanie podrzędnymi działaniami związanymi z obsługą komunikatów przy użyciu obiektu <xref:System.ServiceModel.Activities.CorrelationHandle>.

## <a name="the-correlationscope-activity"></a>Działanie CorrelationScope
 Właściwość <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> określa <xref:System.ServiceModel.Activities.CorrelationHandle> używany do zarządzania podrzędnymi działaniami związanymi z obsługą komunikatów. Działania <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive> zawarte w <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> są skonfigurowane do używania właściwości <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> zawierającej działania <xref:System.ServiceModel.Activities.CorrelationScope> do przeprowadzenia korelacji.

### <a name="using-the-correlationscope-activity-designer"></a>Korzystanie z projektanta działań CorrelationScope
 Projektanta działań **CorrelationScope** można znaleźć w kategorii **wiadomości** w **przyborniku**, do którego uzyskuje się dostęp, klikając kartę **Przybornik** po lewej stronie [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie, wybierając pozycję **pasek narzędzi** z Menu **Widok** lub CTRL + ALT + X.)

 Projektanta działań **CorrelationScope** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchnię. Spowoduje to utworzenie działania <xref:System.ServiceModel.Activities.CorrelationScope> z domyślną wartością **DisplayName** CorrelationScope. @No__t_0 można edytować w nagłówku projektanta działań **CorrelationScope** lub w polu **DisplayName** okna **Właściwości** .

 Aby określić <xref:System.ServiceModel.Activities.CorrelationHandle> używany przez podrzędne działania obsługi komunikatów, kliknij przycisk wielokropka obok pola **CorrelatesWith** w oknie **Właściwości** , aby wyświetlić okno dialogowe **Edytor wyrażeń** . Tę właściwość można również ustawić na powierzchni projektanta aktywności.

 Działania należące do zakresu korelacji są określane przez upuszczenie ich projektantów w obrębie pola **Body** w programie **CorrelationScope** Designer.

### <a name="the-correlationscope-properties"></a>Właściwości CorrelationScope
 W poniższej tabeli przedstawiono właściwości <xref:System.ServiceModel.Activities.CorrelationScope> i opisano sposób ich używania w projektancie. Te właściwości można edytować w oknie **Właściwości** lub na powierzchni projektanta [!INCLUDE[wfd2](../includes/wfd2-md.md)] i często w obu kierunkach.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalna przyjazna nazwa działania <xref:System.ServiceModel.Activities.InitializeCorrelation>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Określa <xref:System.ServiceModel.Activities.CorrelationHandle> używany do zarządzania podrzędnymi działaniami związanymi z obsługą komunikatów. Jeśli ta właściwość nie zostanie ustawiona, <xref:System.ServiceModel.Activities.CorrelationScope> automatycznie tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> niejawną.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Określa działania w zakresie korelacji.|

## <a name="see-also"></a>Zobacz też
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [odbierać](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [wysyłania](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)