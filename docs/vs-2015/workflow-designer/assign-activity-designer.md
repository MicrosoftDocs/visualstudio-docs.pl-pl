---
title: Assign, Projektant działań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 111f53ec5b427207a6bde5d590cf8f1c908ff130
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766129"
---
# <a name="assign-activity-designer"></a>Assign, projektant działań
**Przypisać** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Assign> działania.  
  
## <a name="the-assign-activity"></a>Przypisywania działania  
 <xref:System.Activities.Statements.Assign> Działania przypisuje wartość do zmiennej lub argumentu.  
  
### <a name="using-the-assign-activity-designer"></a>Za pomocą Przypisz Projektant działań  
 **Przypisać** projektanta działań można znaleźć w **podstawowych** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karty (opcjonalnie zaznacz **przybornika** z **widoku** menu lub klawiszy CTRL + ALT + X.)  
  
 **Przypisać** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni gdziekolwiek działań są zwyczajowo umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Assign> działanie przy użyciu domyślnego **DisplayName** z przypisania. <xref:System.Activities.Activity.DisplayName%2A> Mogą być edytowane w nagłówku **przypisać** projektanta działań lub **DisplayName** pola siatki właściwości.  
  
### <a name="the-assign-properties"></a>Przypisz właściwości  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Assign> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości i niektóre z nich mogą być edytowane [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.Assign> działania. Wartość domyślna to przypisanie. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest bezwzględnie konieczne, jest najlepszym rozwiązaniem, aby użyć jednego.|  
|<xref:System.Activities.Statements.Assign.To%2A>|Prawda|Zmiennej lub argumentu, do którego <xref:System.Activities.Statements.Assign.Value%2A> jest przypisany. Musi to być prawidłowym identyfikatorem języka Visual Basic. Aby ustawić właściwości, wpisz wyrażenie języka Visual Basic w **do** polu na **przypisać** działanie projektanta lub w siatce właściwości.|  
|<xref:System.Activities.Statements.Assign.Value%2A>|Prawda|Wartość, która jest przypisana do zmiennej. Aby ustawić <xref:System.Activities.Statements.Assign.Value%2A>, wpisz wyrażenie języka Visual Basic w **wartość** polu na **przypisać** działanie projektanta lub w siatce właściwości.|  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy podstawowe](../workflow-designer/primitives-activity-designers.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)