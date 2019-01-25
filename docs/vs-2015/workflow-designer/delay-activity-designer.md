---
title: Opóźnienie, Projektant działań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 528317a97a9b2582442dacfcf9ba8a35943736e8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805084"
---
# <a name="delay-activity-designer"></a>Delay, projektant działań
**Opóźnienie** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Delay> działania.  
  
## <a name="the-delay-activity"></a>Działanie opóźnienia  
 <xref:System.Activities.Statements.Delay> Działania opóźnia wykonywania przepływu pracy przez określony przedział czasu.  
  
### <a name="using-the-delay-activity-designer"></a>Za pomocą Delay, Projektant działań  
 **Opóźnienie** projektanta działań można znaleźć w **podstawowych** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karcie [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać **narzędzi** z **widoku** menu lub klawiszy CTRL + ALT + X.)  
  
 **Opóźnienie** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zwyczajowo umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Delay> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> z opóźnieniem. <xref:System.Activities.Activity.DisplayName%2A> Mogą być edytowane w nagłówku **opóźnienie** projektanta działań lub **DisplayName** pola siatki właściwości.  
  
### <a name="the-delay-properties"></a>Właściwości opóźnienia  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Delay> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości i ich niektóre mogą być edytowane w [!INCLUDE[wfd2](../includes/wfd2-md.md)]powierzchni projektowej.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.Delay> działania. Wartość domyślna to opóźnienie. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest bezwzględnie konieczne, jest najlepszym rozwiązaniem, aby użyć jednego.|  
|<xref:System.Activities.Statements.Delay.Duration%2A>|Prawda|Ilość czasu, opóźnienie przepływu pracy. Ta właściwość jest ustawiona w siatce właściwości. Wpisz jeden literał <xref:System.TimeSpan> w formacie 00:00:00 lub wyrażenie języka Visual Basic, aby określić ilość czasu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy podstawowe](../workflow-designer/primitives-activity-designers.md)   
 [Przypisz](../workflow-designer/assign-activity-designer.md)   
 [DELAY, Projektant działań](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)