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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656937"
---
# <a name="correlateson-definition-dialog-box"></a>Definicja wyrażenia CorrelatesOn, okno dialogowe
Okno dialogowe **CorrelatesOn** służy [!INCLUDE[wfd1](../includes/wfd1-md.md)] do edytowania <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> właściwości <xref:System.ServiceModel.Activities.Receive> działania. [!INCLUDE[crdefault](../includes/crdefault-md.md)] temat [odbierania](../workflow-designer/receive-activity-designer.md) .

 Korelacja między <xref:System.ServiceModel.Activities.Receive> działaniami określa sposób, w jaki różne operacje usługi łączą się ze sobą w przepływie pracy.

 W poniższej tabeli opisano elementy interfejsu użytkownika (UI) okna dialogowego **CorrelatesOn** .

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**CorrelatesWith**|<xref:System.ServiceModel.Activities.CorrelationHandle>Jest on używany do kierowania wiadomości do odpowiedniego wystąpienia przepływu pracy.|
|**Zapytania XPath**|Para klucz/wartość, która zawiera zapytania używane do wyodrębniania danych korelacji z komunikatów przychodzących. Odpowiada <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> właściwości. Zapytania XPath są zawarte w <xref:System.ServiceModel.MessageQuerySet> obiekcie.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Aby uruchomić okno dialogowe CorrelatesOn
 Projektanta działań **odbioru** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, wszędzie tam gdzie działania są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Receive> działania z domyślnym <xref:System.Activities.Activity.DisplayName%2A> odbiorem. Wybierz projektanta działań **Odbierz** i kliknij przycisk wielokropka obok tekstu (kolekcji) dla właściwości **CorrelatesOn** w siatce właściwości okna dialogowego **Definicja CorrelatesOn** .

## <a name="see-also"></a>Zobacz też
 <xref:System.ServiceModel.Activities.Receive>Okno dialogowe Dodawanie [korelacji](../workflow-designer/initialize-correlation-dialog-box.md) okna [dialogowego CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md)