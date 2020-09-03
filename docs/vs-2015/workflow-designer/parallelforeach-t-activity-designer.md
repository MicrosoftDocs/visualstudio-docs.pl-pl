---
title: ParallelForEach &lt; T — &gt; Projektant działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c659e941a8503a0d5ff601fea23fcec69b2bbcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672614"
---
# <a name="parallelforeachlttgt-activity-designer"></a>ParallelForEach &lt; T, &gt; Projektant działań
<xref:System.Activities.Statements.ParallelForEach%601>Działanie wylicza elementy kolekcji i wykonuje osadzoną instrukcję dla każdego elementu kolekcji równolegle, czyli asynchronicznie w tym samym wątku. Użyj tego działania sterowania przepływem zamiast <xref:System.Activities.Statements.Sequence> działania, jeśli działania podrzędne tego działania powinny być bezczynne.

 <xref:System.Activities.Statements.ParallelForEach%601>Działanie ma <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Właściwość, która zawiera wyrażenie określone przez użytkownika [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] . <xref:System.Activities.Statements.ParallelForEach%601>Działanie oblicza tę właściwość po zakończeniu każdej gałęzi. Jeśli wartość jest **równa true**, <xref:System.Activities.Statements.ParallelForEach%601> działanie kończy się bez wykonywania innych gałęzi. Jeśli nie zostanie <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> obliczona **wartość true**, <xref:System.Activities.Statements.ParallelForEach%601> działanie kończy się po zakończeniu wszystkich działań podrzędnych.

## <a name="the-parallelforeacht-activity"></a>Działanie ParallelForEach \<T>
 <xref:System.Activities.Statements.ParallelForEach%601> Wylicza wartości i planuje <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> dla każdej wartości, która jest wyliczana. Planuje tylko <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> . Sposób wykonywania treści zależy od tego, czy <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> przechodzą w stan bezczynności.

 Jeśli <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> polecenie nie przechodzi w stan bezczynności, jest wykonywane w odwrotnej kolejności, ponieważ zaplanowane działania są obsługiwane jako stos, najpierw wykonywane jest ostatnie zaplanowane działanie. Na przykład jeśli masz kolekcję {1,2,3,4} w programie <xref:System.Activities.Statements.ParallelForEach%601> i używasz funkcji **WriteLine** jako treści do zapisania wartości. W konsoli programu znajduje się 4, 3, 2, 1. Wynika to z faktu, że funkcja **WriteLine** nie przechodzi w stan bezczynności, więc po zaplanowaniu **4 działań** na stosie wykonywane przy użyciu zachowania stosu (najpierw w ostatniej kolejności).

 Ale jeśli masz działania <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> , które mogą przejść w stan bezczynności, np <xref:System.ServiceModel.Activities.Receive> . działanie lub <xref:System.Activities.Statements.Delay> działanie. Nie trzeba czekać na ich zakończenie. <xref:System.Activities.Statements.ParallelForEach%601> przechodzi do następnego działania zaplanowanej treści i spróbuje go wykonać. Jeśli to działanie przekroczy wartość bezczynną, <xref:System.Activities.Statements.ParallelForEach%601> przenosi się ponownie przy następnym działaniu treści.

### <a name="using-the-parallelforeacht-activity-designer"></a>Korzystanie z \<T> projektanta działań ParallelForEach
 Projektanta **działań \<T> ParallelForEach** można znaleźć w kategorii **przepływ sterowania** **przybornika**, do którego uzyskuje się dostęp, klikając kartę **Przybornik** po lewej stronie okna [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X).

 Projektanta **działań \<T> ParallelForEach** można przeciągać z **przybornika** i znajdować się na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, wszędzie tam, gdzie projektanci aktywności są zwykle umieszczane, na przykład w ramach projektanta działania **sekwencji** . Po porzucenie go do programu [!INCLUDE[wfd2](../includes/wfd2-md.md)] tworzy <xref:System.Activities.Statements.ParallelForEach%601> działanie, które domyślnie zawiera <xref:System.Activities.Activity.DisplayName%2A> **ParallelForEach \<Int32> .**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>\<T>Właściwości ParallelForEach w Projektant przepływu pracy
 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.ParallelForEach%601> właściwości działania i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa przyjazną nazwę wyświetlaną projektanta działań w nagłówku. Wartość domyślna to **ParallelForEach \<Int32> **. Wartość można opcjonalnie edytować w siatce **Właściwości** lub bezpośrednio w nagłówku projektanta działań.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|Fałsz|Działanie do wykonania dla każdego elementu w kolekcji. Aby dodać <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> działanie, Usuń działanie z przybornika do pola **treść** w projektancie działań **ParallelForEach \<T> ** z podpowiedzią tekst "upuść działanie tutaj".|
|**Elementu TypeArgument**|Prawda|Typ elementów w <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> kolekcji określony przez parametr generyczny *T*. Domyślnie **elementu TypeArgument** jest ustawiona na **Int32**. Aby zmienić typ T w projektancie działań **ParallelForEach \<T> ** , Zmień wartość pola kombi **elementu TypeArgument** w siatce właściwości.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|Prawda|Kolekcja elementów do iteracji. Aby ustawić <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> , wpisz [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] wyrażenie w polu **wartości** w projektancie działań **ForEach \<T> ** w polu z tekstem wskazówki "wprowadź wyrażenie w języku VB" lub w polu **wartości** w oknie **Właściwości** .|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Oceniane po zakończeniu każdej iteracji. Jeśli wartość jest równa true, zaplanowane oczekujące iteracje zostaną anulowane. Jeśli ta właściwość nie jest ustawiona, wszystkie zaplanowane instrukcje są wykonywane do momentu ukończenia.|

 Domyślnie iterator pętli ma nazwę element. Nazwę zmiennej iteratora można zmienić w polu **foreach** w projektancie działań **ParallelForEach \<T> ** . Iteratora pętli można używać w wyrażeniach w elemencie podrzędnym <xref:System.Activities.Statements.ParallelForEach%601> działania.

## <a name="see-also"></a>Zobacz też
 [Sequence](../workflow-designer/sequence-activity-designer.md) [Równoległy](../workflow-designer/parallel-activity-designer.md) [przepływ sterowania](../workflow-designer/control-flow-activity-designers.md) sekwencji