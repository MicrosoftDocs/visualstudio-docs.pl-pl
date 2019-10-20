---
title: Projektant przepływu pracy — okno dialogowe Definicja CorrelatesOn
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 401f72f55f23779f7c6257437034a4ebc294d219
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650601"
---
# <a name="correlateson-definition-dialog-box"></a>Definicja wyrażenia CorrelatesOn, okno dialogowe

Okno dialogowe **CorrelatesOn** jest używane w Projektant przepływu pracy, aby edytować Właściwość <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> działania <xref:System.ServiceModel.Activities.Receive>. Aby uzyskać więcej informacji, zobacz [Odbierz projektanta działań](../workflow-designer/receive-activity-designer.md).

Korelacja między działaniami <xref:System.ServiceModel.Activities.Receive> określa, jak różne operacje usługi łączą się ze sobą w przepływie pracy.

W poniższej tabeli opisano elementy interfejsu użytkownika (UI) okna dialogowego **CorrelatesOn** .

|Element interfejsu użytkownika|Opis|
|-|-----------------|
|**CorrelatesWith**|@No__t_0, który jest używany do kierowania wiadomości do odpowiedniego wystąpienia przepływu pracy.|
|**Zapytania XPath**|Para klucz/wartość, która zawiera zapytania używane do wyodrębniania danych korelacji z komunikatów przychodzących. Ta wartość odpowiada właściwości <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>. Zapytania XPath są zawarte w obiekcie <xref:System.ServiceModel.MessageQuerySet>.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Aby uruchomić okno dialogowe CorrelatesOn

Projektanta działań **odbioru** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam gdzie działania są zwykle umieszczane. Porzucenie projektanta działań powoduje utworzenie działania <xref:System.ServiceModel.Activities.Receive> z domyślnym <xref:System.Activities.Activity.DisplayName%2A> odbierania. Aby otworzyć okno dialogowe **Definicja CorrelatesOn** , wybierz projektanta działań **Odbierz** , a następnie w siatce właściwości wybierz przycisk wielokropka obok tekstu kolekcji dla właściwości **CorrelatesOn** .

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activities.Receive>
- [Dodawanie CorrelationInitializers, okno dialogowe](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Inicjowanie korelacji, okno dialogowe](../workflow-designer/initialize-correlation-dialog-box.md)