---
title: '&lt; &gt; Projektant działań foreach T | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656656"
---
# <a name="foreachlttgt-activity-designer"></a>&lt; &gt; Projektant działań foreach T
<xref:System.Activities.Statements.ForEach%601>Działanie wykonuje działanie zawarte w jego <xref:System.Activities.Statements.ForEach%601.Body%2A> przypadku dla każdego elementu w określonej <xref:System.Activities.Statements.ForEach%601.Values%2A> kolekcji.

## <a name="foreacht-properties-in-the-workflow-designer"></a>\<T>Właściwości foreach w Projektant przepływu pracy
 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.ForEach%601> właściwości działania i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa <xref:System.Activities.Statements.ForEach%601> działania. Wartość domyślna to ForEach \<Int32> . Chociaż <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Prawda|Kolekcja elementów do iteracji. Aby ustawić <xref:System.Activities.Statements.ForEach%601.Values%2A> , wpisz [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] wyrażenie w polu **wartości** w projektancie działań **ForEach \<T> ** lub w siatce właściwości.|
|*Elementu TypeArgument*|Prawda|Typ elementów w <xref:System.Activities.Statements.ForEach%601.Values%2A> kolekcji określony przez parametr generyczny *T*. Domyślnie *elementu TypeArgument* jest ustawiona na **Int32**. Aby zmienić typ, należy zmienić wartość pola kombi *elementu TypeArgument* w siatce właściwości.|

 Domyślnie iterator pętli ma nazwę **element**. Można zmienić nazwę zmiennej iteratora w <xref:System.Activities.Statements.ForEach%601> projektancie działań. Iteratora pętli można używać w wyrażeniach w elemencie podrzędnym <xref:System.Activities.Statements.ForEach%601> działania.

## <a name="see-also"></a>Zobacz też
 [ParallelForEach \<T> ](../workflow-designer/parallelforeach-t-activity-designer.md) [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)