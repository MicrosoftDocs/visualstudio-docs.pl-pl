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
ms.openlocfilehash: c4f788a69d2be5aa7125c4ca19cb2cab4bf05a04
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54800841"
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
 [Dodaj korelacji, okno dialogowe](http://msdn.microsoft.com/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [Inicjowanie korelacji, okno dialogowe](../workflow-designer/initialize-correlation-dialog-box.md)