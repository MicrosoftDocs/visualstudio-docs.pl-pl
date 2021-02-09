---
title: Projektant przepływu pracy — &lt; &gt; Projektant działań w usłudze foreach T
description: Dowiedz się, jak <T> działanie foreach wykonuje działanie zawarte w jego treści dla każdego elementu w określonej kolekcji wartości.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d4c594e613d1160794e8310695d61bcc97902caa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876462"
---
# <a name="foreachlttgt-activity-designer"></a>&lt; &gt; Projektant działań foreach T

<xref:System.Activities.Statements.ForEach%601>Działanie wykonuje działanie zawarte w jego <xref:System.Activities.Statements.ForEach%601.Body%2A> przypadku dla każdego elementu w określonej <xref:System.Activities.Statements.ForEach%601.Values%2A> kolekcji.

## <a name="foreacht-properties-in-the-workflow-designer"></a>Właściwości ForEach<T \> w Projektant przepływu pracy

W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.ForEach%601> właściwości działania i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa <xref:System.Activities.Statements.ForEach%601> działania. Wartość domyślna to ForEach<Int32 \> . Chociaż <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Prawda|Kolekcja elementów do iteracji. Aby ustawić <xref:System.Activities.Statements.ForEach%601.Values%2A> , wpisz wyrażenie Visual Basic w polu **wartości** w projektancie aktywności **foreach<T \>** lub w siatce właściwości.|
|*Elementu TypeArgument*|Prawda|Typ elementów w <xref:System.Activities.Statements.ForEach%601.Values%2A> kolekcji określony przez parametr generyczny *T*. Domyślnie *elementu TypeArgument* jest ustawiona na **Int32**. Aby zmienić typ, należy zmienić wartość pola kombi *elementu TypeArgument* w siatce właściwości.|

Domyślnie iterator pętli ma nazwę **element**. Można zmienić nazwę zmiennej iteratora w <xref:System.Activities.Statements.ForEach%601> projektancie działań. Iteratora pętli można używać w wyrażeniach w elemencie podrzędnym <xref:System.Activities.Statements.ForEach%601> działania.

## <a name="see-also"></a>Zobacz też

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
