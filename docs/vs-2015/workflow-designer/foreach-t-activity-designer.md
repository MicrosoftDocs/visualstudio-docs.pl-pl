---
title: Instrukcja ForEach&lt;T&gt; projektanta działań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 97732b92c5a90334917ad4e74667f88d605b647d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54787832"
---
# <a name="foreachlttgt-activity-designer"></a>Instrukcja ForEach&lt;T&gt; Projektant działań
<xref:System.Activities.Statements.ForEach%601> Działanie wykonuje działania zawarte w jego <xref:System.Activities.Statements.ForEach%601.Body%2A> dla każdego elementu w określonej <xref:System.Activities.Statements.ForEach%601.Values%2A> kolekcji.  
  
## <a name="foreacht-properties-in-the-workflow-designer"></a>Instrukcja ForEach\<T > właściwości w Projektancie przepływu pracy  
 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.ForEach%601> właściwości działań i informacje dotyczące używania ich w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.ForEach%601> działania. Wartość domyślna to ForEach\<Int32 >. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest bezwzględnie konieczne, jest najlepszym rozwiązaniem, aby użyć jednego.|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Prawda|Kolekcja elementów do iteracji. Aby ustawić <xref:System.Activities.Statements.ForEach%601.Values%2A>, wpisz [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] wyrażenia w **wartości** polu na **ForEach\<T >** działanie projektanta lub w siatce właściwości.|  
|*TypeArgument*|Prawda|Typ elementów w <xref:System.Activities.Statements.ForEach%601.Values%2A> kolekcji określonej przez parametr ogólny *T*. Domyślnie *elementu typeargument w języku* ustawiono **Int32**. Aby zmienić typ, zmień wartość *elementu typeargument w języku* pola kombi w siatce właściwości.|  
  
 Domyślnie, nosi nazwę iteratora pętli **elementu**. Można zmienić nazwy zmiennej iteratora w <xref:System.Activities.Statements.ForEach%601> projektanta działań. Iteratora pętli można używać w wyrażeniach w elementy podrzędne <xref:System.Activities.Statements.ForEach%601> działania.  
  
## <a name="see-also"></a>Zobacz też  
 [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)