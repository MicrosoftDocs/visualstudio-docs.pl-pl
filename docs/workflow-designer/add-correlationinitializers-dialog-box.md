---
title: Okno dialogowe Dodawanie CorrelationInitializers
description: Dowiedz się, jak za pomocą okna dialogowego Dodawanie inicjatorów korelacji w Projektant przepływu pracy skonfigurować właściwości CorrelationInitializers działań wysyłania, odbierania i działania SendReply.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e5822d1dc79835dd6fdcc3a70c3392dbd3d1aab
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996360"
---
# <a name="add-correlationinitializers-dialog-box"></a>Dodawanie CorrelationInitializers, okno dialogowe

Okno dialogowe **Dodawanie inicjatorów korelacji** jest używane w Projektant przepływu pracy do konfigurowania właściwości **CorrelationInitializers** <xref:System.ServiceModel.Activities.Send> działań,, <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> i <xref:System.ServiceModel.Activities.ReceiveReply> . Aby uzyskać więcej informacji na temat projektantów działań, które używają tego pola, zobacz tematy dotyczące [wysyłania](../workflow-designer/send-activity-designer.md), [odbierania](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)i [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

Inicjatory korelacji w kolekcji określonej za pomocą tego okna dialogowego mogą inicjować następujące korelacje między działaniami związanymi z obsługą komunikatów:

- oparte na zapytaniach
- kontekst
- kontekst wywołania zwrotnego
- żądanie-odpowiedź

W poniższej tabeli opisano elementy interfejsu użytkownika (UI) okna dialogowego **Dodaj inicjatory korelacji** :

|Element interfejsu użytkownika|Opis|
|-|-----------------|
|**Dodaj inicjator**|Kliknij pole **Dodaj inicjowanie** , aby dodać dodatkowy inicjator do kolekcji.|
|**Typ korelacji**|Określa typ inicjatora korelacji. Istnieją cztery typy do wyboru:<br /><br /> 1. inicjator korelacji wywołania zwrotnego, aby określić <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> .<br />2. inicjator korelacji kontekstu, aby określić <xref:System.ServiceModel.Activities.CorrelationInitializer> .<br />3. inicjator korelacji typu żądanie-odpowiedź, aby określić <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> .<br />4. inicjator korelacji zapytania, aby określić <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> .<br /><br /> Aby edytować wartość **korelacji**<br /><br /> 1. Tab do określonego wiersza w składniku DataGrid **Dodaj inicjatora** .<br />2. Aby ustawić fokus na **CorrelationTypeComboBox**, naciśnij klawisz **Ctrl** + **Tab**.<br />3. Naciśnij kombinację klawiszy Alt + Strzałka w dół, aby wypróbować **pole kombi** i edytować je.|
|**Zapytania XPath**|Para klucz/wartość, która zawiera zapytania używane do wyodrębniania danych korelacji z komunikatów przychodzących i wychodzących. Ta lista jest prawidłowa tylko w przypadku korzystania z <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> typów.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Aby uruchomić okno dialogowe Dodawanie inicjatorów korelacji

 Okno dialogowe **Dodawanie inicjatorów korelacji** jest używane przez projektantów **wysyłania**, **odbierania**, **ReceiveAndSendReply** i **SendAndReceiveReply** . Dostęp do nich jest podobny w każdym przypadku, a przypadek, który obejmuje projektanta **odbioru** , jest używany tutaj do zilustrowania procedury.

 Projektanta działań **odbioru** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam, gdzie są umieszczone działania. Porzucenie projektanta działań **Odbierz** powoduje utworzenie <xref:System.ServiceModel.Activities.Receive> działania z domyślnym <xref:System.Activities.Activity.DisplayName%2A> odbiorem. Wybierz projektanta **działań i** kliknij przycisk wielokropka obok tekstu (kolekcji) dla właściwości **CorrelationInitializers** w siatce właściwości okna dialogowego **Dodaj inicjatory korelacji** do wyświetlenia.

## <a name="see-also"></a>Zobacz też

- [Inicjowanie korelacji, okno dialogowe](../workflow-designer/initialize-correlation-dialog-box.md)
