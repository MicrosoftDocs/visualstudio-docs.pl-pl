---
title: Projektant przepływu pracy — Interop, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66734cd555c88d960431373d4ccf6a7ca0b39099
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867293"
---
# <a name="interop-activity-designer"></a>Interop, projektant działań

**Międzyoperacyjności** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Interop> działania.

## <a name="the-interop-activity"></a>Działań Interop

<xref:System.Activities.Statements.Interop> Działanie zarządza wykonaniem typów wyprowadzonych z <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> w przepływie pracy.

### <a name="use-the-interop-activity-designer"></a>Użyj Interop, Projektant działań

**Międzyoperacyjności** projektanta działań można znaleźć w **migracji** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**kartę. Można także wybrać **przybornika** z **widoku** menu lub naciśnij klawisz **Ctrl**+**Alt** + **X**.

[Migracji](../workflow-designer/migration-activity-designers.md) kategorię, która zawiera <xref:System.Activities.Statements.Interop> działanie tylko zostaną wyświetlone w **przybornika** Jeśli projekt jest przeznaczony dla pełnego .NET Framework 4.

Dla projektów C#, można ponownie docelowej projektu, aby użyć pełnego .NET Framework 4, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierając polecenie **właściwości**. Na **aplikacji** zaznacz **.NET Framework 4** opcji **platformę docelową**. Wybierz **tak** aby potwierdzić tę zmianę.

Dla projektów języka Visual Basic można ponownie docelowej projektu, aby użyć pełnego .NET Framework 4, klikając prawym przyciskiem myszy nad projektem w **Eksploratora rozwiązań** i wybierając polecenie **właściwości**. Na **skompilować** kliknij pozycję **zaawansowane opcje kompilacji** przycisku. Wybierz **.Net Framework 4** z **Target framework listy**, a następnie kliknij przycisk **OK**. Wybierz **tak** aby potwierdzić tę zmianę.

**Międzyoperacyjności** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchnię projektanta przepływów pracy wszędzie tam, gdzie działań są zazwyczaj umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Upuszczanie **międzyoperacyjności** tworzy projektanta działań <xref:System.Activities.Statements.Interop> działanie przy użyciu domyślnego **DisplayName** z międzyoperacyjności. Możesz edytować <xref:System.Activities.Activity.DisplayName%2A> w nagłówku **międzyoperacyjności** Projektant działań lub **DisplayName** pola siatki właściwości.

Kliknij przycisk **kliknij, aby przeglądać** tekstu w **ActivityType** pole, albo na **międzyoperacyjności** działanie projektanta lub w siatce właściwości, aby otworzyć **Przeglądaj i Wybierz pozycję .net typu** okno dialogowe. Wyświetlane są tylko typy workflow 3.0 lub 3.5 w przepływie pracy działania. Oznacza to, że tylko typy pochodne <xref:System.Workflow.ComponentModel.Activity> są wyświetlane. Aby uzyskać więcej informacji na temat używania tego pola, aby określić typ zobacz [umożliwia przeglądanie i wybieranie typu .NET, okno dialogowe](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>Właściwości międzyoperacyjności

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Interop> właściwości, a w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchni projektanta przepływów pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.Interop> działania. Wartość domyślna to **międzyoperacyjności**. Chociaż nazwa wyświetlana nie jest wymagane, zaleca się podać jedną.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Prawda|Określa typ działania zawarte w <xref:System.Activities.Statements.Interop> działania. Ten typ określony muszą pochodzić od <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Zobacz także

- [Migracja](../workflow-designer/migration-activity-designers.md)