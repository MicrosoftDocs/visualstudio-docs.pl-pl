---
title: Okno dialogowe Projektant przepływu pracy inicjowania korelacji
description: Dowiedz się, jak można użyć okna dialogowego inicjowanie korelacji w Projektant przepływu pracy, aby edytować Właściwość Initalizecorrelation działania InitializeCorrelation.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a35911fef39315580f402e174b0f32d443a33cf
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437804"
---
# <a name="initialize-correlation-dialog-box"></a>Inicjowanie korelacji, okno dialogowe

Okno dialogowe **Inicjowanie korelacji** jest używane w Projektant przepływu pracy, aby edytować <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> Właściwość <xref:System.ServiceModel.Activities.InitializeCorrelation> działania. Aby uzyskać więcej informacji, zobacz [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

W poniższej tabeli opisano elementy interfejsu użytkownika (UI) okna dialogowego **Inicjowanie korelacji** :

|Element interfejsu użytkownika|Opis|
|-|-----------------|
|**korelacja**|Wartość <xref:System.ServiceModel.Activities.CorrelationHandle> korelacji do zainicjowania.|
|**Zainicjuj**|Para klucz/wartość, która zawiera dane do zainicjowania. Ta wartość odpowiada <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> właściwości. Przykładem prawidłowej pary klucz/wartość jest klucz o nazwie "IDZamówienia" sparowany ze zmienną o nazwie IDZamówienia.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Aby uruchomić okno dialogowe inicjowanie korelacji

Kliknij przycisk **Wyświetl** w projektancie działań **InitializeCorrelation** lub wybierz <xref:System.ServiceModel.Activities.InitializeCorrelation> działanie w Projektant przepływu pracy. Następnie kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> właściwości w siatce właściwości.

## <a name="see-also"></a>Zobacz też

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
