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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656955"
---
# <a name="content-definition-dialog-box"></a>Definicja zawartości, okno dialogowe
Okno dialogowe **Definicja zawartości** służy [!INCLUDE[wfd1](../includes/wfd1-md.md)] do konfigurowania właściwości **zawartości** <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> działań,, <xref:System.ServiceModel.Activities.SendReply> i <xref:System.ServiceModel.Activities.ReceiveReply> . [!INCLUDE[crabout](../includes/crabout-md.md)] Projektanci działań, którzy korzystają z tego pola, zobacz tematy dotyczące [wysyłania](../workflow-designer/send-activity-designer.md), [odbierania](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)i [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

 W poniższej tabeli opisano elementy interfejsu użytkownika (UI) okna dialogowego **Inicjowanie korelacji** .

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**Wiadomość**|Określa zawartość komunikatu przy użyciu pola tekstowego wyrażenie **danych komunikatu** i typ za pomocą pola listy rozwijanej **typ komunikatu** . Domyślnie **Definicja zawartości** używa klasy <xref:System.ServiceModel.Activities.ReceiveMessageContent> , która oczekuje <xref:System.ServiceModel.Channels.Message> typu kontraktu lub komunikatu w definicji usługi przepływu pracy.|
|**Parametry**|Kliknij przycisk radiowy **Parametry** , aby użyć <xref:System.ServiceModel.Activities.ReceiveParametersContent> , który oczekuje kontraktu danych. Użyj siatki danych, aby ustawić ogólną kolekcję <xref:System.Activities.OutArgument> par klucz/wartość, których wartości są przypisywane do parametrów zmiennych w bieżącym przepływie pracy.|

 Okno dialogowe **Definicja zawartości** jest używane przez projektantów **wysyłania**, **odbierania**, **ReceiveAndSendReply**i **SendAndReceiveReply** . Dostęp do nich jest podobny w każdym przypadku, a przypadek odbioru jest używany tutaj do zilustrowania procedury.

 Projektanta działań **odbioru** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, wszędzie tam gdzie działania są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Receive> działania z domyślnym <xref:System.Activities.Activity.DisplayName%2A> odbiorem. Wybierz pozycję **Odbierz** projektanta aktywności i kliknij przycisk wielokropka obok tekstu (zawartość) dla właściwości **zawartość** w siatce właściwości okna dialogowego **Definicja zawartości** , które ma zostać wyświetlone.

 Zawartość można określić w sekcji **Message** dla <xref:System.ServiceModel.Activities.ReceiveMessageContent> działania lub w sekcji **parametrów** dla <xref:System.ServiceModel.Activities.ReceiveParametersContent> działania.

## <a name="see-also"></a>Zobacz też
 [Pomoc interfejsu użytkownika Projektanta przepływu pracy](../workflow-designer/workflow-designer-ui-help.md)