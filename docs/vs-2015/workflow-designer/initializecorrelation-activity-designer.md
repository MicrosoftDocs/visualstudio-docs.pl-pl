---
title: InitializeCorrelation — Projektant działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 145b67574169696771f4102b29e9dc8f6a9d1575
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659018"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation, projektant działań
Projektant działań **InitializeCorrelation** służy do tworzenia i konfigurowania działania <xref:System.ServiceModel.Activities.InitializeCorrelation>, które służy do ustanawiania korelacji między komunikatami przed ich wysłaniem lub odebraniem.

## <a name="the-initializecorrelation-activity"></a>Działanie InitializeCorrelation
 Działanie <xref:System.ServiceModel.Activities.InitializeCorrelation> służy do inicjowania korelacji bez wysyłania ani otrzymywania wiadomości. Zwykle korelacja jest inicjowana podczas wysyłania lub otrzymywania wiadomości. Jeśli należy ustalić korelację przed wysłaniem lub odebraniem komunikatu, użyj <xref:System.ServiceModel.Activities.InitializeCorrelation> do zainicjowania korelacji.

### <a name="using-the-initializecorrelation-activity-designer"></a>Korzystanie z projektanta działań InitializeCorrelation
 Projektanta działań **InitializeCorrelation** można znaleźć w kategorii **wiadomości** w **przyborniku**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** w [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz pozycję **pasek narzędzi** z widoku) **.** menu lub CTRL + ALT + X.)

 Projektanta działań **InitializeCorrelation** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchnię. Spowoduje to utworzenie działania <xref:System.ServiceModel.Activities.InitializeCorrelation> przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> InitializeCorrelation. <xref:System.Activities.Activity.DisplayName%2A> można edytować w nagłówku projektanta działań **InitializeCorrelation** lub w polu **DisplayName** okna **Właściwości** .

 @No__t_0 można określić w polu **korelacji** w oknie **Właściwości** na powierzchni projektanta aktywności **InitializeCorrelation** .

 Kliknięcie przycisku wielokropka obok pola **initalizecorrelation** w oknie **dialogowym właściwości** lub "widok..." tekst wskazówki na powierzchni projektanta aktywności **InitializeCorrelation** wyświetlane jest okno dialogowe **Inicjowanie korelacji** , w którym można określić uchwyt korelacji i pary klucz-wartość używane do inicjowania. [!INCLUDE[crabout](../includes/crabout-md.md)] przy użyciu tego okna dialogowego, zobacz [okno dialogowe Edytor kolekcji typów](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>Właściwości InitializeCorrelation
 W poniższej tabeli przedstawiono właściwości <xref:System.ServiceModel.Activities.InitializeCorrelation> i opisano sposób ich używania w projektancie. Te właściwości można edytować w oknie **Właściwości** lub na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa działania <xref:System.ServiceModel.Activities.InitializeCorrelation>. Wartość domyślna to InitializeCorrelation.<br /><br /> Chociaż użycie wartości innej niż domyślna dla przyjaznej <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie takiej wartości.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|@No__t_0 używany do kojarzenia działań przepływu pracy w korelacji.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Słownik danych korelacji, który wiąże komunikaty z wystąpieniem przepływu pracy.<br /><br /> Aby skonfigurować <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>, użyj okna dialogowego **Inicjowanie korelacji** . [!INCLUDE[crabout](../includes/crabout-md.md)] oknie dialogowym korzystanie z tego okna, zobacz [okno dialogowe Edytor kolekcji typów](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Zobacz też
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [odbierać](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [wysyłania](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)