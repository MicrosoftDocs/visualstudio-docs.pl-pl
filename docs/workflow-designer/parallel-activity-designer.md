---
title: Projektant przepływu pracy — Parallel, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: adc84c10f703488357adcee7739c46183f8c2e85
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925802"
---
# <a name="parallel-activity-designer"></a>Parallel, projektant działań

<xref:System.Activities.Statements.Parallel> Działanie jest wykonywane równocześnie zbiór działań podrzędnych.

## <a name="the-parallel-activity"></a>Działanie równoległe

<xref:System.Activities.Statements.Parallel> Działania przechowuje działania podrzędne w <xref:System.Activities.Statements.Parallel.Branches%2A> kolekcji. Użyj <xref:System.Activities.Statements.Parallel> działania zamiast <xref:System.Activities.Statements.Sequence> działanie w przypadku niektórych działań podrzędnych może być bezczynny.

<xref:System.Activities.Statements.Parallel> Działanie ma <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> właściwość, która zawiera użytkownika określone wyrażenie języka Visual Basic. <xref:System.Activities.Statements.Parallel> Działania daje w wyniku tej właściwości po zakończeniu każdej gałęzi. Jeśli daje w wyniku **True**, a następnie <xref:System.Activities.Statements.Parallel> działanie zakończy się bez wykonania innych działów. Jeśli <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> nie można rozpoznać **True**, a następnie <xref:System.Activities.Statements.Parallel> ukończeniu działania, gdy wszystkie działania podrzędne zostały ukończone.

### <a name="using-the-parallel-activity-designer"></a>Za pomocą Parallel, Projektant działań

Dostęp do **równoległe** projektanta działań w **przepływ sterowania** kategorii **przybornika**.

**Równoległe** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy wszędzie tam, gdzie Projektanci działań są zazwyczaj umieszczone, na przykład wewnątrz **Sekwencji** projektanta działań. Po upuszczając go do projektanta przepływów pracy, tworzy <xref:System.Activities.Statements.Parallel> działania, które domyślnie zawiera <xref:System.Activities.Activity.DisplayName%2A> z **równoległe**

Aby dodać działanie, aby <xref:System.Activities.Statements.Parallel.Branches%2A> kolekcji aktywności równoległej, przeciągnij niektóre projektanta działań z **przybornika** i upuść je na trójkąt wewnątrz **równoległe** Projektant działań. Trójkąty części bocznej działań zawartych w gałęzi. Można dodawać dodatkowe działania, powtarzając tej procedury. Działania można zmienić kolejności, przez przeciąganie i upuszczanie ich w ramach **równoległe** projektanta działań.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Właściwości działania równoległe w Projektancie przepływu pracy

Poniższa tabela pokazuje właściwości działań równoległych i w tym artykule opisano, jak są używane w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę wyświetlaną projektanta działań w nagłówku. Wartość domyślna to **równoległe**. Wartość może być opcjonalnie edytować w **właściwości** siatki lub bezpośrednio w nagłówku projektanta działań.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Prawda|Zawiera kolekcję działania podrzędne do wykonania.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Oceniane, po zakończeniu gałęzi. Jeśli daje w wyniku **True**, następnie zaplanowane oczekujące gałęzie zostały anulowane. Jeśli ta właściwość nie jest ustawiona lub daje w wyniku **False**, działanie zakończy się po zakończeniu wszystkich swoich działań podrzędnych. Wartość domyślna to **null**.|

## <a name="see-also"></a>Zobacz także

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)