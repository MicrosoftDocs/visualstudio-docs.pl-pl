---
title: FlowSwitch &lt; T — &gt; Projektant działań | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656642"
---
# <a name="flowswitchlttgt-activity-designer"></a>FlowSwitch &lt; T, &gt; Projektant działań
<xref:System.Activities.Statements.FlowSwitch%601>Działanie jest węzłem warunkowym, który zapewnia rozgałęzianie przepływu sterowania na podstawie kryterium dopasowywania, gdy wymagane są więcej niż dwa alternatywne gałęzie. Jeśli rozgałęzienie przepływu wymaga tylko dwóch ścieżek, użyj <xref:System.Activities.Statements.FlowDecision> działania zamiast tego.

## <a name="the-flowswitcht-activity"></a>Działanie FlowSwitch \<T>
 <xref:System.Activities.Statements.FlowSwitch%601>Działanie zawiera element <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> , który zwraca wartość typu *T* (określoną przez parametr ogólny) podczas szacowania. Działanie zawiera również zestaw <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> , który określa unikatowe mapowanie z możliwych wyników tej oceny do zestawu <xref:System.Activities.Statements.FlowNode> obiektów. <xref:System.Activities.Statements.FlowNode>Wykonanie jest tym, którego obiekt typu *T* jest zgodny z wartością obliczoną <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . W przypadku, gdy <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> nie zostanie uzyskany odpowiednika, można podać wartość Case (opcjonalnie).

### <a name="using-the-flowswitcht-activity-designer"></a>Korzystanie z \<T> projektanta działań FlowSwitch
 Projektanta **działań \<T> FlowSwitch** można znaleźć w kategorii **schemat blokowy** **przybornika**, do którego uzyskuje się dostęp, klikając kartę **Przybornik** po lewej stronie okna [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X).

 Projektanta **działań \<T> FlowSwitch** można przeciągać z **przybornika** i upuszczać na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchnię w ramach projektanta działań **schematu blokowego** . Użyj okna **Wybieranie typów** , które wyświetla, aby określić typ (skojarzony w kodzie za pomocą <xref:System.Activities.Statements.FlowSwitch%601> jego parametru ogólnego) uzyskany z oceny <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Ta procedura powoduje utworzenie <xref:System.Activities.Statements.FlowSwitch%601> działania z etykietą **przełącznika** w ramach <xref:System.Activities.Statements.Flowchart> działania. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>Można wpisać w polu **wyrażenie** okna **Właściwości** , klikając miejsce, w którym tekst wskazówki brzmi "wprowadź wyrażenie VB".

 Wskaźnik myszy nad projektantem działań **FlowSwitch \<T> ** , aby spowodować, że uchwyty kwadratowe, które są używane do łączenia się, <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> są wyświetlane wokół krawędzi. Po przeciągnięciu projektanta aktywności **FlowSwitch \><T** i innych projektantów działań na **schemat blokowy** <xref:System.Activities.Activity> obiekty, które reprezentują, są gotowe do powiązania ze sobą, aby określić kolejność wykonywania. Aby utworzyć jedno z elementów <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> skojarzonych z <xref:System.Activities.Statements.FlowSwitch%601> , kliknij jeden z kwadratowych uchwytów wielkości liter na obwodzie **FlowSwitch \<T> ** i przeciągnij go (trzymając przycisk myszy) do jednego z dojść, które pojawiają się w podobny sposób wokół działania docelowego, gdy wskaźnik myszy jest przesuwany nad jego projektantem. Zwolnij przycisk myszy i strzałkę od **FlowSwitch \<T> ** do projektanta docelowego pojawia się w tym przypadku. Wartość domyślna tego przypadku jest wyświetlana na strzałce i może być edytowana w polu **Case** okna **Właściwości** .

### <a name="the-flowswitcht-properties"></a>Właściwości FlowSwitch \<T>
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.FlowSwitch%601> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchni projektanta.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Prawda|Określa wyrażenie, które jest oceniane, aby określić, które z elementów <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> do przełączenia w ścieżce wykonania.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|Fałsz|Określa unikatowe mapowanie z możliwych wyników uzyskanych na podstawie oceny <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> do zestawu <xref:System.Activities.Statements.FlowNode> obiektów.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Prawda|Określa mapowanie, gdy oszacowanie <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> nie pasuje do jednej z wartości zawartych w <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> obiekcie.|

## <a name="see-also"></a>Zobacz też
 Schemat blokowy [schematu blokowego](../workflow-designer/flowchart-activity-designers.md) [Flowchart](../workflow-designer/flowchart-activity-designer.md) [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)