---
title: Projektant przepływu pracy — Projektant działań równoległych
description: Zapoznaj się z działaniem równoległym oraz jak używać projektanta działań równoległych w celu współbieżnego wykonywania kolekcji działań podrzędnych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3997b72105c22f10500559370d8a23faaa2f24eb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905172"
---
# <a name="parallel-activity-designer"></a>Parallel, projektant działań

<xref:System.Activities.Statements.Parallel>Działanie wykonuje kolekcję działań podrzędnych jednocześnie.

## <a name="the-parallel-activity"></a>Działanie równoległe

<xref:System.Activities.Statements.Parallel>Działanie przechowuje działania podrzędne w <xref:System.Activities.Statements.Parallel.Branches%2A> kolekcji. Użyj <xref:System.Activities.Statements.Parallel> działania zamiast <xref:System.Activities.Statements.Sequence> działania, jeśli niektóre działania podrzędne mogą przejść w stan bezczynności.

<xref:System.Activities.Statements.Parallel>Działanie ma <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> Właściwość, która zawiera wyrażenie Visual Basic określone przez użytkownika. <xref:System.Activities.Statements.Parallel>Działanie oblicza tę właściwość po zakończeniu każdej gałęzi. Jeśli wartość jest **równa true**, <xref:System.Activities.Statements.Parallel> działanie kończy się bez wykonywania innych gałęzi. Jeśli nie zostanie <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> obliczona **wartość true**, <xref:System.Activities.Statements.Parallel> działanie kończy się po zakończeniu wszystkich działań podrzędnych.

### <a name="using-the-parallel-activity-designer"></a>Korzystanie z programu Parallel Activity Designer

Dostęp do programu **Parallel** Activity Designer w kategorii **przepływ sterowania** w **przyborniku**.

Projektanta działań **równoległych** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, gdy projektanci aktywności są zwykle umieszczane na przykład w ramach projektanta działania **sekwencji** . Po porzucenie go do Projektant przepływu pracy tworzy <xref:System.Activities.Statements.Parallel> działanie, które domyślnie zawiera a <xref:System.Activities.Activity.DisplayName%2A> **równolegle**

Aby dodać działanie do <xref:System.Activities.Statements.Parallel.Branches%2A> kolekcji aktywności równoległej, przeciągnij inny Projektant działań z **przybornika** i upuść go na trójkącie wewnątrz projektanta działań **równoległych** . Trójkąty współdzielą działania zawarte w gałęziach. Dodatkowe działania można dodać przez powtórzenie tej procedury. Działania można zmienić uporządkowane przez przeciąganie i upuszczanie ich w obrębie projektanta działań **równoległych** .

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Właściwości działania równoległego w Projektant przepływu pracy

W poniższej tabeli przedstawiono właściwości działania równoległego i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa przyjazną nazwę wyświetlaną projektanta działań w nagłówku. Wartość domyślna to **Parallel**. Wartość można opcjonalnie edytować w siatce **Właściwości** lub bezpośrednio w nagłówku projektanta działań.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Prawda|Zawiera kolekcję działań podrzędnych do wykonania.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|Fałsz|Oceniane po zakończeniu gałęzi. Jeśli wartość jest **równa true**, zaplanowane oczekujące gałęzie są anulowane. Jeśli ta właściwość nie jest ustawiona lub ma **wartość false**, działanie kończy się po zakończeniu wszystkich działań podrzędnych. Wartość domyślna to **null**.|

## <a name="see-also"></a>Zobacz też

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
