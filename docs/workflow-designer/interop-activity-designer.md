---
title: Projektant przepływu pracy — Projektant działań międzyoperacyjnych
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8047df3787c0871e369b6079e4f0cc80f6d93949
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650211"
---
# <a name="interop-activity-designer"></a>Interop, projektant działań

Projektant działań **międzyoperacyjnych** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.Interop>.

## <a name="the-interop-activity"></a>Działanie międzyoperacyjności

Działanie <xref:System.Activities.Statements.Interop> zarządza wykonywaniem typów, które pochodzą od <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> w ramach przepływu pracy.

### <a name="use-the-interop-activity-designer"></a>Korzystanie z projektanta działań międzyoperacyjnych

Projektanta działań **międzyoperacyjnych** można znaleźć w kategorii **migracji** **przybornika**, do którego jest uzyskiwany dostęp przez kliknięcie karty **przybornika** . Możesz też wybrać **Przybornik** z menu **Widok** lub klawisz **Ctrl.** +**Alt** +**X**.

Kategoria [migracji](../workflow-designer/migration-activity-designers.md) zawierająca działanie <xref:System.Activities.Statements.Interop> pojawia się tylko w **przyborniku** , jeśli projekt jest przeznaczony .NET Framework 4 (pełny) lub nowszy. W razie potrzeby można zmienić wersję platformy, która jest przeznaczona dla projektu.

Projektanta działań **międzyoperacyjnych** można przeciągnąć z **przybornika** i upuścić na Projektant przepływu pracy powierzchni, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence>. Porzucenie projektanta działań **międzyoperacyjnych** powoduje utworzenie działania <xref:System.Activities.Statements.Interop> z domyślną wartością **DisplayName** międzyoperacyjności. @No__t_0 można edytować w nagłówku projektanta działań **międzyoperacyjnych** lub w polu **DisplayName** siatki właściwości.

Kliknij **przycisk kliknij, aby przeglądać** tekst w **polu ActivityType** , w projektancie działań **międzyoperacyjnych** lub w siatce właściwości, aby otworzyć okno dialogowe **Przeglądaj i wybierz typ platformy .NET** . Wyświetlane są tylko typy dla działań przepływu pracy 3,0 lub przepływu pracy 3,5. Oznacza to, że wyświetlane są tylko typy pochodzące z <xref:System.Workflow.ComponentModel.Activity>. Aby uzyskać więcej informacji na temat używania tego pola do określania typu, zobacz [przeglądanie i wybieranie typu .NET okno dialogowe](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>Właściwości międzyoperacyjności

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.Interop> i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości lub na Projektant przepływu pracy powierzchni.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa działania <xref:System.Activities.Statements.Interop>. Wartość domyślna to **międzyoperacyjność**. Chociaż nazwa wyświetlana nie jest wymagana, zaleca się jej dostarczenie.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Oznacza|Określa typ działania zawartego w działaniu <xref:System.Activities.Statements.Interop>. Określony typ musi pochodzić od <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Zobacz także

- [Migracja](../workflow-designer/migration-activity-designers.md)