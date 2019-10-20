---
title: FlowSwitch &lt;T &gt; — Projektant działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 27abb660766a7c04742eca221432af19f05f0d28
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656642"
---
# <a name="flowswitchlttgt-activity-designer"></a>FlowSwitch &lt;T &gt; — Projektant działań
Działanie <xref:System.Activities.Statements.FlowSwitch%601> jest węzłem warunkowym, który zapewnia rozgałęzianie przepływu sterowania w oparciu o kryterium dopasowywania, gdy wymagane są więcej niż dwa gałęzie alternatywne. Jeśli rozgałęzienie przepływu wymaga tylko dwóch ścieżek, zamiast tego użyj działania <xref:System.Activities.Statements.FlowDecision>.

## <a name="the-flowswitcht-activity"></a>Działanie FlowSwitch \<T >
 Działanie <xref:System.Activities.Statements.FlowSwitch%601> zawiera <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>, które zwraca wartość typu *t* (określoną przez parametr ogólny) podczas szacowania. Działanie zawiera również zestaw <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, który określa unikatowe mapowanie z możliwych wyników tej oceny do zestawu obiektów <xref:System.Activities.Statements.FlowNode>. @No__t_0 wykonywane jest taki, którego obiekt typu *t* jest zgodny z wartością szacowanego <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. W przypadku <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> może być określony (opcjonalnie) dla przypadku, w którym nie jest uzyskiwane dopasowanie.

### <a name="using-the-flowswitcht-activity-designer"></a>Korzystanie z FlowSwitch \<T > Projektant działań
 Projektanta działań programu **FlowSwitch \<T >** można znaleźć w kategorii **schemat blokowy** **przybornika**, do którego jest uzyskiwany dostęp, klikając kartę **Przybornik** po lewej stronie [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierając pozycję **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X.)

 **FlowSwitch \<T >** projektanta aktywności można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchnię w ramach projektanta działań **Flowchart** . Użyj okna **Wybieranie typów** , które wyświetla, aby określić typ (skojarzony w kodzie z <xref:System.Activities.Statements.FlowSwitch%601>ą przez jego parametr ogólny) uzyskaną z oceny <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Ta procedura powoduje utworzenie <xref:System.Activities.Statements.FlowSwitch%601> z etykietą działania **w ramach działania** <xref:System.Activities.Statements.Flowchart>. @No__t_0 można wpisać w polu **wyrażenie** okna **Właściwości** , klikając miejsce, w którym tekst wskazówki brzmi "wprowadź wyrażenie VB".

 Wskaźnik myszy nad **FlowSwitch \<T >** projektanta działań, aby spowodować, że uchwyty kwadratowe, które są używane do łączenia <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> do wyświetlania wokół krawędzi. Po przeciągnięciu projektanta aktywności **FlowSwitch < T \>** i innych projektantów działań na **schemat blokowy**<xref:System.Activities.Activity> obiekty, które reprezentują, są gotowe do połączenia, aby określić kolejność wykonywania. Aby utworzyć jedną z <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> skojarzonych z <xref:System.Activities.Statements.FlowSwitch%601>, kliknij jeden z kwadratowych uchwytów wielkości liter na obrzeżu **FlowSwitch \<T >** i przeciągnij go (przytrzymując przycisk myszy) do jednego z uchwytów, które pojawiają się w podobny sposób wokół działanie docelowe po umieszczeniu wskaźnika myszy nad jego projektantem. Zwolnij przycisk myszy i strzałkę z **FlowSwitch \<T >** zostanie wyświetlony Projektant docelowy reprezentujący ten przypadek. Wartość domyślna tego przypadku jest wyświetlana na strzałce i może być edytowana w polu **Case** okna **Właściwości** .

### <a name="the-flowswitcht-properties"></a>Właściwości FlowSwitch \<T >
 W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.FlowSwitch%601> i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchni projektanta.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Oznacza|Określa wyrażenie, które ma zostać obliczone, aby określić, który <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> do przełączenia w ścieżce wykonania.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Określa unikatowe mapowanie spośród możliwych wyników uzyskanych z oceny <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> do zestawu obiektów <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Oznacza|Określa mapowanie, gdy Obliczanie <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> nie jest zgodne z jedną z wartości zawartych w obiekcie <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|

## <a name="see-also"></a>Zobacz też
 Schemat blokowy [schematu blokowego](../workflow-designer/flowchart-activity-designers.md) [](../workflow-designer/flowchart-activity-designer.md) [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)