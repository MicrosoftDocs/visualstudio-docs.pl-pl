---
title: Projektant przepływu pracy — Projektant działań CorrelationScope
description: Dowiedz się, jak za pomocą projektanta działań CorrelationScope utworzyć i skonfigurować działanie CorrelationScope.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e9edd755465cf812c1572c62f1c6335fc5295281
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955527"
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope, projektant działań

Projektant działań **CorrelationScope** służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.CorrelationScope> działania, które zapewnia niejawne zarządzanie podrzędnymi działaniami związanymi z obsługą komunikatów przy użyciu <xref:System.ServiceModel.Activities.CorrelationHandle> obiektu.

## <a name="the-correlationscope-activity"></a>Działanie CorrelationScope

<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>Właściwość określa, że <xref:System.ServiceModel.Activities.CorrelationHandle> służy do zarządzania podrzędnymi działaniami związanymi z obsługą komunikatów. <xref:System.ServiceModel.Activities.Send>Działania i <xref:System.ServiceModel.Activities.Receive> zawarte w programie <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> są skonfigurowane do używania <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> Właściwości zawierającego <xref:System.ServiceModel.Activities.CorrelationScope> działania w celu przeprowadzenia korelacji.

### <a name="use-the-correlationscope-activity-designer"></a>Korzystanie z projektanta działań CorrelationScope

Projektanta działań **CorrelationScope** można znaleźć w kategorii **wiadomości** w **przyborniku**, do którego uzyskuje się dostęp, klikając kartę **Przybornik** po lewej stronie Projektant przepływu pracy. Alternatywnie możesz wybrać **Przybornik** z menu **Widok** lub nacisnąć **klawisze CTRL** + **Alt** + **X**.

Projektanta działań **CorrelationScope** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.CorrelationScope> działania z domyślną wartością **DisplayName** elementu CorrelationScope. <xref:System.Activities.Activity.DisplayName%2A>Można edytować w nagłówku projektanta działań **CorrelationScope** lub w polu **DisplayName** okna **Właściwości** .

Aby określić <xref:System.ServiceModel.Activities.CorrelationHandle> używane przez podrzędne działania obsługi komunikatów, wybierz przycisk wielokropka obok pola **CorrelatesWith** w oknie **Właściwości** , aby wyświetlić okno dialogowe **Edytor wyrażeń** . Tę właściwość można również ustawić na powierzchni projektanta aktywności.

Działania należące do zakresu korelacji są określane przez upuszczenie ich projektantów w obrębie pola **Body** w programie **CorrelationScope** Designer.

### <a name="the-correlationscope-properties"></a>Właściwości CorrelationScope

W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.CorrelationScope> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w oknie **Właściwości** lub na Projektant przepływu pracy powierzchni i często w obu.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Opcjonalna przyjazna nazwa <xref:System.ServiceModel.Activities.InitializeCorrelation> działania.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|Fałsz|Określa <xref:System.ServiceModel.Activities.CorrelationHandle> używany do zarządzania podrzędnymi działaniami związanymi z obsługą komunikatów. Jeśli ta właściwość nie zostanie ustawiona, program <xref:System.ServiceModel.Activities.CorrelationScope> automatycznie tworzy niejawny element <xref:System.ServiceModel.Activities.CorrelationHandle> .|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|Fałsz|Określa działania w zakresie korelacji.|

## <a name="see-also"></a>Zobacz też

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Odbieranie](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Wysyłanie](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)