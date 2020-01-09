---
title: Projektant przepływu pracy — Projektant działań<T> FlowSwitch
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8271100936b9cf70e17c0e6279297d583714f018
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597155"
---
# <a name="flowswitcht-activity-designer"></a>FlowSwitch\<T >, Projektant działań

Działanie <xref:System.Activities.Statements.FlowSwitch%601> jest węzłem warunkowym, który zapewnia rozgałęzianie przepływu sterowania w oparciu o kryterium dopasowywania, gdy wymagane są więcej niż dwa gałęzie alternatywne. Jeśli rozgałęzienie przepływu wymaga tylko dwóch ścieżek, zamiast tego użyj działania <xref:System.Activities.Statements.FlowDecision>.

## <a name="the-flowswitcht-activity"></a>Działanie FlowSwitch\<T >

Działanie <xref:System.Activities.Statements.FlowSwitch%601> zawiera <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>, które zwraca wartość typu *t* (określoną przez parametr ogólny) podczas szacowania. Działanie zawiera również zestaw <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, który określa unikatowe mapowanie z możliwych wyników tej oceny do zestawu obiektów <xref:System.Activities.Statements.FlowNode>. <xref:System.Activities.Statements.FlowNode> wykonywane jest taki, którego obiekt typu *t* jest zgodny z wartością szacowanego <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. W przypadku <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> może być określony (opcjonalnie) dla przypadku, w którym nie jest uzyskiwane dopasowanie.

### <a name="using-the-flowswitcht-activity-designer"></a>Korzystanie z programu FlowSwitch\<T > Designer

**FlowSwitch\<t >** projektanta aktywności można znaleźć w kategorii **schemat blokowy** **, do**którego uzyskuje się dostęp, klikając kartę **Przybornik** po lewej stronie Projektant przepływu pracy. Alternatywnie wybierz pozycję **Przybornik** z menu **Widok** lub naciśnij **klawisze CTRL**+**Alt**+**X**.

**FlowSwitch\<t >** projektanta aktywności można przeciągnąć z **przybornika** i porzucić na powierzchnię Projektant przepływu pracy w ramach projektanta działań **schematu blokowego** . Użyj okna **Wybieranie typów** , które wyświetla, aby określić typ (skojarzony w kodzie z <xref:System.Activities.Statements.FlowSwitch%601>ą przez jego parametr ogólny) uzyskaną z oceny <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Ta procedura powoduje utworzenie <xref:System.Activities.Statements.FlowSwitch%601> z etykietą działania **w ramach działania** <xref:System.Activities.Statements.Flowchart>. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> można wpisać w polu **wyrażenie** okna **Właściwości** , klikając miejsce, w którym tekst wskazówki brzmi "wprowadź wyrażenie VB".

Wskaźnik myszy nad **FlowSwitch\<t >** , aby spowodować, że uchwyty kwadratowe, które są używane do łączenia <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> do wyświetlania wokół krawędzi. Po przeciągnięciu projektanta aktywności **FlowSwitch < T\>** i innych projektantów działań na **schemat blokowy**<xref:System.Activities.Activity> obiekty, które reprezentują, są gotowe do połączenia, aby określić kolejność wykonywania. Aby utworzyć jedną z <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> skojarzonych z <xref:System.Activities.Statements.FlowSwitch%601>, kliknij jeden z kwadratowych uchwytów wielkości liter na obrzeżu **FlowSwitch < t\>** i przeciągnij go (trzymając wciśnięty przycisk myszy) do jednego z uchwytów, które pojawiają się w podobny sposób wokół działania docelowego, gdy wskaźnik myszy jest przesuwany nad jego projektantem. Zwolnij przycisk myszy i strzałkę z **FlowSwitch < T\>** do projektanta docelowego pojawia się w tym przypadku. Wartość domyślna tego przypadku jest wyświetlana na strzałce i może być edytowana w polu **Case** okna **Właściwości** .

### <a name="the-flowswitcht-properties"></a>Właściwości FlowSwitch\<T >

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.FlowSwitch%601> i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchni projektanta.

|Nazwa właściwości|Wymagane|Pomiar|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Prawda|Określa wyrażenie, które ma zostać obliczone, aby określić, który <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> do przełączenia w ścieżce wykonania.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|Fałsz|Określa unikatowe mapowanie spośród możliwych wyników uzyskanych z oceny <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> do zestawu obiektów <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Prawda|Określa mapowanie, gdy Obliczanie <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> nie jest zgodne z jedną z wartości zawartych w obiekcie <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|

## <a name="see-also"></a>Zobacz także

- [Schemat blokowy](../workflow-designer/flowchart-activity-designers.md)
- [Schemat blokowy](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
