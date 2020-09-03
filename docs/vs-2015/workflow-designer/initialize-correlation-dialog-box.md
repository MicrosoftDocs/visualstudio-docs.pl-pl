---
title: Okno dialogowe inicjowanie korelacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ab913027a6a992494dad609b98ab11dbc6ae61c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659050"
---
# <a name="initialize-correlation-dialog-box"></a>Inicjowanie korelacji, okno dialogowe
Okno dialogowe **Inicjowanie korelacji** służy [!INCLUDE[wfd1](../includes/wfd1-md.md)] do edytowania <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> właściwości <xref:System.ServiceModel.Activities.InitializeCorrelation> działania. [!INCLUDE[crdefault](../includes/crdefault-md.md)] temat [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) .

 W poniższej tabeli opisano elementy interfejsu użytkownika (UI) okna dialogowego **Inicjowanie korelacji** .

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**korelacja**|Wartość <xref:System.ServiceModel.Activities.CorrelationHandle> korelacji do zainicjowania.|
|**Zainicjuj**|Para klucz/wartość, która zawiera dane do zainicjowania. Odpowiada <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> właściwości. Przykładem prawidłowej pary klucz/wartość będzie klucz o nazwie "IDZamówienia" sparowany ze zmienną o nazwie IDZamówienia.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Aby uruchomić okno dialogowe inicjowanie korelacji

- Kliknij przycisk **Wyświetl** w projektancie działań **InitializeCorrelation** lub wybierz <xref:System.ServiceModel.Activities.InitializeCorrelation> działanie w [!INCLUDE[wfd2](../includes/wfd2-md.md)] , a następnie kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> właściwości w siatce właściwości.

## <a name="see-also"></a>Zobacz też
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)