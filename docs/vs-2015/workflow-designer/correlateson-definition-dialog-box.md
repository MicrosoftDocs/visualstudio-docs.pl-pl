---
title: Definiowanie CorrelatesOn, okno dialogowe | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fd03e1a8615e75d3f00f79eb10b7a7ff97f0eb33
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977371"
---
# <a name="correlateson-definition-dialog-box"></a>Definicja wyrażenia CorrelatesOn, okno dialogowe
**CorrelatesOn** okno dialogowe jest używany w [!INCLUDE[wfd1](../includes/wfd1-md.md)] edytować <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> właściwość <xref:System.ServiceModel.Activities.Receive> działania. [!INCLUDE[crdefault](../includes/crdefault-md.md)] [Receive](../workflow-designer/receive-activity-designer.md) tematu.  
  
 Korelacja między <xref:System.ServiceModel.Activities.Receive> działania określa, jak różne usługi operations łączyć się ze sobą w przepływie pracy.  
  
 W poniższej tabeli opisano elementy interfejsu użytkownika **CorrelatesOn** okno dialogowe.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**CorrelatesWith**|<xref:System.ServiceModel.Activities.CorrelationHandle> Służący do rozsyłania wiadomości dla wystąpienia przepływu pracy odpowiednie.|  
|**Zapytania XPath**|Parą klucz/wartość, która zawiera zapytania, używany do wyodrębniania danych korelacji z komunikatów przychodzących. Odpowiada to <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> właściwości. Zapytania XPath są zawarte w <xref:System.ServiceModel.MessageQuerySet> obiektu.|  
  
## <a name="to-launch-the-correlateson-dialog-box"></a>Aby uruchomić okno dialogowe CorrelatesOn  
 **Receive** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zazwyczaj umieszczone. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Receive> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> Receive. Wybierz **Receive** projektanta działań i kliknij przycisk wielokropka, obok tekstu (kolekcji) dla **CorrelatesOn** właściwość w siatce właściwości **definice Vlastnosti Correlateson**  wyświetlane okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Activities.Receive>   
 [Dodawanie CorrelationInitializers, okno dialogowe](../workflow-designer/add-correlationinitializers-dialog-box.md)   
 [Inicjowanie korelacji, okno dialogowe](../workflow-designer/initialize-correlation-dialog-box.md)