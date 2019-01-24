---
title: Persist, Projektant działań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f87997178f98e9e632b756b5a4440c19544b5c86
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779383"
---
# <a name="persist-activity-designer"></a>Persist, projektant działań
**Utrwalanie** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Persist> działania.  
  
## <a name="the-persist-activity"></a>Utrwalanie działania  
 <xref:System.Activities.Statements.Persist> Działanie zapisuje przepływ pracy na dysku, jeśli jest to możliwe. <xref:System.Activities.Statements.Persist> Działania nie można wykonać w strefie bez trwałości, jak na przykład w ramach <xref:System.Activities.Statements.TransactionScope> działania. Jeśli używasz <xref:System.Activities.Statements.Persist> działań w zakresie bez trwałości, zgłaszany jest wyjątek w czasie wykonywania.  
  
### <a name="using-the-persist-activity-designer"></a>Za pomocą Persist, Projektant działań  
 **Utrwalanie** projektanta działań można znaleźć w **środowiska uruchomieniowego** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** Karta (można także wybrać **przybornika** z **widoku** menu lub klawiszy CTRL + ALT + X.)  
  
 **Utrwalanie** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zwyczajowo umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Persist> działanie przy użyciu domyślnego **DisplayName** z utrwalanie. <xref:System.Activities.Activity.DisplayName%2A> Mogą być edytowane w nagłówku **utrwalanie** projektanta działań lub **DisplayName** pola siatki właściwości.  
  
### <a name="the-persist-properties"></a>Utrwalanie właściwości  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Persist> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości i niektóre z nich mogą być edytowane [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.Persist> działania. Wartość domyślna to utrwalanie. Chociaż nazwa wyświetlana nie jest bezwzględnie konieczne, jest najlepszym rozwiązaniem, aby użyć nazwy wyświetlanej.|  
  
## <a name="see-also"></a>Zobacz też  
 [Środowisko uruchomieniowe](../workflow-designer/runtime-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)