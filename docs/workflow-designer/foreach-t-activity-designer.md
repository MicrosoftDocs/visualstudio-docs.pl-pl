---
title: Projektant przepływu pracy-ForEach&lt;T&gt; działanie projektanta aktywności
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30d43351211a6ff857630b47f05be77e27bd7951
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593918"
---
# <a name="foreachlttgt-activity-designer"></a>&gt; ForEach&lt;, Projektant działań

Działanie <xref:System.Activities.Statements.ForEach%601> wykonuje działanie zawarte w jego <xref:System.Activities.Statements.ForEach%601.Body%2A> dla każdego elementu w określonej kolekcji <xref:System.Activities.Statements.ForEach%601.Values%2A>.

## <a name="foreacht-properties-in-the-workflow-designer"></a>Właściwości ForEach < T\> w Projektant przepływu pracy

W poniższej tabeli przedstawiono najbardziej przydatne właściwości działania <xref:System.Activities.Statements.ForEach%601> i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagane|Pomiar|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa działania <xref:System.Activities.Statements.ForEach%601>. Wartość domyślna to ForEach < Int32\>. Mimo że wartość <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Prawda|Kolekcja elementów do iteracji. Aby ustawić <xref:System.Activities.Statements.ForEach%601.Values%2A>, wpisz wyrażenie Visual Basic w polu **wartości** w projektancie działania **ForEach < t\>** lub w siatce właściwości.|
|*TypeArgument*|Prawda|Typ elementów w kolekcji <xref:System.Activities.Statements.ForEach%601.Values%2A> określonej przez parametr generyczny *t*. Domyślnie *elementu TypeArgument* jest ustawiona na **Int32**. Aby zmienić typ, należy zmienić wartość pola kombi *elementu TypeArgument* w siatce właściwości.|

Domyślnie iterator pętli ma nazwę **element**. Nazwę zmiennej iteratora można zmienić w projektancie działania <xref:System.Activities.Statements.ForEach%601>. Iteratora pętli można używać w wyrażeniach w elemencie podrzędnym działania <xref:System.Activities.Statements.ForEach%601>.

## <a name="see-also"></a>Zobacz także

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
