---
title: WriteLine, Projektant działań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 591ecf53e04eaff115d45e1358f385a009ab29f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855229"
---
# <a name="writeline-activity-designer"></a>WriteLine, projektant działań
**WriteLine** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.WriteLine> działania.  
  
## <a name="the-writeline-activity"></a>Działanie WriteLine  
 <xref:System.Activities.Statements.WriteLine> Działanie zapisuje tekst na określony <xref:System.IO.TextWriter> obiektu. Jeśli nie <xref:System.IO.TextWriter> jest określony, <xref:System.Activities.Statements.WriteLine> zapisuje tekst w konsoli.  
  
### <a name="using-the-writeline-activity-designer"></a>Za pomocą WriteLine, Projektant działań  
 **WriteLine** projektanta działań można znaleźć w **podstawowych** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karcie [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać **narzędzi** z **widoku** menu lub klawiszy CTRL + ALT + X.)  
  
 **WriteLine** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zwyczajowo umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.WriteLine> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> z WriteLine. <xref:System.Activities.Activity.DisplayName%2A> Mogą być edytowane w nagłówku **WriteLine** projektanta działań lub **DisplayName** pola siatki właściwości.  
  
### <a name="the-writeline-properties"></a>Właściwości WriteLine  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.WriteLine> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości i niektóre z nich mogą być edytowane [!INCLUDE[wfd2](../includes/wfd2-md.md)]powierzchni projektowej.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.WriteLine> działania. Wartość domyślna to WriteLine. Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest bezwzględnie konieczne jest najlepszym rozwiązaniem jest użycie jednego.|  
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Tekst do zapisu. Aby ustawić właściwości, wpisz wyrażenie języka Visual Basic w **tekstu** polu na **WriteLine** działanie projektanta lub w siatce właściwości.|  
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|<xref:System.IO.TextWriter> Do której <xref:System.Activities.Statements.WriteLine> zapisuje <xref:System.Activities.Statements.WriteLine.Text%2A>. Wartość domyślna to konsoli.|  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy podstawowe](../workflow-designer/primitives-activity-designers.md)   
 [Przypisz](../workflow-designer/assign-activity-designer.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)