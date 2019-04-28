---
title: Confirm, Projektant działań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 29635044eb4cca558d631ab959b1b4f5480dbdbe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977384"
---
# <a name="confirm-activity-designer"></a>Confirm, projektant działań
**Potwierdź** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Confirm> działania.  
  
## <a name="the-confirm-activity"></a>Potwierdź działanie  
 <xref:System.Activities.Statements.Confirm> Działania jawnie wywołuje <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> dla działania zawarte w <xref:System.Activities.Statements.CompensableActivity>. Jeśli <xref:System.Activities.Statements.Confirm> działanie nie jest używane w ramach <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, lub <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> z <xref:System.Activities.Statements.CompensableActivity>, a następnie należy określić <xref:System.Activities.Statements.Confirm.Target%2A> właściwości.  
  
 <xref:System.Activities.Statements.CompensationToken> Określony przez <xref:System.Activities.Statements.Compensate.Target%2A> udostępnia środki do jawnie potwierdzić, lub kompensacji <xref:System.Activities.Statements.CompensableActivity> po <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> została ukończona pomyślnie.  
  
### <a name="using-the-confirm-activity-designer"></a>Za pomocą Confirm, Projektant działań  
 **Potwierdź** projektanta działań można znaleźć w **transakcji** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karty w lewej części [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać **narzędzi** z **widoku** menu lub klawiszy CTRL + ALT + X.)  
  
 **Potwierdź** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zwyczajowo umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Confirm> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> o potwierdzenie. <xref:System.Activities.Activity.DisplayName%2A> Wartość może być edytowany w nagłówku **Potwierdź** projektanta działań lub **DisplayName** pola siatki właściwości.  
  
### <a name="the-confirm-properties"></a>Upewnij się, właściwości  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Confirm> właściwości i w tym artykule opisano, jak są używane w projektancie. <xref:System.Activities.Activity.DisplayName%2A> Właściwości można edytować w siatce właściwości lub na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, ale <xref:System.Activities.Statements.Confirm.Target%2A> właściwości muszą być edytowane w siatce właściwości.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalny przyjazna nazwa <xref:System.Activities.Statements.CancellationScope> działania. Wartość domyślna to potwierdzić.|  
|<xref:System.Activities.Statements.Confirm.Target%2A>|Prawda|Określa <xref:System.Activities.InArgument%601> zawierający <xref:System.Activities.Statements.CompensationToken> tego <xref:System.Activities.Statements.Confirm> działania.|  
  
## <a name="see-also"></a>Zobacz też  
 [Transakcji](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Wyrównania](../workflow-designer/compensate-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)