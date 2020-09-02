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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72650211"
---
# <a name="interop-activity-designer"></a>Interop, projektant działań

Projektant działań **międzyoperacyjnych** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Interop> działania.

## <a name="the-interop-activity"></a>Działanie międzyoperacyjności

<xref:System.Activities.Statements.Interop>Działanie zarządza wykonywaniem typów, które pochodzą z <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> przepływu pracy.

### <a name="use-the-interop-activity-designer"></a>Korzystanie z projektanta działań międzyoperacyjnych

Projektanta działań **międzyoperacyjnych** można znaleźć w kategorii **migracja** **przybornika**, do którego jest uzyskiwany dostęp, klikając kartę **Przybornik** . Alternatywnie możesz wybrać **Przybornik** z menu **Widok** lub nacisnąć **klawisze CTRL** + **Alt** + **X**.

Kategoria [migracji](../workflow-designer/migration-activity-designers.md) , która zawiera <xref:System.Activities.Statements.Interop> działanie, pojawia się tylko w **przyborniku** , jeśli projekt jest przeznaczony .NET Framework 4 (pełny) lub nowszy. W razie potrzeby można zmienić wersję platformy, która jest przeznaczona dla projektu.

Projektanta działań **międzyoperacyjnych** można przeciągnąć z **przybornika** i upuścić na Projektant przepływu pracy powierzchnię wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Porzucenie projektanta działań **międzyoperacyjnych** powoduje utworzenie <xref:System.Activities.Statements.Interop> działania z domyślną wartością **DisplayName** międzyoperacyjności. Można edytować <xref:System.Activities.Activity.DisplayName%2A> w nagłówku projektanta działań **międzyoperacyjnych** lub w polu **DisplayName** siatki właściwości.

Kliknij **przycisk kliknij, aby przeglądać** tekst w **polu ActivityType** , w projektancie działań **międzyoperacyjnych**  lub w siatce właściwości, aby otworzyć okno dialogowe **Przeglądaj i wybierz typ platformy .NET** . Wyświetlane są tylko typy dla działań przepływu pracy 3,0 lub przepływu pracy 3,5. Oznacza to, że wyświetlane są tylko typy pochodne od <xref:System.Workflow.ComponentModel.Activity> . Aby uzyskać więcej informacji na temat używania tego pola do określania typu, zobacz [przeglądanie i wybieranie typu .NET okno dialogowe](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>Właściwości międzyoperacyjności

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Interop> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości lub na Projektant przepływu pracy powierzchni.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa <xref:System.Activities.Statements.Interop> działania. Wartość domyślna to **międzyoperacyjność**. Chociaż nazwa wyświetlana nie jest wymagana, zaleca się jej dostarczenie.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Prawda|Określa typ działania zawartego w <xref:System.Activities.Statements.Interop> działaniu. Określony typ musi pochodzić od <xref:System.Workflow.ComponentModel.Activity> .|

## <a name="see-also"></a>Zobacz też

- [Migracja](../workflow-designer/migration-activity-designers.md)