---
title: Projektant przepływu pracy — Projektant działań FlowDecision
description: Dowiedz się, w jaki sposób węzeł FlowDecision jest węzłem warunkowym, który zapewnia gałąź dla przepływu sterowania w jednym z dwóch alternatyw.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 77570557563b4aca3109f5bcbdebd16c7af09144
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938437"
---
# <a name="flowdecision-activity-designer"></a>FlowDecision, projektant działań

<xref:System.Activities.Statements.FlowDecision>Węzeł jest węzłem warunkowym, który udostępnia gałąź dla przepływu sterowania w jednym z dwóch alternatyw, w zależności od tego, czy określony warunek jest spełniony. Jeśli przepływ wymaga więcej niż dwóch gałęzi, użyj <xref:System.Activities.Statements.FlowSwitch%601> zamiast niego.

## <a name="the-flowdecision-node"></a>Węzeł FlowDecision

Użyj <xref:System.Activities.Statements.FlowDecision> , gdy przepływ można rozgałęziać na dwie ścieżki. <xref:System.Activities.Statements.FlowDecision>Węzeł ma <xref:System.Activities.Statements.FlowDecision.Condition%2A> i jest <xref:System.Activities.Statements.FlowNode> skojarzony z każdą z dwóch możliwych wyników: <xref:System.Activities.Statements.FlowDecision.True%2A> lub <xref:System.Activities.Statements.FlowDecision.False%2A> . <xref:System.Activities.Statements.FlowDecision.Condition%2A>Jest oceniane i wartość tej oceny określa, że następny <xref:System.Activities.Statements.FlowNode> do przetworzenia w ramach <xref:System.Activities.Statements.Flowchart> .

### <a name="using-the-flowdecision-designer"></a>Korzystanie z narzędzia FlowDecision Designer

Projektanta **FlowDecision** można znaleźć w kategorii **schemat blokowy** , do którego **uzyskuje się dostęp**, klikając kartę **Przybornik** na Projektant przepływu pracy. Alternatywnie możesz wybrać **Przybornik** z menu **Widok** lub nacisnąć **klawisze CTRL** + **Alt** + **X**.

Projektanta **FlowDecision** można przeciągnąć z **przybornika** i porzucić do Projektant przepływu pracy powierzchni w ramach projektanta działań **schematu blokowego** . Spowoduje to utworzenie <xref:System.Activities.Statements.FlowDecision> oznaczonej **decyzji** w ramach <xref:System.Activities.Statements.Flowchart> działania. Wskaźnik myszy nad projektantem i dojścia do **rzeczywistych** i **fałszywych** kwadratów dla dwóch gałęzi.

Po przeciągnięciu projektanta **FlowDecision** i innych projektantów na **schemat blokowy** węzły mogą być połączone ze sobą, aby określić kolejność wykonywania. Aby utworzyć łącze między węzłem źródłowym (z uwzględnieniem **rzeczywistych** i **fałszywych** gałęzi **FlowDecision**) i węzłem docelowym, mysz nad projektantem węzła źródłowego i uchwyty kwadratowe pojawiają się po każdej stronie. Kliknij jeden z uchwytów kwadratowych i przeciągnij go, przytrzymując wciśnięty przycisk myszy do jednego z uchwytów, które pojawiają się w podobny sposób wokół węzła docelowego po umieszczeniu nad nim wskaźnika myszy. Zwolnij przycisk myszy, a łącze między utworzonymi tymi dwoma węzłami jest reprezentowane jako strzałka z projektanta źródła do projektanta docelowego.

Wyrażenie określające, że <xref:System.Activities.Statements.FlowDecision.Condition%2A> można wpisać w polu **warunek** okna **Właściwości** , klikając miejsce, w którym tekst wskazówki brzmi "wprowadź wyrażenie VB".

### <a name="the-flowdecision-properties"></a>Właściwości FlowDecision

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.FlowDecision> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchni projektanta.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|Prawda|Warunek określający, która ścieżka ma być wykonywana przez sterowanie przepływem.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|Fałsz|Ścieżka wykonywana przez sterowanie przepływem, jeśli <xref:System.Activities.Statements.FlowDecision.Condition%2A> jest spełniony.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|Fałsz|Ścieżka wykonywana przez sterowanie przepływem, jeśli <xref:System.Activities.Statements.FlowDecision.Condition%2A> nie jest spełniony.|

## <a name="see-also"></a>Zobacz też

- [Schemat blokowy](../workflow-designer/flowchart-activity-designers.md)
- [Schemat blokowy](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)
