---
title: Projektant przepływu pracy — Pick, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3afd20b75bdb2c00317f9acf6ec6adcd12f6f949
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069787"
---
# <a name="pick-activity-designer"></a>Pick, projektant działań

<xref:System.Activities.Statements.Pick> Aktywności zawiera przepływ sterowania opartego na zdarzeniach. Działanie wykonuje jedną kilka gałęzi w odpowiedzi na wyzwalającą zdarzenie.

## <a name="the-pick-activity"></a>Działania Pick

A <xref:System.Activities.Statements.Pick> aktywności zawiera zbiór <xref:System.Activities.Statements.PickBranch> obiektów, z których jedna <xref:System.Activities.Statements.Pick> działania można wykonywać z powodu niektóre zdarzenia przychodzące, która służy jako wyzwalacz. W ten sposób Workflow Designer udostępnia modelowanie przepływu sterowania opartego na zdarzeniach. Każdy <xref:System.Activities.Statements.PickBranch> zawiera <xref:System.Activities.Statements.PickBranch.Trigger%2A> i <xref:System.Activities.Statements.PickBranch.Action%2A>. Na początku <xref:System.Activities.Statements.Pick> wykonanie tego działania, wszystkie działania wyzwalacza z <xref:System.Activities.Statements.PickBranch> elementy są zaplanowane. Po zakończeniu pierwszego działania zaplanowano odpowiadającego im działania akcji, a inne działania wyzwalacza zostały anulowane.

### <a name="how-to-use-the-pick-activity-designer"></a>Jak używać Projektanta wybierz działanie

Dostęp do **wybierz** projektanta działań w **przepływ sterowania** kategorii **przybornika**. **Wybierz** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy wszędzie tam, gdzie Projektanci działań są zazwyczaj umieszczone, na przykład wewnątrz  **Sekwencja** projektanta działań. Po upuszczając go do projektanta przepływów pracy, tworzy <xref:System.Activities.Statements.Pick> działania, które domyślnie zawiera dwa puste <xref:System.Activities.Statements.PickBranch> działań jako elementy za pomocą wyświetlania nazw Branch1 i Branch2. Te odpowiednich <xref:System.Activities.Statements.PickBranch.DisplayName%2A> wartości właściwości mogą być edytowane w **PickBranch** nagłówka projektanta działań lub w ramach **właściwości** okna dla każdej gałęzi.

Istnieją dwa sposoby dodawania <xref:System.Activities.Statements.PickBranch> działań do kolekcji <xref:System.Activities.Statements.Pick> obiektu: przeciąganie i upuszczanie **PickBranch** projektanta z **przybornika** lub za pomocą menu kliknij prawym przyciskiem myszy z poziomu **wybierz** powierzchni projektowej. Aby uzyskać więcej informacji, zobacz [PickBranch](../workflow-designer/pickbranch-activity-designer.md) tematu. Zwróć uwagę, że tylko element, którego można umieścić wewnątrz **wybierz** jest Projektant działań **PickBranch** projektanta działań.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Wybierz właściwości działania w Projektancie przepływu pracy

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Pick> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchni projektowej.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.Pick> projektanta działań w nagłówku. Wartość domyślna to pobranie. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku projektanta działań.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest bezwzględnie konieczne jest najlepszym rozwiązaniem, aby użyć jednego.|

## <a name="see-also"></a>Zobacz także

- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
- [Wybieranie działania](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Używanie działania Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)