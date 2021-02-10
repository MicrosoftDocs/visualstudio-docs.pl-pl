---
title: Projektant przepływu pracy — okno dialogowe Definicja CorrelatesOn
description: Dowiedz się, w jaki sposób można użyć okna dialogowego CorrelatesOn w Projektant przepływu pracy, aby edytować Właściwość CorrelatesOn działania Receive.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b4f371da2570d5573ce84c7e29393889202ae940
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955544"
---
# <a name="correlateson-definition-dialog-box"></a>Definicja wyrażenia CorrelatesOn, okno dialogowe

Okno dialogowe **CorrelatesOn** jest używane w Projektant przepływu pracy, aby edytować <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> Właściwość <xref:System.ServiceModel.Activities.Receive> działania. Aby uzyskać więcej informacji, zobacz [Odbierz projektanta działań](../workflow-designer/receive-activity-designer.md).

Korelacja między <xref:System.ServiceModel.Activities.Receive> działaniami określa sposób, w jaki różne operacje usługi łączą się ze sobą w przepływie pracy.

W poniższej tabeli opisano elementy interfejsu użytkownika (UI) okna dialogowego **CorrelatesOn** .

|Element interfejsu użytkownika|Opis|
|-|-----------------|
|**CorrelatesWith**|<xref:System.ServiceModel.Activities.CorrelationHandle>Jest on używany do kierowania wiadomości do odpowiedniego wystąpienia przepływu pracy.|
|**Zapytania XPath**|Para klucz/wartość, która zawiera zapytania używane do wyodrębniania danych korelacji z komunikatów przychodzących. Ta wartość odpowiada <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> właściwości. Zapytania XPath są zawarte w <xref:System.ServiceModel.MessageQuerySet> obiekcie.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Aby uruchomić okno dialogowe CorrelatesOn

Projektanta działań **odbioru** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam gdzie działania są zwykle umieszczane. Porzucenie projektanta działań powoduje utworzenie <xref:System.ServiceModel.Activities.Receive> działania z domyślnym <xref:System.Activities.Activity.DisplayName%2A> odbiorem. Aby otworzyć okno dialogowe **Definicja CorrelatesOn** , wybierz projektanta działań **Odbierz** , a następnie w siatce właściwości wybierz przycisk wielokropka obok tekstu kolekcji dla właściwości **CorrelatesOn** .

## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Activities.Receive>
- [Dodawanie CorrelationInitializers, okno dialogowe](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Inicjowanie korelacji, okno dialogowe](../workflow-designer/initialize-correlation-dialog-box.md)