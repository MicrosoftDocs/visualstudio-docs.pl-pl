---
title: '@No__t_0T ForEach &gt; Projektant działań | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d41451ada0e37f953e9d611a4e3733815a9d347b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656656"
---
# <a name="foreachlttgt-activity-designer"></a>@No__t_0T ForEach — Projektant działań &gt;
Działanie <xref:System.Activities.Statements.ForEach%601> wykonuje działanie zawarte w jego <xref:System.Activities.Statements.ForEach%601.Body%2A> dla każdego elementu w określonej kolekcji <xref:System.Activities.Statements.ForEach%601.Values%2A>.

## <a name="foreacht-properties-in-the-workflow-designer"></a>@No__t_0T ForEach > właściwości w Projektant przepływu pracy
 W poniższej tabeli przedstawiono najbardziej przydatne właściwości działania <xref:System.Activities.Statements.ForEach%601> i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa działania <xref:System.Activities.Statements.ForEach%601>. Wartość domyślna to ForEach \<Int32 >. Mimo że wartość <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Oznacza|Kolekcja elementów do iteracji. Aby ustawić <xref:System.Activities.Statements.ForEach%601.Values%2A>, wpisz wyrażenie [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] w polu **wartości** w projektancie aktywności **\<T foreach >** lub w siatce właściwości.|
|*Elementu TypeArgument*|Oznacza|Typ elementów w kolekcji <xref:System.Activities.Statements.ForEach%601.Values%2A> określonej przez parametr generyczny *t*. Domyślnie *elementu TypeArgument* jest ustawiona na **Int32**. Aby zmienić typ, należy zmienić wartość pola kombi *elementu TypeArgument* w siatce właściwości.|

 Domyślnie iterator pętli ma nazwę **element**. Nazwę zmiennej iteratora można zmienić w projektancie działania <xref:System.Activities.Statements.ForEach%601>. Iteratora pętli można używać w wyrażeniach w elemencie podrzędnym działania <xref:System.Activities.Statements.ForEach%601>.

## <a name="see-also"></a>Zobacz też
 [ParallelForEach \<T >](../workflow-designer/parallelforeach-t-activity-designer.md) [przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)