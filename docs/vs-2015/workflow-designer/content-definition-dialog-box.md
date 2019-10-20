---
title: Okno dialogowe Definicja zawartości | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d989f5a0c57e381041e8fe9c200aae1a76316ad8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656955"
---
# <a name="content-definition-dialog-box"></a>Definicja zawartości, okno dialogowe
Okno dialogowe **Definicja zawartości** służy [!INCLUDE[wfd1](../includes/wfd1-md.md)] do konfigurowania właściwości **zawartości** działań <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> i <xref:System.ServiceModel.Activities.ReceiveReply>. [!INCLUDE[crabout](../includes/crabout-md.md)] projektantów działań, które używają tego pola, zobacz tematy dotyczące [wysyłania](../workflow-designer/send-activity-designer.md), [odbierania](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)i [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

 W poniższej tabeli opisano elementy interfejsu użytkownika (UI) okna dialogowego **Inicjowanie korelacji** .

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**Komunikat**|Określa zawartość komunikatu przy użyciu pola tekstowego wyrażenie **danych komunikatu** i typ za pomocą pola listy rozwijanej **typ komunikatu** . Domyślnie **Definicja zawartości** używa <xref:System.ServiceModel.Activities.ReceiveMessageContent>, która oczekuje <xref:System.ServiceModel.Channels.Message> lub typu kontraktu komunikatu w ramach definicji usługi przepływu pracy.|
|**Parametry**|Kliknij przycisk radiowy **Parametry** , aby użyć <xref:System.ServiceModel.Activities.ReceiveParametersContent>, który oczekuje kontraktu danych. Użyj siatki danych, aby ustawić ogólną kolekcję par klucz/wartość <xref:System.Activities.OutArgument>, których wartości są przypisane do parametrów zmiennych w bieżącym przepływie pracy.|

 Okno dialogowe **Definicja zawartości** jest używane przez projektantów **wysyłania**, **odbierania**, **ReceiveAndSendReply**i **SendAndReceiveReply** . Dostęp do nich jest podobny w każdym przypadku, a przypadek odbioru jest używany tutaj do zilustrowania procedury.

 Projektanta działań **odbioru** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchnię, wszędzie tam gdzie działania są zwykle umieszczane. Spowoduje to utworzenie działania <xref:System.ServiceModel.Activities.Receive> przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> odbierania. Wybierz pozycję **Odbierz** projektanta aktywności i kliknij przycisk wielokropka obok tekstu (zawartość) dla właściwości **zawartość** w siatce właściwości okna dialogowego **Definicja zawartości** , które ma zostać wyświetlone.

 Zawartość można określić w sekcji **Message** dla działania <xref:System.ServiceModel.Activities.ReceiveMessageContent> lub w sekcji **parametrów** dla działania <xref:System.ServiceModel.Activities.ReceiveParametersContent>.

## <a name="see-also"></a>Zobacz też
 [Pomoc interfejsu użytkownika Projektanta przepływu pracy](../workflow-designer/workflow-designer-ui-help.md)