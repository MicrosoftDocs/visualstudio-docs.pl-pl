---
title: Projektant przepływu pracy — inicjowanie korelacji, okno dialogowe
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51f001e053b0c2fdfe892175b00ed3f39dc6f1b4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829764"
---
# <a name="initialize-correlation-dialog-box"></a>Inicjowanie korelacji, okno dialogowe

**Inicjowanie korelacji** okno dialogowe jest używany w Projektancie przepływu pracy do edytowania <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> właściwość <xref:System.ServiceModel.Activities.InitializeCorrelation> działania. Aby uzyskać więcej informacji, zobacz [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

W poniższej tabeli opisano elementy interfejsu użytkownika **inicjowanie korelacji** okno dialogowe:

|Element interfejsu użytkownika|Opis|
|-|-----------------|
|**Korelacja**|<xref:System.ServiceModel.Activities.CorrelationHandle> Korelacji, aby zainicjować.|
|**Inicializace zapnuta**|Parą klucz/wartość, która zawiera dane do zainicjowania. Ta wartość odpowiada <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> właściwości. Przykładem parę prawidłowy klucz/wartość jest klucz o nazwie "OrderID", skojarzone ze zmienną o nazwie OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Aby uruchomić okno dialogowe Inicjowanie korelacji

Kliknij przycisk **widoku** na **InitializeCorrelation** działanie projektanta lub wybierz <xref:System.ServiceModel.Activities.InitializeCorrelation> działania w Projektancie przepływu pracy. Następnie kliknij przycisk oznaczony wielokropkiem obok <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> właściwość w siatce właściwości.

## <a name="see-also"></a>Zobacz także

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)