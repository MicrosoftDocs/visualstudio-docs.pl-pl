---
title: Projektant przepływu pracy — Projektant działań InitializeCorrelation
description: Dowiedz się, jak za pomocą projektanta działań InitializeCorrelation utworzyć i skonfigurować działanie InitializeCorrelation.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82b786277c79a355e1859b337a45ab093e6f2a42
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437791"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation, projektant działań

Projektant działań **InitializeCorrelation** służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.InitializeCorrelation> działania. <xref:System.ServiceModel.Activities.InitializeCorrelation>Działanie ustanawia korelację między komunikatami przed ich wysłaniem lub odebraniem.

## <a name="the-initializecorrelation-activity"></a>Działanie InitializeCorrelation

<xref:System.ServiceModel.Activities.InitializeCorrelation>Działanie służy do inicjowania korelacji bez wysyłania lub otrzymywania wiadomości. Zwykle korelacja jest inicjowana podczas wysyłania lub otrzymywania wiadomości. Jeśli należy ustalić korelację przed wysłaniem lub odebraniem komunikatu, użyj <xref:System.ServiceModel.Activities.InitializeCorrelation> do zainicjowania korelacji.

### <a name="using-the-initializecorrelation-activity-designer"></a>Korzystanie z projektanta działań InitializeCorrelation

Dostęp do projektanta działań **InitializeCorrelation** w kategorii **Obsługa wiadomości** w **przyborniku**.

Projektanta działań **InitializeCorrelation** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię. Porzucenie projektanta działań powoduje utworzenie <xref:System.ServiceModel.Activities.InitializeCorrelation> działania z wartością domyślną <xref:System.Activities.Activity.DisplayName%2A> InitializeCorrelation. <xref:System.Activities.Activity.DisplayName%2A>Można edytować w nagłówku projektanta działań **InitializeCorrelation** lub w polu **DisplayName** okna **Właściwości** .

<xref:System.ServiceModel.Activities.CorrelationHandle>Można określić w polu **korelacji** w oknie **Właściwości** na powierzchni projektanta aktywności **InitializeCorrelation** .

Aby wyświetlić okno dialogowe **Inicjowanie korelacji** , w którym można określić uchwyt korelacji i par klucz-wartość używanych do jego zainicjowania, wybierz przycisk wielokropka obok pola **Initalizecorrelation** w oknie **Właściwości** . Lub wybierz pozycję "widok..." tekst wskazówki na powierzchni projektanta działań **InitializeCorrelation** . Aby uzyskać więcej informacji na temat korzystania z tego okna dialogowego, zobacz artykuł [okno dialogowe Edytor kolekcji typów](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>Właściwości InitializeCorrelation

W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.InitializeCorrelation> właściwości i opisano, jak są one używane w projektancie. Te właściwości można edytować w oknie **Właściwości** lub na Projektant przepływu pracy powierzchni.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa <xref:System.ServiceModel.Activities.InitializeCorrelation> działania. Wartość domyślna to InitializeCorrelation.<br /><br /> Chociaż użycie wartości innej niż domyślna dla elementu friendly <xref:System.Activities.Activity.DisplayName%2A> nie jest absolutnie wymagane, jest to zalecane.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|Fałsz|<xref:System.ServiceModel.Activities.CorrelationHandle>Służy do kojarzenia działań przepływu pracy w korelacji.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|Fałsz|Słownik danych korelacji, który wiąże komunikaty z wystąpieniem przepływu pracy.<br /><br /> Za pomocą okna dialogowego **Inicjowanie korelacji** można skonfigurować <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> . Aby uzyskać więcej informacji na temat korzystania z tego okna dialogowego, zobacz [okno dialogowe Edytor kolekcji typów](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Zobacz też

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Odbieranie](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Wysyłanie](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)