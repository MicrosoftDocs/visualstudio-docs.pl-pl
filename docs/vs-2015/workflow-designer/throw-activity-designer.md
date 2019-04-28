---
title: Throw, Projektant działań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: db909618971eeab2d92506d1c29b06290aa9263b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976618"
---
# <a name="throw-activity-designer"></a>Throw, projektant działań
**Throw** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Throw> działania.  
  
## <a name="the-throw-activity"></a>Działanie Throw  
 <xref:System.Activities.Statements.Throw> Działanie zgłasza wyjątek.  
  
### <a name="using-the-throw-activity-designer"></a>Za pomocą projektanta działań Throw  
 **Throw** projektanta działań można znaleźć w **obsługę błędów** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karty w lewej części [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać **narzędzi** z **widoku** menu lub klawiszy CTRL + ALT + X.)  
  
 **Throw** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zwyczajowo umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Throw> działanie przy użyciu domyślnego **DisplayName** z Throw. <xref:System.Activities.Activity.DisplayName%2A> Wartość może być edytowana w nagłówku **Throw** projektanta działań lub **DisplayName** pola siatki właściwości. <xref:System.Activities.Statements.Throw.Exception%2A> Można edytować właściwości, w siatce właściwości.  
  
### <a name="the-throw-properties"></a>Właściwości Throw  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Throw> właściwości i w tym artykule opisano, jak są używane w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalny przyjazna nazwa <xref:System.Activities.Statements.Throw> działania. Wartość domyślna to Throw.|  
|<xref:System.Activities.Statements.Throw.Exception%2A>|Prawda|Wyjątek do zgłoszenia. Ten wyjątek musi pochodzić od klasy <xref:System.Exception>. Aby określić wyjątek, wpisz wyrażenie języka Visual Basic w siatce właściwości.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcja](../workflow-designer/collection-activity-designers.md)   
 [Zgłoś ponownie](../workflow-designer/rethrow-activity-designer.md)   
 [Throw, Projektant działań](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)