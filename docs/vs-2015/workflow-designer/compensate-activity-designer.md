---
title: Compensate, Projektant działań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0f643770482c2d01f3f091157e63f8e987853da5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977190"
---
# <a name="compensate-activity-designer"></a>Compensate, projektant działań
**Compensate** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Compensate> działania.  
  
## <a name="the-compensate-activity"></a>Kompensacji działania  
 <xref:System.Activities.Statements.Compensate> Działania jawnie wywołuje <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> dla działania zawarte w <xref:System.Activities.Statements.CompensableActivity>. Jeśli <xref:System.Activities.Statements.Compensate> działanie nie jest używane w ramach <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, lub <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> z <xref:System.Activities.Statements.CompensableActivity>, a następnie należy określić <xref:System.Activities.Statements.Compensate.Target%2A> właściwości.  
  
 <xref:System.Activities.Statements.CompensationToken> Określony przez <xref:System.Activities.Statements.Compensate.Target%2A> udostępnia środki do jawnie potwierdzić, lub kompensacji <xref:System.Activities.Statements.CompensableActivity> po <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> została ukończona pomyślnie.  
  
### <a name="using-the-compensate-activity-designer"></a>Za pomocą Compensate, Projektant działań  
 **Compensate** projektanta działań można znaleźć w **transakcji** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** karty w lewej części [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać **narzędzi** z **widoku** menu lub klawiszy CTRL + ALT + X.)  
  
 **Compensate** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zwyczajowo umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Compensate> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> z Compensate. <xref:System.Activities.Activity.DisplayName%2A> Wartość może być edytowana w nagłówku **Compensate** projektanta działań lub **DisplayName** pola siatki właściwości.  
  
### <a name="the-compensate-properties"></a>Kompensacji właściwości  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.CancellationScope> właściwości i w tym artykule opisano, jak są używane w projektancie. <xref:System.Activities.Activity.DisplayName%2A> Właściwości można edytować w siatce właściwości lub na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, ale <xref:System.Activities.Statements.Compensate.Target%2A> właściwości muszą być edytowane w siatce właściwości.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalny przyjazna nazwa <xref:System.Activities.Statements.Compensate> działania. Wartość domyślna to Compensate.|  
|<xref:System.Activities.Statements.Compensate.Target%2A>|Prawda|Określa <xref:System.Activities.InArgument%601> zawierający <xref:System.Activities.Statements.CompensationToken> tego <xref:System.Activities.Statements.Compensate> działania.|  
  
## <a name="see-also"></a>Zobacz też  
 [Transakcji](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate, Projektant działań](../workflow-designer/compensate-activity-designer.md)   
 [Upewnij się](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)