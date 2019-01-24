---
title: Okno dialogowe definicji zawartości | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 17b5b5609718dce1347928be491e8817b5796e4d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790470"
---
# <a name="content-definition-dialog-box"></a>Definicja zawartości, okno dialogowe
**Definicji zawartości** okno dialogowe jest używany w [!INCLUDE[wfd1](../includes/wfd1-md.md)] skonfigurować **zawartości** właściwości <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply> działania. [!INCLUDE[crabout](../includes/crabout-md.md)] Projektanci działań, które używają tego pola, zobacz [wysyłania](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), i [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) tematów.  
  
 W poniższej tabeli opisano elementy interfejsu użytkownika **inicjowanie korelacji** okno dialogowe.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Komunikat**|Określa komunikat, który zawartość **komunikatu danych** pole tekstowe wyrażenie i typu przy użyciu **typ komunikatu** pole listy rozwijanej. Domyślnie **definicji zawartości** używa <xref:System.ServiceModel.Activities.ReceiveMessageContent>, która oczekuje <xref:System.ServiceModel.Channels.Message> lub typu w definicji usługi przepływu pracy kontraktu komunikatu.|  
|**Parametry**|Kliknij przycisk **parametry** przycisk radiowy, aby użyć <xref:System.ServiceModel.Activities.ReceiveParametersContent>, którego oczekuje kontraktu danych. Użyj siatki danych, aby ustawić ogólnego zbiór <xref:System.Activities.OutArgument> których wartości są przypisane do parametrów zmiennych w przepływie pracy bieżącego par klucz/wartość.|  
  
 **Definicji zawartości** okno dialogowe jest używany przez **wysyłania**, **Receive**, **ReceiveAndSendReply**, i  **SendAndReceiveReply** projektantów. Uzyskiwanie dostępu do nich przypomina w każdym przypadku, a w przypadku odbierania służy tutaj, aby zilustrować procedurę.  
  
 **Receive** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zazwyczaj umieszczone. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Receive> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> Receive. Wybierz **Receive** projektanta działań i kliknij przycisk wielokropka, obok tekstu (zawartość) dla **zawartości** właściwość w siatce właściwości **definicji zawartości**wyświetlane okno dialogowe.  
  
 Zawartość może być określone w **komunikat** sekcji <xref:System.ServiceModel.Activities.ReceiveMessageContent> działania lub w ramach **parametru** sekcji <xref:System.ServiceModel.Activities.ReceiveParametersContent> działania.  
  
## <a name="see-also"></a>Zobacz też  
 [Pomoc interfejsu użytkownika Projektanta przepływu pracy](../workflow-designer/workflow-designer-ui-help.md)