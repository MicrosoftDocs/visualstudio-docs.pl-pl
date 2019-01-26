---
title: Projektant przepływu pracy — InitializeCorrelation, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ff0dd27409c77e75a451e98a3771dfb78bf2b7d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070789"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation, projektant działań

**InitializeCorrelation** projektanta działań służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.InitializeCorrelation> działania. <xref:System.ServiceModel.Activities.InitializeCorrelation> Działanie ustanawia korelacja komunikatów przed wysyłać ani odbierać z nich.

## <a name="the-initializecorrelation-activity"></a>Działanie InitializeCorrelation

<xref:System.ServiceModel.Activities.InitializeCorrelation> To działanie służy do zainicjowania korelacji bez wysyłania i odbierania wiadomości. Zazwyczaj korelacji jest inicjowany przy wysyłaniu lub odbieraniu wiadomości. Jeśli przed wysłanego lub odebranego komunikatu, należy ustanowić korelacji, użyj <xref:System.ServiceModel.Activities.InitializeCorrelation> zainicjować korelacji.

### <a name="using-the-initializecorrelation-activity-designer"></a>Za pomocą InitializeCorrelation, Projektant działań

Dostęp do **InitializeCorrelation** projektanta działań w **komunikatów** kategorii **przybornika**.

**InitializeCorrelation** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy. Projektant działań porzucenie tworzy <xref:System.ServiceModel.Activities.InitializeCorrelation> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> z InitializeCorrelation. <xref:System.Activities.Activity.DisplayName%2A> Mogą być edytowane w nagłówku **InitializeCorrelation** projektanta działań lub **DisplayName** pole **właściwości** okna.

<xref:System.ServiceModel.Activities.CorrelationHandle> Może być Określa **korelacji** pole **właściwości** okno na **InitializeCorrelation** powierzchni projektanta działań.

Aby wyświetlić **inicjowanie korelacji** okno dialogowe, w którym można określić dojście korelacji i pary klucz wartość, używane do zainicjowania, kliknij przycisk wielokropka obok **CorrelationData** pole **właściwości** okna. Lub wybierz "Wyświetl..." tekst wskazówki w **InitializeCorrelation** powierzchni projektanta działań. Aby uzyskać więcej informacji o korzystaniu z tego okna dialogowego, zobacz [okno dialogowe Edytor kolekcji typów](../workflow-designer/type-collection-editor-dialog-box.md) artykułu.

### <a name="the-initializecorrelation-properties"></a>Właściwości InitializeCorrelation

W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.InitializeCorrelation> właściwości oraz opisano sposoby ich używania w projektancie. Te właściwości można edytować w **właściwości** oknie lub na powierzchni projektanta przepływów pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.ServiceModel.Activities.InitializeCorrelation> działania. Wartość domyślna to InitializeCorrelation.<br /><br /> Mimo że użycie wartości innych niż domyślne przyjazna <xref:System.Activities.Activity.DisplayName%2A> nie jest bezwzględnie konieczne jest zalecane.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> Używanego do kojarzenia działań przepływu pracy w korelacji.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Słownik danych korelacji, który odnosi się komunikaty do wystąpienia przepływu pracy.<br /><br /> Użyj **inicjowanie korelacji** okno dialogowe konfigurowania <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Aby uzyskać więcej informacji na temat użycia to okno dialogowe, zobacz [okno dialogowe Edytor kolekcji typów](../workflow-designer/type-collection-editor-dialog-box.md) artykułu.|

## <a name="see-also"></a>Zobacz także

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)