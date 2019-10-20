---
title: Projektant działań równoległych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a46a340ccdeacacb8f04b962313db18975447a67
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672638"
---
# <a name="parallel-activity-designer"></a>Parallel, projektant działań
Działanie <xref:System.Activities.Statements.Parallel> wykonuje kolekcję działań podrzędnych jednocześnie.

## <a name="the-parallel-activity"></a>Działanie równoległe
 Działanie <xref:System.Activities.Statements.Parallel> przechowuje swoje działania podrzędne w kolekcji <xref:System.Activities.Statements.Parallel.Branches%2A>. Użyj działania <xref:System.Activities.Statements.Parallel> zamiast działania <xref:System.Activities.Statements.Sequence>, jeśli niektóre działania podrzędne mogą przejść w stan bezczynności.

 Działanie <xref:System.Activities.Statements.Parallel> ma właściwość <xref:System.Activities.Statements.Parallel.CompletionCondition%2A>, która zawiera wyrażenie [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] określone przez użytkownika. Działanie <xref:System.Activities.Statements.Parallel> oblicza tę właściwość po zakończeniu każdej gałęzi. Jeśli wartość jest **równa true**, działanie <xref:System.Activities.Statements.Parallel> zostanie zakończone bez wykonywania innych gałęzi. Jeśli <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> nie zostanie obliczona na **wartość true**, działanie <xref:System.Activities.Statements.Parallel> zostanie zakończone po zakończeniu wszystkich działań podrzędnych.

### <a name="using-the-parallel-activity-designer"></a>Korzystanie z programu Parallel Activity Designer
 Projektanta działań **równoległych** można znaleźć w kategorii **przepływ sterowania** **przybornika**, do którego uzyskuje się dostęp, klikając kartę **Przybornik** po lewej stronie [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie, wybierając pozycję **pasek narzędzi** z  **Menu Widok** lub CTRL + ALT + X.)

 Projektanta działań **równoległych** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchnię, gdy projektanci aktywności są zwykle umieszczane na przykład w ramach projektanta działania **sekwencji** . Po porzucenie go do [!INCLUDE[wfd2](../includes/wfd2-md.md)] tworzy działanie <xref:System.Activities.Statements.Parallel>, które domyślnie zawiera <xref:System.Activities.Activity.DisplayName%2A> **równoległe**

 Aby dodać działanie do kolekcji <xref:System.Activities.Statements.Parallel.Branches%2A> działania równoległego, przeciągnij inny Projektant działań z **przybornika** i upuść go na trójkącie wewnątrz projektanta działań **równoległych** . Trójkąty współdzielą działania zawarte w gałęziach. Dodatkowe działania można dodać przez powtórzenie tej procedury. Działania można zmienić uporządkowane przez przeciąganie i upuszczanie ich w obrębie projektanta działań **równoległych** .

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Właściwości działania równoległego w Projektant przepływu pracy
 W poniższej tabeli przedstawiono właściwości działania równoległego i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę wyświetlaną projektanta działań w nagłówku. Wartość domyślna to **Parallel**. Wartość można opcjonalnie edytować w siatce **Właściwości** lub bezpośrednio w nagłówku projektanta działań.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Oznacza|Zawiera kolekcję działań podrzędnych do wykonania.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Oceniane po zakończeniu gałęzi. Jeśli wartość jest **równa true**, zaplanowane oczekujące gałęzie są anulowane. Jeśli ta właściwość nie jest ustawiona lub ma **wartość false**, działanie kończy się po zakończeniu wszystkich działań podrzędnych. Wartość domyślna to **null**.|

## <a name="see-also"></a>Zobacz też
 [](../workflow-designer/sequence-activity-designer.md) [@No__t_2T ParallelForEach sekwencji >](../workflow-designer/parallelforeach-t-activity-designer.md) [przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)