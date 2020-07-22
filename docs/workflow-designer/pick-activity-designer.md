---
title: Projektant przepływu pracy — Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01ebd0dbfa8274b370a7e84b1033465e2be0b4a9
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876037"
---
# <a name="pick-activity-designer"></a>Pick, projektant działań

<xref:System.Activities.Statements.Pick>Działanie zapewnia przepływ sterowania oparty na zdarzeniach. Działanie wykonuje jedną z kilku gałęzi w odpowiedzi na zdarzenie wyzwalające.

## <a name="the-pick-activity"></a>Działanie pobrania

<xref:System.Activities.Statements.Pick>Działanie zawiera kolekcję <xref:System.Activities.Statements.PickBranch> obiektów, z których jedno <xref:System.Activities.Statements.Pick> działanie może zostać wykonane z powodu zdarzenia przychodzącego, które służy jako wyzwalacz. W ten sposób Projektant przepływu pracy zapewnia modelowanie przepływu sterowania opartego na zdarzeniach. Każdy <xref:System.Activities.Statements.PickBranch> z nich zawiera <xref:System.Activities.Statements.PickBranch.Trigger%2A> a i <xref:System.Activities.Statements.PickBranch.Action%2A> . Na początku <xref:System.Activities.Statements.Pick> wykonywania działania są planowane wszystkie działania wyzwalacza <xref:System.Activities.Statements.PickBranch> elementów. Po zakończeniu pierwszego działania zostanie zaplanowana odpowiednia aktywność działania, a wszystkie inne działania wyzwalacza są anulowane.

### <a name="how-to-use-the-pick-activity-designer"></a>Jak używać projektanta działań wyboru

Dostęp do projektanta działań **Wybierz** w kategorii **przepływ sterowania** w **przyborniku**. Projektanta działań **wyboru** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, gdy projektanci aktywności są zwykle umieszczane na przykład w ramach projektanta działań **sekwencji** . Po porzucenie go do Projektant przepływu pracy tworzy <xref:System.Activities.Statements.Pick> działanie, które domyślnie zawiera dwa puste <xref:System.Activities.Statements.PickBranch> działania jako elementy z nazwami wyświetlanymi Branch1 i Branch2. Te odpowiednie <xref:System.Activities.Statements.PickBranch.DisplayName%2A> wartości właściwości można edytować w nagłówku projektanta działań **PickBranch** lub w oknie **Właściwości** dla każdej gałęzi.

Istnieją dwa sposoby dodawania <xref:System.Activities.Statements.PickBranch> działań do kolekcji <xref:System.Activities.Statements.Pick> obiektów: przeciąganie i upuszczanie projektanta **PickBranch** z **przybornika** lub za pomocą menu dostępnego po kliknięciu prawym przyciskiem myszy z poziomu powierzchni projektowej **pobierania** . Aby uzyskać szczegółowe informacje, zobacz temat [PickBranch](../workflow-designer/pickbranch-activity-designer.md) . Należy zauważyć, że jedynym elementem, który można umieścić wewnątrz projektanta działań **wyboru** , jest **PickBranch** .

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Wybierz właściwości działania w Projektant przepływu pracy

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Pick> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchni projektanta.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa przyjazną nazwę <xref:System.Activities.Statements.Pick> projektanta działań w nagłówku. Wartość domyślna to wybierz. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku projektanta działań.<br /><br /> Chociaż <xref:System.Activities.Activity.DisplayName%2A> nie jest to ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|

## <a name="see-also"></a>Zobacz także

- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
- [Wybieranie działania](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Używanie działania Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)