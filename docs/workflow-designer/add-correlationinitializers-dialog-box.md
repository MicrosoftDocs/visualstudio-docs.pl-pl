---
title: Projektant przepływu pracy — Dodawanie CorrelationInitializers, okno dialogowe
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67dea88845ffbfab8350e4a1134e09436c95321b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860357"
---
# <a name="add-correlationinitializers-dialog-box"></a>Dodawanie CorrelationInitializers, okno dialogowe

**Dodaj inicjatory korelacji** okno dialogowe służy do konfigurowania w Projektancie przepływu pracy **CorrelationInitializers** właściwości <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply> działań. Aby uzyskać więcej informacji na temat Projektanci działań, które używają tego pola, zobacz [wysyłania](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), i [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) tematów.

Inicjatory korelacji w kolekcji określonej z tego okna dialogowego, można zainicjować następujących korelacji między działań dotyczących komunikatów:

- oparte na zapytaniach
- kontekst
- Kontekst wywołania zwrotnego
- "żądanie-odpowiedź"

W poniższej tabeli opisano elementy interfejsu użytkownika **Dodaj inicjatory korelacji** okno dialogowe:

|Element interfejsu użytkownika|Opis|
|-|-----------------|
|**Dodaj inicjator**|Kliknij przycisk **Dodaj inicjowanie** pole, aby dodać dodatkowe inicjatora do kolekcji.|
|**Typ korelace**|Określa typ inicjatora korelacji. Istnieją cztery typy do wyboru:<br /><br /> 1. Wywołanie zwrotne inicjatora korelacji, aby określić <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2. Kontekst inicjatora korelacji, aby określić <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3. Inicjator korelacji "żądanie-odpowiedź", aby określić <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4. Inicjator korelacji zapytania, aby określić <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Aby edytować **CorrelationType**<br /><br /> 1. Karta do określonego wiersza w **Dodaj inicjator** DataGrid.<br />2. Aby ustawić fokus na **CorrelationTypeComboBox**, naciśnij klawisz **Ctrl**+**kartę**.<br />3. Naciśnij klawisze Alt + Strzałka w dół, przeskoczyć do góry **ComboBox** i go edytować.|
|**Zapytania XPath**|Parą klucz/wartość, która zawiera zapytania, używany do wyodrębniania danych korelacji z komunikatów przychodzących i wychodzących. Ta lista jest prawidłowy tylko w przypadku korzystania z <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> typów.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Aby uruchomić okno dialogowe Dodaj inicjatory korelacji

 **Dodaj inicjatory korelacji** okno dialogowe jest używany przez **wysyłania**, **Receive**, **ReceiveAndSendReply**, i  **SendAndReceiveReply** projektantów. Uzyskiwanie dostępu do nich przypomina w każdym przypadku i przypadek, który obejmuje **Receive** projektanta jest używany w tym miejscu, aby zilustrować procedurę.

 **Receive** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy wszędzie tam, gdzie są umieszczone działań. Upuszczanie **Receive** tworzy projektanta działań <xref:System.ServiceModel.Activities.Receive> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> Receive. Wybierz **Receive** projektanta działań i kliknij przycisk wielokropka, obok tekstu (kolekcji) dla **CorrelationInitializers** właściwość w siatce właściwości **Dodaj Inicjatory korelacji** wyświetlane okno dialogowe.

## <a name="see-also"></a>Zobacz także

- [Dodaj korelacji, okno dialogowe](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Inicjowanie korelacji, okno dialogowe](../workflow-designer/initialize-correlation-dialog-box.md)