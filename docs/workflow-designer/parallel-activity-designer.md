---
title: Projektant przepływu pracy — Projektant działań równoległych
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f07dd02f682cd5c61d4d17099c1aeb76bb39bf8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593164"
---
# <a name="parallel-activity-designer"></a>Parallel, projektant działań

Działanie <xref:System.Activities.Statements.Parallel> wykonuje kolekcję działań podrzędnych jednocześnie.

## <a name="the-parallel-activity"></a>Działanie równoległe

Działanie <xref:System.Activities.Statements.Parallel> przechowuje swoje działania podrzędne w kolekcji <xref:System.Activities.Statements.Parallel.Branches%2A>. Użyj działania <xref:System.Activities.Statements.Parallel> zamiast działania <xref:System.Activities.Statements.Sequence>, jeśli niektóre działania podrzędne mogą przejść w stan bezczynności.

Działanie <xref:System.Activities.Statements.Parallel> ma właściwość <xref:System.Activities.Statements.Parallel.CompletionCondition%2A>, która zawiera wyrażenie Visual Basic określone przez użytkownika. Działanie <xref:System.Activities.Statements.Parallel> oblicza tę właściwość po zakończeniu każdej gałęzi. Jeśli wartość jest **równa true**, działanie <xref:System.Activities.Statements.Parallel> zostanie zakończone bez wykonywania innych gałęzi. Jeśli <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> nie zostanie obliczona na **wartość true**, działanie <xref:System.Activities.Statements.Parallel> zostanie zakończone po zakończeniu wszystkich działań podrzędnych.

### <a name="using-the-parallel-activity-designer"></a>Korzystanie z programu Parallel Activity Designer

Dostęp do programu **Parallel** Activity Designer w kategorii **przepływ sterowania** w **przyborniku**.

Projektanta działań **równoległych** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, gdy projektanci aktywności są zwykle umieszczane na przykład w ramach projektanta działania **sekwencji** . Po porzucenie go do Projektant przepływu pracy tworzy działanie <xref:System.Activities.Statements.Parallel>, które domyślnie zawiera <xref:System.Activities.Activity.DisplayName%2A> **równoległe**

Aby dodać działanie do kolekcji <xref:System.Activities.Statements.Parallel.Branches%2A> działania równoległego, przeciągnij inny Projektant działań z **przybornika** i upuść go na trójkącie wewnątrz projektanta działań **równoległych** . Trójkąty współdzielą działania zawarte w gałęziach. Dodatkowe działania można dodać przez powtórzenie tej procedury. Działania można zmienić uporządkowane przez przeciąganie i upuszczanie ich w obrębie projektanta działań **równoległych** .

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Właściwości działania równoległego w Projektant przepływu pracy

W poniższej tabeli przedstawiono właściwości działania równoległego i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagane|Pomiar|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa przyjazną nazwę wyświetlaną projektanta działań w nagłówku. Wartość domyślna to **Parallel**. Wartość można opcjonalnie edytować w siatce **Właściwości** lub bezpośrednio w nagłówku projektanta działań.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Prawda|Zawiera kolekcję działań podrzędnych do wykonania.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|Fałsz|Oceniane po zakończeniu gałęzi. Jeśli wartość jest **równa true**, zaplanowane oczekujące gałęzie są anulowane. Jeśli ta właściwość nie jest ustawiona lub ma **wartość false**, działanie kończy się po zakończeniu wszystkich działań podrzędnych. Wartość domyślna to **null**.|

## <a name="see-also"></a>Zobacz także

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
