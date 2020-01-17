---
title: Projektant przepływu pracy — Projektant działań FlowDecision
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79e405f82bcf33bc01ad07f1092879c17dec5849
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76111432"
---
# <a name="flowdecision-activity-designer"></a>FlowDecision, projektant działań

Węzeł <xref:System.Activities.Statements.FlowDecision> jest węzłem warunkowym, który udostępnia gałąź dla przepływu sterowania w jednym z dwóch alternatyw, w zależności od tego, czy określony warunek jest spełniony. Jeśli przepływ wymaga więcej niż dwóch gałęzi, Użyj zamiast niego <xref:System.Activities.Statements.FlowSwitch%601>.

## <a name="the-flowdecision-node"></a>Węzeł FlowDecision

Użyj <xref:System.Activities.Statements.FlowDecision>, gdy przepływ można rozgałęzić na dwie ścieżki. Węzeł <xref:System.Activities.Statements.FlowDecision> ma <xref:System.Activities.Statements.FlowDecision.Condition%2A> i <xref:System.Activities.Statements.FlowNode> skojarzone z dwoma możliwymi wynikami: <xref:System.Activities.Statements.FlowDecision.True%2A> lub <xref:System.Activities.Statements.FlowDecision.False%2A>. <xref:System.Activities.Statements.FlowDecision.Condition%2A> jest oceniane, a wartość tej oceny określa następny <xref:System.Activities.Statements.FlowNode> do przetworzenia w <xref:System.Activities.Statements.Flowchart>.

### <a name="using-the-flowdecision-designer"></a>Korzystanie z narzędzia FlowDecision Designer

Projektanta **FlowDecision** można znaleźć w kategorii **schemat blokowy** , do którego **uzyskuje się dostęp**, klikając kartę **Przybornik** na Projektant przepływu pracy. Alternatywnie wybierz pozycję **Przybornik** z menu **Widok** lub naciśnij **klawisze CTRL**+**Alt**+**X**.

Projektanta **FlowDecision** można przeciągnąć z **przybornika** i porzucić do Projektant przepływu pracy powierzchni w ramach projektanta działań **schematu blokowego** . Spowoduje to utworzenie <xref:System.Activities.Statements.FlowDecision> oznaczonej **decyzją** w ramach działania <xref:System.Activities.Statements.Flowchart>. Wskaźnik myszy nad projektantem i dojścia do **rzeczywistych** i **fałszywych** kwadratów dla dwóch gałęzi.

Po przeciągnięciu projektanta **FlowDecision** i innych projektantów na **schemat blokowy**węzły mogą być połączone ze sobą, aby określić kolejność wykonywania. Aby utworzyć łącze między węzłem źródłowym (z uwzględnieniem **rzeczywistych** i **fałszywych** gałęzi **FlowDecision**) i węzłem docelowym, mysz nad projektantem węzła źródłowego i uchwyty kwadratowe pojawiają się po każdej stronie. Kliknij jeden z uchwytów kwadratowych i przeciągnij go, przytrzymując wciśnięty przycisk myszy do jednego z uchwytów, które pojawiają się w podobny sposób wokół węzła docelowego po umieszczeniu nad nim wskaźnika myszy. Zwolnij przycisk myszy, a łącze między utworzonymi tymi dwoma węzłami jest reprezentowane jako strzałka z projektanta źródła do projektanta docelowego.

Wyrażenie określające <xref:System.Activities.Statements.FlowDecision.Condition%2A> można wpisać w polu **warunek** okna **Właściwości** , klikając miejsce, w którym tekst wskazówki brzmi "wprowadź wyrażenie VB".

### <a name="the-flowdecision-properties"></a>Właściwości FlowDecision

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.FlowDecision> i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchni projektanta.

|Nazwa właściwości|Wymagane|Pomiar|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|Prawda|Warunek określający, która ścieżka ma być wykonywana przez sterowanie przepływem.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|Fałsz|Ścieżka wykonywana przez sterowanie przepływem, jeśli <xref:System.Activities.Statements.FlowDecision.Condition%2A> jest spełniony.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|Fałsz|Ścieżka wykonywana przez sterowanie przepływem, jeśli <xref:System.Activities.Statements.FlowDecision.Condition%2A> nie jest spełniony.|

## <a name="see-also"></a>Zobacz także

- [Schemat blokowy](../workflow-designer/flowchart-activity-designers.md)
- [Schemat blokowy](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)
