---
title: Okno dialogowe Dodawanie CorrelationInitializers | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1402b90dfc78068546b510ce6b85379b1695f47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672038"
---
# <a name="add-correlationinitializers-dialog-box"></a>Dodawanie CorrelationInitializers, okno dialogowe
Okno dialogowe **Dodawanie inicjatorów korelacji** służy [!INCLUDE[wfd1](../includes/wfd1-md.md)] do konfigurowania właściwości **CorrelationInitializers** <xref:System.ServiceModel.Activities.Send> działań,, <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> i <xref:System.ServiceModel.Activities.ReceiveReply> . [!INCLUDE[crabout](../includes/crabout-md.md)] Projektanci działań, którzy korzystają z tego pola, zobacz tematy dotyczące [wysyłania](../workflow-designer/send-activity-designer.md), [odbierania](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)i [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

 Inicjatory korelacji w kolekcji określonej za pomocą tego okna dialogowego mogą inicjować korelacje oparte na zapytaniach, kontekstach wywołania zwrotnego lub żądanie-odpowiedź między działaniami związanymi z obsługą komunikatów.

 W poniższej tabeli opisano elementy interfejsu użytkownika (UI) okna dialogowego **Dodaj inicjatory korelacji** .

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**Dodaj inicjator**|Kliknij pole **Dodaj inicjowanie** , aby dodać dodatkowy inicjator do kolekcji.|
|**Typ korelacji**|Określa typ inicjatora korelacji. Istnieją cztery typy do wyboru:<br /><br /> 1. inicjator korelacji wywołania zwrotnego, aby określić <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> .<br />2. inicjator korelacji kontekstu, aby określić <xref:System.ServiceModel.Activities.CorrelationInitializer> .<br />3. inicjator korelacji typu żądanie-odpowiedź, aby określić <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> .<br />4. inicjator korelacji zapytania, aby określić <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> .<br /><br /> Aby edytować wartość **korelacji**<br /><br /> 1. Tab do określonego wiersza w składniku DataGrid **Dodaj inicjatora** .<br />2. Naciśnij kombinację klawiszy CTRL + TAB, aby ustawić fokus na **CorrelationTypeComboBox**<br />3. Naciśnij kombinację klawiszy Alt + Strzałka w dół, aby wypróbować **pole kombi** i edytować je.|
|**Zapytania XPath**|Para klucz/wartość, która zawiera zapytania używane do wyodrębniania danych korelacji z komunikatów przychodzących i wychodzących. Ta lista jest prawidłowa tylko w przypadku korzystania z <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> typów.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Aby uruchomić okno dialogowe Dodawanie inicjatorów korelacji
 Okno dialogowe **Dodawanie inicjatorów korelacji** jest używane przez projektantów **wysyłania**, **odbierania**, **ReceiveAndSendReply**i **SendAndReceiveReply** . Dostęp do nich jest podobny w każdym przypadku, a przypadek, który obejmuje projektanta **odbioru** , jest używany tutaj do zilustrowania procedury.

 Projektanta działań **odbioru** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, wszędzie tam gdzie działania są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Receive> działania z domyślnym <xref:System.Activities.Activity.DisplayName%2A> odbiorem. Wybierz projektanta **działań i** kliknij przycisk wielokropka obok tekstu (kolekcji) dla właściwości **CorrelationInitializers** w siatce właściwości okna dialogowego **Dodaj inicjatory korelacji** do wyświetlenia.

## <a name="see-also"></a>Zobacz też
 [Inicjowanie korelacji, okno dialogowe](../workflow-designer/initialize-correlation-dialog-box.md)