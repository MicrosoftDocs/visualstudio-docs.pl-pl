---
title: Dodawanie CorrelationInitializers, okno dialogowe | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 73fd7168124e75276427b711ad2c21f2f84994d6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782642"
---
# <a name="add-correlationinitializers-dialog-box"></a>Dodawanie CorrelationInitializers, okno dialogowe
**Dodaj inicjatory korelacji** okno dialogowe jest używany w [!INCLUDE[wfd1](../includes/wfd1-md.md)] skonfigurować **CorrelationInitializers** właściwości <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply> działań. [!INCLUDE[crabout](../includes/crabout-md.md)] Projektanci działań, które używają tego pola, zobacz [wysyłania](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), i [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) tematów.  
  
 Inicjatory korelacji w kolekcji określonej z tego okna dialogowego można zainicjować oparte na zapytaniach kontekstu, wywołania zwrotnego kontekstu lub "żądanie-odpowiedź" korelacji między działań dotyczących komunikatów.  
  
 W poniższej tabeli opisano elementy interfejsu użytkownika **Dodaj inicjatory korelacji** okno dialogowe.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Dodaj inicjator**|Kliknij przycisk **Dodaj inicjowanie** pole, aby dodać dodatkowe inicjatora do kolekcji.|  
|**Typ korelace**|Określa typ inicjatora korelacji. Istnieją cztery typy do wyboru:<br /><br /> 1.  Wywołanie zwrotne inicjatora korelacji, aby określić <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2.  Kontekst inicjatora korelacji, aby określić <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3.  Inicjator korelacji "żądanie-odpowiedź", aby określić <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4.  Inicjator korelacji zapytania, aby określić <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Aby edytować **CorrelationType**<br /><br /> 1.  Karta do określonego wiersza w **Dodaj inicjator** DataGrid.<br />2.  Naciśnij klawisze Ctrl + Tab, aby ustawić fokus na **CorrelationTypeComboBox**<br />3.  Naciśnij klawisze Alt + Strzałka w dół, przeskoczyć do góry **ComboBox** i go edytować.|  
|**Zapytania XPath**|Parą klucz/wartość, która zawiera zapytania, używany do wyodrębniania danych korelacji z komunikatów przychodzących i wychodzących. Ta lista jest prawidłowy tylko w przypadku korzystania z <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> typów.|  
  
## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Aby uruchomić okno dialogowe Dodaj inicjatory korelacji  
 **Dodaj inicjatory korelacji** okno dialogowe jest używany przez **wysyłania**, **Receive**, **ReceiveAndSendReply**, i  **SendAndReceiveReply** projektantów. Uzyskiwanie dostępu do nich przypomina w każdym przypadku i przypadek, który obejmuje **Receive** Projektant jest użycie tutaj, aby zilustrować procedurę.  
  
 **Receive** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zazwyczaj umieszczone. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Receive> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> Receive. Wybierz **Receive** projektanta działań i kliknij przycisk wielokropka, obok tekstu (kolekcji) dla **CorrelationInitializers** właściwość w siatce właściwości **Dodaj Inicjatory korelacji** wyświetlane okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodaj korelacji, okno dialogowe](http://msdn.microsoft.com/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [Inicjowanie korelacji, okno dialogowe](../workflow-designer/initialize-correlation-dialog-box.md)