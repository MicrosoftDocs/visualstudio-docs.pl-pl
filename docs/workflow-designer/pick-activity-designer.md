---
title: Projektant przepływu pracy — Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 983a3ee3539617bf7ee5864c2138b2f0369e228f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650078"
---
# <a name="pick-activity-designer"></a>Pick, projektant działań

Działanie <xref:System.Activities.Statements.Pick> zapewnia przepływ sterowania oparty na zdarzeniach. Działanie wykonuje jedną z kilku gałęzi w odpowiedzi na zdarzenie wyzwalające.

## <a name="the-pick-activity"></a>Działanie pobrania

Działanie <xref:System.Activities.Statements.Pick> zawiera kolekcję obiektów <xref:System.Activities.Statements.PickBranch>, z których jednym działaniem <xref:System.Activities.Statements.Pick> można wykonać z powodu zdarzenia przychodzącego, które służy jako wyzwalacz. W ten sposób Projektant przepływu pracy zapewnia modelowanie przepływu sterowania opartego na zdarzeniach. Każda <xref:System.Activities.Statements.PickBranch> zawiera <xref:System.Activities.Statements.PickBranch.Trigger%2A> i <xref:System.Activities.Statements.PickBranch.Action%2A>. Na początku wykonywania działania <xref:System.Activities.Statements.Pick> zostanie zaplanowana cała aktywność wyzwalacza elementów <xref:System.Activities.Statements.PickBranch>. Po zakończeniu pierwszego działania zostanie zaplanowana odpowiednia aktywność działania, a wszystkie inne działania wyzwalacza są anulowane.

### <a name="how-to-use-the-pick-activity-designer"></a>Jak używać projektanta działań wyboru

Dostęp do projektanta działań **Wybierz** w kategorii **przepływ sterowania** w **przyborniku**. Projektanta działań **wyboru** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, gdy projektanci aktywności są zwykle umieszczane na przykład w ramach projektanta działań **sekwencji** . Po porzucenie go do Projektant przepływu pracy tworzy działanie <xref:System.Activities.Statements.Pick>, które domyślnie zawiera dwa puste działania <xref:System.Activities.Statements.PickBranch> jako elementy z nazwami wyświetlanymi Branch1 i Branch2. Te odpowiednie wartości właściwości <xref:System.Activities.Statements.PickBranch.DisplayName%2A> można edytować w nagłówku projektanta działań **PickBranch** lub w oknie **Właściwości** dla każdej gałęzi.

Istnieją dwa sposoby dodawania działań <xref:System.Activities.Statements.PickBranch> do kolekcji <xref:System.Activities.Statements.Pick> obiektu: przeciąganie i upuszczanie projektanta **PickBranch** z **przybornika** lub za pomocą menu dostępnego po kliknięciu prawym przyciskiem myszy z poziomu powierzchni projektowej **wyboru** . Aby uzyskać szczegółowe informacje, zobacz temat [PickBranch](../workflow-designer/pickbranch-activity-designer.md) . Należy zauważyć, że jedynym elementem, który można umieścić wewnątrz projektanta działań **wyboru** , jest **PickBranch** .

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Wybierz właściwości działania w Projektant przepływu pracy

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.Pick> i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchni projektanta.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.Pick> projektanta działań w nagłówku. Wartość domyślna to wybierz. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku projektanta działań.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|

## <a name="see-also"></a>Zobacz także

- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
- [Wybieranie działania](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Używanie działania Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)