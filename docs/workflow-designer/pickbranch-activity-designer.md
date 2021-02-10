---
title: Projektant przepływu pracy — Projektant działań PickBranch
description: Dowiedz się, jak Projektant działań PickBranch udostępnia ścieżkę wykonywania w ramach działania pobrania, które może zostać wyzwolone przez zdarzenie przychodzące.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9d3ac314d5f8eb7980bdf5102d871546d3167141
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968674"
---
# <a name="pickbranch-activity-designer"></a>PickBranch, projektant działań

<xref:System.Activities.Statements.PickBranch>Zapewnia ścieżkę wykonywania w ramach <xref:System.Activities.Statements.Pick> działania, które może zostać wyzwolone przez zdarzenie przychodzące.

## <a name="pickbranch"></a>PickBranch

<xref:System.Activities.Statements.PickBranch> obiekty są zawarte w <xref:System.Activities.Statements.Pick.Branches%2A> kolekcji <xref:System.Activities.Statements.Pick> działań. Każda z nich <xref:System.Activities.Statements.PickBranch> jest zawarta w gałęzi <xref:System.Activities.Statements.Pick> działania i może być wykonana z powodu zdarzenia przychodzącego, które służy jako wyzwalacz. W ten sposób Projektant przepływu pracy zapewnia modelowanie przepływu sterowania opartego na zdarzeniach. Każdy <xref:System.Activities.Statements.PickBranch> z nich zawiera <xref:System.Activities.Statements.PickBranch.Trigger%2A> a i <xref:System.Activities.Statements.PickBranch.Action%2A> .

### <a name="how-to-use-the-pick-activity-designer"></a>Jak używać projektanta działań wyboru

Dostęp do projektanta **PickBranch** w kategorii **przepływ sterowania** w **przyborniku**.

Dwa puste <xref:System.Activities.Statements.PickBranch> obiekty z nazwami wyświetlanymi **Branch1** i **Branch2** są tworzone domyślnie jako elementy <xref:System.Activities.Statements.Pick> działania po początkowym **pobraniu** projektanta działań na Projektant przepływu pracy. Te odpowiednie <xref:System.Activities.Statements.PickBranch.DisplayName%2A> wartości właściwości można edytować w nagłówku projektanta **PickBranch** lub w oknie **Właściwości** dla każdej gałęzi.

Istnieją dwa sposoby dodawania <xref:System.Activities.Statements.PickBranch> obiektów do kolekcji <xref:System.Activities.Statements.Pick> obiektów: przeciąganie i upuszczanie projektanta **PickBranch** z **przybornika** lub za pomocą menu dostępnego po kliknięciu prawym przyciskiem myszy z poziomu powierzchni projektowej **wyboru** :

- Projektant **PickBranch** tworzy, <xref:System.Activities.Statements.PickBranch> gdy jest przeciągany z **przybornika** i upuszczany na jedną z gałęzi projektanta działań **wyboru** na Projektant przepływu pracy powierzchni. Nowe <xref:System.Activities.Statements.PickBranch> obiekty można umieścić wewnątrz <xref:System.Activities.Statements.Pick> projektanta po lewej lub prawej stronie wszelkich istniejących elementów znajdujących się <xref:System.Activities.Statements.PickBranch> już w kolekcji. Gdy przeciągasz projektanta **PickBranch** do projektanta **wyboru** z myszą, Projektant **wyboru** używa pionowego szarego pasma, aby wskazać, gdzie <xref:System.Activities.Statements.PickBranch> zostanie dodany dla danego położenia myszy.

- Kliknij prawym przyciskiem myszy pozycję **Wybierz** projektanta działań (ale nie w programie **PickBranch** Designer), aby uzyskać menu kontekstowe i wybrać polecenie **Utwórz gałąź** , aby dodać nowy element <xref:System.Activities.Statements.PickBranch> . Zwróć uwagę, że nowy <xref:System.Activities.Statements.PickBranch> zostanie dodany po prawej stronie istniejących <xref:System.Activities.Statements.PickBranch> obiektów w projektancie **wyboru** .

Projektanta **PickBranch** można rozszerzyć, aby odsłonić pola **wyzwalacza** i **akcji** lub zwinięte przez kliknięcie podwójnego karetki po prawej stronie jego nagłówków. Edytuj <xref:System.Activities.Statements.PickBranch.Trigger%2A> i <xref:System.Activities.Statements.PickBranch.Action%2A> każdego z nich, <xref:System.Activities.Statements.PickBranch> usuwając działania do pól **wyzwalacz** i **Akcja** w swoich projektantach.

<xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.Pick.Branches%2A> <xref:System.Activities.Statements.Pick> Można zmienić kolejność obiektów w kolekcji obiektów, przeciągając je i upuszczając do nowej lokalizacji w projektancie **wyboru** . Projektant **wyboru** używa pionowego niebieskiego pasma, aby wskazać, gdzie <xref:System.Activities.Statements.PickBranch> zostanie dodany dla danego położenia myszy.

Istnieją dwa sposoby usunięcia <xref:System.Activities.Statements.PickBranch> :

- Wybierz projektanta **PickBranch** i usuń go.
- Wybierz projektanta **PickBranch** , kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowe, a następnie wybierz pozycję **Usuń**.

Pamiętaj, aby wybrać projektanta **PickBranch** , wybierając jedno z działań wewnątrz jego **wyzwalacza** lub **akcji** przez pomyłkę usuwa jedną z tych działań, a nie <xref:System.Activities.Statements.PickBranch> obiekt.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Właściwości PickBranch w Projektant przepływu pracy

W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.PickBranch> właściwości i opisano sposób ich używania w Projektant przepływu pracy.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|Fałsz|Przyjazna nazwa wyświetlana w nagłówku projektanta **PickBranch** . Wartość domyślna to gałąź.<br /><br /> Chociaż <xref:System.Activities.Activity.DisplayName%2A> nie jest to ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Prawda|Każda <xref:System.Activities.Statements.PickBranch> z nich zawiera <xref:System.Activities.Statements.PickBranch.Trigger%2A> akcję, która może wywołać <xref:System.Activities.Statements.PickBranch.Action%2A> .|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|Fałsz|Każdy <xref:System.Activities.Statements.PickBranch> z nich zawiera element <xref:System.Activities.Statements.PickBranch.Action%2A> , który jest wykonywany, gdy zostanie wyzwolony.|

## <a name="see-also"></a>Zobacz też

- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
- [Wybieranie działania](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Używanie działania Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)