---
title: Projektant przepływu pracy — CorrelationScope, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0562b113e91bb9485eaf356085715522b1b39bc3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829923"
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope, projektant działań

**CorrelationScope** projektanta działań służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.CorrelationScope> działanie, które umożliwia niejawne Zarządzanie podrzędnych działań dotyczących komunikatów za pomocą <xref:System.ServiceModel.Activities.CorrelationHandle> obiektu.

## <a name="the-correlationscope-activity"></a>Działanie CorrelationScope

<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> Właściwość określa <xref:System.ServiceModel.Activities.CorrelationHandle> używany do zarządzania działań dotyczących komunikatów podrzędnych. <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive> działań zawartych w <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> są skonfigurowane do używania <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> właściwości zawierającego <xref:System.ServiceModel.Activities.CorrelationScope> działania do wykonania korelacji.

### <a name="use-the-correlationscope-activity-designer"></a>Użyj CorrelationScope, Projektant działań

**CorrelationScope** projektanta działań można znaleźć w **komunikatów** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** karty w lewej części projektanta przepływów pracy. Można także wybrać **przybornika** z **widoku** menu lub naciśnij klawisz **Ctrl**+**Alt** + **X**.

**CorrelationScope** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.CorrelationScope> działanie przy użyciu domyślnego **DisplayName** z CorrelationScope. <xref:System.Activities.Activity.DisplayName%2A> Mogą być edytowane w nagłówku **CorrelationScope** projektanta działań lub **DisplayName** pole **właściwości** okna.

Aby określić <xref:System.ServiceModel.Activities.CorrelationHandle> używany przez podrzędny działań dotyczących komunikatów, kliknij przycisk wielokropka obok **CorrelatesWith** pole **właściwości** okno, aby wyświetlić **wyrażenia Edytor** okno dialogowe. Można również ustawić tę właściwość na powierzchni projektanta działań.

Działania o określonym zakresie w ramach korelację są określone przez usunięcie ich projektantów w ramach **treści** polu w ramach **CorrelationScope** projektanta.

### <a name="the-correlationscope-properties"></a>Właściwości CorrelationScope

W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.CorrelationScope> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości mogą być edytowane w **właściwości** oknie lub na powierzchni projektanta przepływów pracy i często w obu.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalna nazwa przyjazna <xref:System.ServiceModel.Activities.InitializeCorrelation> działania.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Określa <xref:System.ServiceModel.Activities.CorrelationHandle> używany do zarządzania działań dotyczących komunikatów podrzędnych. Jeśli nie ustawisz tę właściwość, <xref:System.ServiceModel.Activities.CorrelationScope> tworzy ukrytego <xref:System.ServiceModel.Activities.CorrelationHandle> automatycznie.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Określa działań w zakresie korelacji.|

## <a name="see-also"></a>Zobacz także

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)