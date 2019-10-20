---
title: Okno dialogowe Definicja CorrelatesOn | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2a9a6f7ec6b8bf246ebfc03c166780b229e1aee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656937"
---
# <a name="correlateson-definition-dialog-box"></a>Definicja wyrażenia CorrelatesOn, okno dialogowe
Okno dialogowe **CorrelatesOn** jest używane w [!INCLUDE[wfd1](../includes/wfd1-md.md)], aby edytować Właściwość <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> działania <xref:System.ServiceModel.Activities.Receive>. [!INCLUDE[crdefault](../includes/crdefault-md.md)] temat [odbierania](../workflow-designer/receive-activity-designer.md) .

 Korelacja między działaniami <xref:System.ServiceModel.Activities.Receive> określa, jak różne operacje usługi łączą się ze sobą w przepływie pracy.

 W poniższej tabeli opisano elementy interfejsu użytkownika (UI) okna dialogowego **CorrelatesOn** .

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**CorrelatesWith**|@No__t_0, który jest używany do kierowania wiadomości do odpowiedniego wystąpienia przepływu pracy.|
|**Zapytania XPath**|Para klucz/wartość, która zawiera zapytania używane do wyodrębniania danych korelacji z komunikatów przychodzących. Odpowiada właściwości <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>. Zapytania XPath są zawarte w obiekcie <xref:System.ServiceModel.MessageQuerySet>.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Aby uruchomić okno dialogowe CorrelatesOn
 Projektanta działań **odbioru** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchnię, wszędzie tam gdzie działania są zwykle umieszczane. Spowoduje to utworzenie działania <xref:System.ServiceModel.Activities.Receive> przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> odbierania. Wybierz projektanta działań **Odbierz** i kliknij przycisk wielokropka obok tekstu (kolekcji) dla właściwości **CorrelatesOn** w siatce właściwości okna dialogowego **Definicja CorrelatesOn** .

## <a name="see-also"></a>Zobacz też
 okno dialogowe [CorrelationInitializers Dodawanie](../workflow-designer/add-correlationinitializers-dialog-box.md) [korelacji](../workflow-designer/initialize-correlation-dialog-box.md) okna dialogowego <xref:System.ServiceModel.Activities.Receive>