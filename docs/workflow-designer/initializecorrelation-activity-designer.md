---
title: Projektant przepływu pracy — Projektant działań InitializeCorrelation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98a9a6bccb6eab2c4565a717daa897f93dbe8f53
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650225"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation, projektant działań

Projektant działań **InitializeCorrelation** służy do tworzenia i konfigurowania działania <xref:System.ServiceModel.Activities.InitializeCorrelation>. Działanie <xref:System.ServiceModel.Activities.InitializeCorrelation> ustanawia korelację między komunikatami przed ich wysłaniem lub odebraniem.

## <a name="the-initializecorrelation-activity"></a>Działanie InitializeCorrelation

Działanie <xref:System.ServiceModel.Activities.InitializeCorrelation> służy do inicjowania korelacji bez wysyłania ani otrzymywania wiadomości. Zwykle korelacja jest inicjowana podczas wysyłania lub otrzymywania wiadomości. Jeśli należy ustalić korelację przed wysłaniem lub odebraniem komunikatu, użyj <xref:System.ServiceModel.Activities.InitializeCorrelation> do zainicjowania korelacji.

### <a name="using-the-initializecorrelation-activity-designer"></a>Korzystanie z projektanta działań InitializeCorrelation

Dostęp do projektanta działań **InitializeCorrelation** w kategorii **Obsługa wiadomości** w **przyborniku**.

Projektanta działań **InitializeCorrelation** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię. Porzucenie projektanta działań powoduje utworzenie działania <xref:System.ServiceModel.Activities.InitializeCorrelation> przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> InitializeCorrelation. @No__t_0 można edytować w nagłówku projektanta działań **InitializeCorrelation** lub w polu **DisplayName** okna **Właściwości** .

@No__t_0 można określić w polu **korelacji** w oknie **Właściwości** na powierzchni projektanta aktywności **InitializeCorrelation** .

Aby wyświetlić okno dialogowe **Inicjowanie korelacji** , w którym można określić uchwyt korelacji i par klucz-wartość używanych do jego zainicjowania, wybierz przycisk wielokropka obok pola **Initalizecorrelation** w oknie **Właściwości** . Lub wybierz pozycję "widok..." tekst wskazówki na powierzchni projektanta działań **InitializeCorrelation** . Aby uzyskać więcej informacji na temat korzystania z tego okna dialogowego, zobacz artykuł [okno dialogowe Edytor kolekcji typów](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>Właściwości InitializeCorrelation

W poniższej tabeli przedstawiono właściwości <xref:System.ServiceModel.Activities.InitializeCorrelation> i opisano, jak są one używane w projektancie. Te właściwości można edytować w oknie **Właściwości** lub na Projektant przepływu pracy powierzchni.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa działania <xref:System.ServiceModel.Activities.InitializeCorrelation>. Wartość domyślna to InitializeCorrelation.<br /><br /> Chociaż użycie wartości innej niż domyślna dla przyjaznego <xref:System.Activities.Activity.DisplayName%2A> nie jest absolutnie wymagane, zaleca się ją.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|@No__t_0 używany do kojarzenia działań przepływu pracy w korelacji.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Słownik danych korelacji, który wiąże komunikaty z wystąpieniem przepływu pracy.<br /><br /> Aby skonfigurować <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>, użyj okna dialogowego **Inicjowanie korelacji** . Aby uzyskać więcej informacji na temat korzystania z tego okna dialogowego, zobacz [okno dialogowe Edytor kolekcji typów](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Zobacz także

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)