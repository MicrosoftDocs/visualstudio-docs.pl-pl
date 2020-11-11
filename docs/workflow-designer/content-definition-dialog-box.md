---
title: Projektant przepływu pracy — okno dialogowe Definicja zawartości
description: Dowiedz się, jak za pomocą okna dialogowego definicja zawartości skonfigurować właściwości zawartości działań typu wysyłanie, odbieranie, działanie SendReply i ReceiveReply.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2858c179d05645b3e47e6be27e386168392fcb48
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438168"
---
# <a name="content-definition-dialog-box"></a>Definicja zawartości, okno dialogowe

Okno dialogowe **Definicja zawartości** Projektant przepływu pracy służy do konfigurowania właściwości **zawartości** <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> działań,, <xref:System.ServiceModel.Activities.SendReply> , i <xref:System.ServiceModel.Activities.ReceiveReply> . Aby uzyskać więcej informacji na temat projektantów działań, które używają tego pola, zobacz tematy dotyczące [wysyłania](../workflow-designer/send-activity-designer.md), [odbierania](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)i [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

W poniższej tabeli opisano elementy interfejsu użytkownika (UI) okna dialogowego **Inicjowanie korelacji** :

|Element interfejsu użytkownika|Opis|
|-|-----------------|
|**Wiadomość**|Określa zawartość komunikatu przy użyciu pola tekstowego wyrażenie **danych komunikatu** i typ za pomocą pola listy rozwijanej **typ komunikatu** . Domyślnie **Definicja zawartości** używa klasy <xref:System.ServiceModel.Activities.ReceiveMessageContent> , która oczekuje <xref:System.ServiceModel.Channels.Message> typu kontraktu lub komunikatu w definicji usługi przepływu pracy.|
|**Parametry**|Kliknij przycisk radiowy **Parametry** , aby użyć <xref:System.ServiceModel.Activities.ReceiveParametersContent> , który oczekuje kontraktu danych. Użyj siatki danych, aby ustawić ogólną kolekcję <xref:System.Activities.OutArgument> par klucz/wartość, których wartości są przypisywane do parametrów zmiennych w bieżącym przepływie pracy.|

Okno dialogowe **Definicja zawartości** jest używane przez projektantów **wysyłania** , **odbierania** , **ReceiveAndSendReply** i **SendAndReceiveReply** . Dostęp do nich jest podobny w każdym przypadku, a przypadek odbioru jest używany tutaj do zilustrowania procedury.

Projektanta działań **odbioru** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam gdzie działania są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Receive> działania z domyślnym <xref:System.Activities.Activity.DisplayName%2A> odbiorem. Wybierz pozycję **Odbierz** projektanta aktywności i kliknij przycisk wielokropka obok tekstu (zawartość) dla właściwości **zawartość** w siatce właściwości okna dialogowego **Definicja zawartości** , które ma zostać wyświetlone.

Zawartość można określić w sekcji **Message** dla <xref:System.ServiceModel.Activities.ReceiveMessageContent> działania lub w sekcji **parametrów** dla <xref:System.ServiceModel.Activities.ReceiveParametersContent> działania.

## <a name="see-also"></a>Zobacz też

- [Pomoc interfejsu użytkownika Projektanta przepływu pracy](browse-and-select-a-dotnet-type-dialog-box.md)