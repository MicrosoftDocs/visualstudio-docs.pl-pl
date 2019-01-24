---
title: InitializeCorrelation, Projektant działań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 383a2e892c8f0962ab8c09d5e8984d3cc570ebaa
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54783231"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation, projektant działań
**InitializeCorrelation** projektanta działań służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.InitializeCorrelation> działania, który jest używany do ustanawiania korelacja komunikatów przed wysyłać ani odbierać z nich.  
  
## <a name="the-initializecorrelation-activity"></a>Działanie InitializeCorrelation  
 <xref:System.ServiceModel.Activities.InitializeCorrelation> To działanie służy do zainicjowania korelacji bez wysyłania i odbierania wiadomości. Zazwyczaj korelacji jest inicjowany przy wysyłaniu lub odbieraniu wiadomości. Jeśli przed wysłanego lub odebranego komunikatu, należy ustanowić korelacji, użyj <xref:System.ServiceModel.Activities.InitializeCorrelation> zainicjować korelacji.  
  
### <a name="using-the-initializecorrelation-activity-designer"></a>Za pomocą InitializeCorrelation, Projektant działań  
 **InitializeCorrelation** projektanta działań można znaleźć w **komunikatów** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**  karcie [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać **narzędzi** z **widoku** menu lub klawiszy CTRL + ALT + X.)  
  
 **InitializeCorrelation** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.InitializeCorrelation> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> z InitializeCorrelation.The <xref:System.Activities.Activity.DisplayName%2A> mogą być edytowane w nagłówku **InitializeCorrelation** projektanta działań lub  **DisplayName** pole **właściwości** okna.  
  
 <xref:System.ServiceModel.Activities.CorrelationHandle> Może być Określa **korelacji** pole **właściwości** okno na **InitializeCorrelation** powierzchni projektanta działań.  
  
 Klikając przycisk wielokropka, oprócz **CorrelationData** pole **właściwości** okna lub "Widok..." podpowiedzi tekstowe na **InitializeCorrelation** Wyświetla powierzchni projektanta działań **inicjowanie korelacji** okno dialogowe, w którym można określić dojście korelacji i pary klucz wartość, używany do go zainicjować. [!INCLUDE[crabout](../includes/crabout-md.md)] za pomocą tego okna dialogowego zobacz [okno dialogowe Edytor kolekcji typów](../workflow-designer/type-collection-editor-dialog-box.md) tematu.  
  
### <a name="the-initializecorrelation-properties"></a>Właściwości InitializeCorrelation  
 W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.InitializeCorrelation> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w **właściwości** oknie lub na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.ServiceModel.Activities.InitializeCorrelation> działania. Wartość domyślna to InitializeCorrelation.<br /><br /> Mimo że użycie wartości innych niż domyślne przyjazna <xref:System.Activities.Activity.DisplayName%2A> nie jest bezwzględnie konieczne jest najlepszym rozwiązaniem jest użycie tych wartości.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> Używanego do kojarzenia działań przepływu pracy w korelacji.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Słownik danych korelacji, który odnosi się komunikaty do wystąpienia przepływu pracy.<br /><br /> Użyj **inicjowanie korelacji** okno dialogowe konfigurowania <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. [!INCLUDE[crabout](../includes/crabout-md.md)] Użycie tego okna dialogowego zobacz [okno dialogowe Edytor kolekcji typów](../workflow-designer/type-collection-editor-dialog-box.md) tematu.|  
  
## <a name="see-also"></a>Zobacz też  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Odbieranie](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Wyślij](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)