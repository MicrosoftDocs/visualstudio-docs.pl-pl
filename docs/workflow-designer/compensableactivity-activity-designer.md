---
title: Projektant przepływu pracy — CompensableActivity, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f08d967269df6046c53b9c6bdd8d369c56cc23e4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54977216"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity, projektant działań

**CompensableActivity** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.CompensableActivity> działania.

## <a name="the-compensableactivity-activity"></a>Działanie CompensableActivity
 <xref:System.Activities.Statements.CompensableActivity> Definiuje jednostkę pracy, która potwierdzenia lub płatne po pomyślnym ukończeniu.

### <a name="using-the-compensableactivity-activity-designer"></a>Za pomocą CompensableActivity, Projektant działań
 **CompensableActivity** projektanta działań można znaleźć w **transakcji** kategorii **przybornika**. Aby otworzyć **przybornika**, wybierz opcję **przybornika** karty w lewej części projektanta przepływów pracy. Można także wybrać **przybornika** z **widoku** menu lub naciśnij klawisz **Ctrl**+**Alt** + **X**.

 **CompensableActivity** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy. Można usunąć, Projektant działań wewnątrz <xref:System.Activities.Statements.Sequence>. Projektant działań porzucenie tworzy <xref:System.Activities.Statements.CompensableActivity> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> z CompensableActivity. Edytuj <xref:System.Activities.Activity.DisplayName%2A> wartością w nagłówku **CompensableActivity** projektanta działań. Ponadto można je edytować w **DisplayName** pola siatki właściwości.

### <a name="the-compensableactivity-properties"></a>Właściwości CompensableActivity
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.CompensableActivity> właściwości i w tym artykule opisano, jak są używane w projektancie. <xref:System.Activities.Activity.DisplayName%2A> i <xref:System.Activities.Activity%601.Result%2A> właściwości można edytować w siatce właściwości, ale inne właściwości, należy edytować na powierzchni projektanta przepływów pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalna nazwa przyjazna <xref:System.Activities.Statements.CompensableActivity> działania. Wartość domyślna to CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Określa wartość zwracaną przez <xref:System.Activities.Statements.CompensableActivity>. Można edytować tej właściwości, w siatce właściwości.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Prawda|Określa działania, dla których dostępny jest logiki wynagrodzenie, anulowanie i potwierdzenia. Aby dodać <xref:System.Activities.Statements.CompensableActivity.Body%2A> działania, listy działanie z **przybornika** do **treści** polu na **CompensableActivity** Projektant działań. Dodaj tekst wskazówki "W tym miejscu listy activity".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Określa działania, który jest wykonywany po anulowania. Aby dodać działanie, Porzuć swojego projektanta z **przybornika** do **CancellationHandler** polu na **CompensableActivity** projektanta działań. Dodaj tekst wskazówki "Upuść działanie tutaj".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Określa działania, które zostaną wykonane podczas kompensowania <xref:System.Activities.Statements.CompensableActivity.Body%2A> działania. Ten program obsługi może być jawnie wywołana, za pomocą <xref:System.Activities.Statements.Compensate> działania.<br /><br /> Aby dodać działanie, Porzuć swojego projektanta działań z **przybornika** do **CompensationHandler** polu na **CompensableActivity** projektanta działań. Dodaj tekst wskazówki "Upuść działanie tutaj".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Określa działanie do wykonania podczas potwierdzania <xref:System.Activities.Statements.CompensableActivity.Body%2A> działania. Ten program obsługi może być jawnie wywołana, za pomocą <xref:System.Activities.Statements.Confirm> działania.<br /><br /> Aby dodać działanie, Porzuć swojego projektanta działań z **przybornika** do **ConfirmationHandler** polu na **CompensableActivity** projektanta działań. Dodaj tekst wskazówki "Upuść działanie tutaj".|

## <a name="see-also"></a>Zobacz także

- [Transakcja](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)