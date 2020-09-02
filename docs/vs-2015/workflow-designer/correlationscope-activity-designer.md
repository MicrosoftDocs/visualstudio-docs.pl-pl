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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656915"
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope, projektant działań
Projektant działań **CorrelationScope** służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.CorrelationScope> działania, które zapewnia niejawne zarządzanie podrzędnymi działaniami związanymi z obsługą komunikatów przy użyciu <xref:System.ServiceModel.Activities.CorrelationHandle> obiektu.

## <a name="the-correlationscope-activity"></a>Działanie CorrelationScope
 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>Właściwość określa, że <xref:System.ServiceModel.Activities.CorrelationHandle> służy do zarządzania podrzędnymi działaniami związanymi z obsługą komunikatów. <xref:System.ServiceModel.Activities.Send>Działania i <xref:System.ServiceModel.Activities.Receive> zawarte w programie <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> są skonfigurowane do używania <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> Właściwości zawierającego <xref:System.ServiceModel.Activities.CorrelationScope> działania w celu przeprowadzenia korelacji.

### <a name="using-the-correlationscope-activity-designer"></a>Korzystanie z projektanta działań CorrelationScope
 Projektanta działań **CorrelationScope** można znaleźć w kategorii **wiadomości** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** w lewej części okna [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X).

 Projektanta działań **CorrelationScope** można przeciągnąć z **przybornika** i upuścić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchnię. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.CorrelationScope> działania z domyślną wartością **DisplayName** elementu CorrelationScope. <xref:System.Activities.Activity.DisplayName%2A>Można edytować w nagłówku projektanta działań **CorrelationScope** lub w polu **DisplayName** okna **Właściwości** .

 Aby określić <xref:System.ServiceModel.Activities.CorrelationHandle> używane przez podrzędne działania obsługi komunikatów, kliknij przycisk wielokropka obok pola **CorrelatesWith** w oknie **Właściwości** , aby wyświetlić okno dialogowe **Edytor wyrażeń** . Tę właściwość można również ustawić na powierzchni projektanta aktywności.

 Działania należące do zakresu korelacji są określane przez upuszczenie ich projektantów w obrębie pola **Body** w programie **CorrelationScope** Designer.

### <a name="the-correlationscope-properties"></a>Właściwości CorrelationScope
 W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.CorrelationScope> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w oknie **Właściwości** lub na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni projektanta i często w obu.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Opcjonalna przyjazna nazwa <xref:System.ServiceModel.Activities.InitializeCorrelation> działania.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|Fałsz|Określa <xref:System.ServiceModel.Activities.CorrelationHandle> używany do zarządzania podrzędnymi działaniami związanymi z obsługą komunikatów. Jeśli ta właściwość nie zostanie ustawiona, program <xref:System.ServiceModel.Activities.CorrelationScope> automatycznie tworzy niejawny element <xref:System.ServiceModel.Activities.CorrelationHandle> .|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|Fałsz|Określa działania w zakresie korelacji.|

## <a name="see-also"></a>Zobacz też
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [odbierać](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [wysyłania](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)