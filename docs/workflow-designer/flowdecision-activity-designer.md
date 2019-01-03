---
title: Projektant przepływu pracy — FlowDecision, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 15100a7a43147e49d6762119828566d613034fea
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848208"
---
# <a name="flowdecision-activity-designer"></a>FlowDecision, projektant działań

<xref:System.Activities.Statements.FlowDecision> Węzeł jest węzłem warunkowe, oferująca gałęzi przepływ sterowania w jednym z dwóch rozwiązań alternatywnych, na podstawie tego, czy określony warunek jest spełniony. Jeśli przepływ wymaga więcej niż dwie gałęzie, należy użyć <xref:System.Activities.Statements.FlowSwitch%601> zamiast tego.

## <a name="the-flowdecision-node"></a>Węzeł FlowDecision

Użyj <xref:System.Activities.Statements.FlowDecision> podczas przepływu, można rozgałęzić do dwóch ścieżek. A <xref:System.Activities.Statements.FlowDecision> węzeł ma <xref:System.Activities.Statements.FlowDecision.Condition%2A> i <xref:System.Activities.Statements.FlowNode> związany z każdą dwa możliwe wyniki: <xref:System.Activities.Statements.FlowDecision.True%2A> lub <xref:System.Activities.Statements.FlowDecision.False%2A>. <xref:System.Activities.Statements.FlowDecision.Condition%2A> Jest obliczane i wartość tego okresu ewaluacji określa następnego <xref:System.Activities.Statements.FlowNode> mają być przetwarzane w ramach <xref:System.Activities.Statements.Flowchart>.

### <a name="using-the-flowdecision-designer"></a>Za pomocą projektanta FlowDecision

**FlowDecision** projektanta znajdują się w **schemat blokowy** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** Karta w Projektancie przepływu pracy. Można także wybrać **przybornika** z **widoku** menu lub naciśnij klawisz **Ctrl**+**Alt** + **X**.

**FlowDecision** projektanta mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy w ramach **schemat blokowy** projektanta działań. Spowoduje to utworzenie <xref:System.Activities.Statements.FlowDecision> etykietą **decyzji** w ramach <xref:System.Activities.Statements.Flowchart> działania. Myszy projektanta i **True** i **False** kwadratowy dla obu gałęzi uchwytów.

Po przeciągnięciu **FlowDecision** projektanta i innych projektantów na **schemat blokowy**, węzły, które mogą być połączone ze sobą, aby określić kolejność wykonywania. Utwórz łącze między węzeł źródłowy (w tym **True** i **False** gałęzi z **FlowDecision**) i węzła docelowego myszy Projektanta węzeł źródłowy i kwadratowy uchwytów na każdej stronie. Kliknij jeden z uchwytów, kwadratowych i przeciągnij go, przytrzymując przycisk myszy, aby jeden z uchwytów, które pojawia się w podobny sposób w całym węźle docelowym, gdy wskaźnik myszy nad nim. Zwolnij przycisk myszy, a następnie tworzone jest połączenie między tymi dwoma węzłami, które jest reprezentowany jako strzałka z projektanta źródła do docelowego projektanta.

Wyrażenie, które stany <xref:System.Activities.Statements.FlowDecision.Condition%2A> można wpisać w **warunek** pole **właściwości** , klikając pozycję okna, gdy tekst wskazówki jest wyświetlany komunikat "Wprowadź wyrażenie VB".

### <a name="the-flowdecision-properties"></a>Właściwości FlowDecision

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.FlowDecision> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchni projektowej.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|Prawda|Warunek, który określa ścieżkę, która przyjmuje sterowanie przepływem.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|Ścieżka podjęte przez sterowanie przepływem, jeśli <xref:System.Activities.Statements.FlowDecision.Condition%2A> jest spełniony.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|Ścieżka podjęte przez sterowanie przepływem, jeśli <xref:System.Activities.Statements.FlowDecision.Condition%2A> nie jest spełniony.|

## <a name="see-also"></a>Zobacz także

- [Schemat blokowy](../workflow-designer/flowchart-activity-designers.md)
- [Schemat blokowy](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)