---
title: Projektant przepływu pracy-ParallelForEach &lt;T &gt; — Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b68cd543ed41408e7510708367c8e539c0702ea1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650089"
---
# <a name="parallelforeach-activity-designer"></a>ParallelForEach, Projektant działań

Działanie <xref:System.Activities.Statements.ParallelForEach%601> wylicza elementy kolekcji i wykonuje osadzoną instrukcję dla każdego elementu kolekcji równolegle, czyli asynchronicznie w tym samym wątku. Użyj tego działania sterowania przepływem zamiast działania <xref:System.Activities.Statements.Sequence>, jeśli działania podrzędne tego działania powinny być bezczynne.

Działanie <xref:System.Activities.Statements.ParallelForEach%601> ma właściwość <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, która zawiera wyrażenie Visual Basic określone przez użytkownika. Działanie <xref:System.Activities.Statements.ParallelForEach%601> oblicza tę właściwość po zakończeniu każdej gałęzi. Jeśli wartość jest **równa true**, działanie <xref:System.Activities.Statements.ParallelForEach%601> zostanie zakończone bez wykonywania innych gałęzi. Jeśli <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> nie zostanie obliczona na **wartość true**, działanie <xref:System.Activities.Statements.ParallelForEach%601> zostanie zakończone po zakończeniu wszystkich działań podrzędnych.

## <a name="the-parallelforeacht-activity"></a>Działanie ParallelForEach < T \>

<xref:System.Activities.Statements.ParallelForEach%601> wylicza wartości i planuje <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> dla każdej wartości, która jest wyliczona. Planuje tylko <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. Sposób wykonywania treści zależy od tego, czy <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> przechodzą w stan bezczynności.

Jeśli <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> nie przejdzie w stan bezczynności, jest wykonywane w odwrotnej kolejności, ponieważ zaplanowane działania są obsługiwane jako stos, najpierw wykonywane jest ostatnie zaplanowane działanie. Na przykład jeśli masz kolekcję {1,2,3,4}in <xref:System.Activities.Statements.ParallelForEach%601> i użyj funkcji **WriteLine** jako treści, aby zapisać wartość. W konsoli programu znajduje się 4, 3, 2, 1. Wynika to z faktu, że funkcja **WriteLine** nie przechodzi w stan bezczynności, więc po zaplanowaniu **4 działań** na stosie wykonywane przy użyciu zachowania stosu (najpierw w ostatniej kolejności).

Ale jeśli masz działania w <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>, które mogą przejść w stan bezczynności, takie jak działanie <xref:System.ServiceModel.Activities.Receive> lub działanie <xref:System.Activities.Statements.Delay>. Nie trzeba czekać na ich zakończenie. <xref:System.Activities.Statements.ParallelForEach%601> przechodzi do następnego działania zaplanowanej treści i spróbuje go wykonać. Jeśli to działanie przekroczy wartość bezczynną, <xref:System.Activities.Statements.ParallelForEach%601> następuje po ponownym działaniu następnej treści.

### <a name="using-the-parallelforeacht-activity-designer"></a>Korzystanie z ParallelForEach \<T > Projektant działań

Dostęp do programu **ParallelForEach \<T >** projektanta działań w kategorii **przepływ sterowania** w **przyborniku**.

**ParallelForEach \<T >** projektanta aktywności można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchni, gdy projektanci aktywności są zwykle umieszczane na przykład w ramach działania **sekwencji** projektantów. Po porzucenie go do Projektant przepływu pracy tworzy działanie <xref:System.Activities.Statements.ParallelForEach%601>, które domyślnie zawiera <xref:System.Activities.Activity.DisplayName%2A> **ParallelForEach < Int32 \>.**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach < T \> właściwości w Projektant przepływu pracy

W poniższej tabeli przedstawiono najbardziej przydatne właściwości działania <xref:System.Activities.Statements.ParallelForEach%601> i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę wyświetlaną projektanta działań w nagłówku. Wartość domyślna to **ParallelForEach \<Int32 >** . Wartość można opcjonalnie edytować w siatce **Właściwości** lub bezpośrednio w nagłówku projektanta działań.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Działanie do wykonania dla każdego elementu w kolekcji. Aby dodać działanie <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>, Usuń działanie z przybornika do pola **treść** w projektancie aktywności **ParallelForEach \<T >** z podpowiedzią tekst "upuść działanie tutaj".|
|**Elementu TypeArgument**|Oznacza|Typ elementów w kolekcji <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> określonej przez parametr generyczny *t*. Domyślnie **elementu TypeArgument** jest ustawiona na **Int32**. Aby zmienić typ T w **ParallelForEach < T \>** , Zmień wartość pola kombi **elementu TypeArgument** w siatce właściwości.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|Oznacza|Kolekcja elementów do iteracji. Aby ustawić <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, wpisz wyrażenie Visual Basic w polu **wartości** w projektancie aktywności w usłudze **ForEach < t \>** w polu z tekstem wskazówki "wprowadź wyrażenie VB" lub w polu **wartości** w oknie **Właściwości** .|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Oceniane po zakończeniu każdej iteracji. Jeśli wartość jest równa true, zaplanowane oczekujące iteracje zostaną anulowane. Jeśli ta właściwość nie jest ustawiona, wszystkie zaplanowane instrukcje są wykonywane do momentu ukończenia.|

Domyślnie iterator pętli ma nazwę element. Nazwę zmiennej iteratora można zmienić w polu **foreach** w **ParallelForEach \<T >** projektancie działań. Iteratora pętli można używać w wyrażeniach w elemencie podrzędnym działania <xref:System.Activities.Statements.ParallelForEach%601>.

## <a name="see-also"></a>Zobacz także

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)